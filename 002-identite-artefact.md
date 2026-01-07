

# Le pipeline publie tout le staging directory comme un seul blob sans frontière sémantique.En consequence L’artefact n’a pas d’identité.

    Un artefact qui n’a pas de frontière logique ne peut pas être contrôlé, seulement transporté.

## 2. Pourquoi c’est un problème structurel (tes points sont bons)

« Parce qu’en cas de problème, on est obligé de tout redéployer, tout tester et tout analyser, même si une seule partie est en cause — ce qui augmente le temps d’incident et le risque de nouvelles erreurs. »
Le problème est en amont des tests : sans identité ni périmètre clair de l’artefact, on ne sait même pas quoi tester.

    Sans identité explicite, l’artefact ne peut ni être contrôlé, ni promu, ni audité de manière fiable.

    No artifact contract → correct
    No blast-radius control → très juste
    No promotion model → excellent point (souvent oublié)
    Audit & compliance nightmare → exact
