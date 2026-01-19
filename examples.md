

## Exemple - Définition explicite de l’artefact

```yaml
- task: PublishPipelineArtifact@1
  inputs:
    targetPath: front/dist/namedproject/browser
    artifact: front-build # À partir de ce point, le pipeline opère sur un objet, et non sur des hypothèses liées à l’état du workspace.

- task: DownloadPipelineArtifact@2
  inputs:
    artifact: front-build
    path: $(Pipeline.Workspace)/front-build
```

--- 

## Exemple — La version est une propriété vérifiée et bloquante de l’artefact

```bash
VERSION_FILE="$BUILD_ARTIFACTSTAGINGDIRECTORY/version.txt" 
# la validité d’une version vérifié explicitement, l’artefact porte une identité versionnée et pipeline bloque l’exécution en cas d’anomalie.

if [ ! -f "$VERSION_FILE" ]; then
  echo "❌ Version not defined for artefact"
  exit 1
fi

VERSION=$(cat "$VERSION_FILE")

if [ -z "$VERSION" ]; then
  echo "❌ Empty artefact version"
  exit 1
fi

echo "✅ Artefact version detected: $VERSION"
```


## Contre-Exemple — cas commun (E002, E003)
Illustrant l’absence de garanties sur l’immutabilité et l’identité de l’artefact.


```yaml
- script: |
    cd src
    dotnet build Application.csproj --configuration Release --no-restore
    dotnet publish Application.csproj --configuration Release \
      --output "$(Build.ArtifactStagingDirectory)/publish_output"

    cd "$(Build.ArtifactStagingDirectory)"
    zip -r application.zip publish_output/*
  displayName: 'Build and package application artefact'

# La rupture d’immuabilité est possible sans changement de version détectable.
# Le pipeline constate l’existence du fichier, mais ne lui donne aucune identité versionnée
- script: |
    az webapp deploy \
      --resource-group "${RESOURCE_GROUP}" \
      --name "${APP_SERVICE_NAME}" \
      --src-path "$(Build.ArtifactStagingDirectory)/application.zip" \
      --type zip
  displayName: 'Deploy application artefact'
```
