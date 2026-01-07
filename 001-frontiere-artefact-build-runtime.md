



# 001.Démasquer les abstractions d’exécution cloud
To jest warunek poprawności architektury pipeline.

## Ce design est valide pour faire fonctionner le système, mais incompatible avec l’objectif de preuve et de prévention de régression.




### 
problem (abstrakcyjny)

Le pipeline masque une complexité réelle (build, assemblage, contenu final) derrière des mécanismes de haut niveau qui donnent l’illusion que tout est contrôlé, alors qu’aucune preuve formelle n’existe.

Le pipeline peut déployer un artefact partiellement construit sans jamais prouver qu’il est complet.

« Cette abstraction masque le contenu réel de l’artefact »
« Ce mécanisme empêche toute vérification formelle »
« Le système peut dériver sans signal »

 
####
<!--
	Dowód (WHERE):

DotNetCoreCLI@2 publish

potem npm build

potem CopyFiles do katalogu publikacji

brak momentu zamknięcia artefaktu

brak listy plików końcowych

brak checksum / manifestu

-->
