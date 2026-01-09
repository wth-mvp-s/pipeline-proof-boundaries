

# Artefacts


## [E001 — Artefact de build immuable par conception](./001.md)
Un artefact de build n’est jamais modifié ; toute modification implique la production d’un nouvel artefact, c’est-à-dire d’une nouvelle version.

## [E002. Le pipeline doit rendre explicite la frontière à partir de laquelle l’artefact est défini comme immuable et toute modification par le runtime est interdite.](./002.md)

## [E003. La source de version est unique et non ambiguë.Le système garantit la compatibilité des outils afin d’éviter toute hypothèse implicite.Toute divergence de version avec l’étape concernée déclenche une erreur explicite.](./003.md)

## [E004. Stabilité des identifiants de ressources.](./004.md)
Les identifiants de ressources utilisés par les tiers (ex. : captcha) doivent rester inchangés dans toutes les publications CI/CD.

## [E005. Les règles de sécurité sont enforcés par des vérifications automatiques et des erreurs bloquantes.Toute violation produit un signal exploitable, explicitement rattaché à son périmètre (build, déploiement ou exécution).](./005.md)
