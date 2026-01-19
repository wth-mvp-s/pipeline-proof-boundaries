

# Artefacts
Les points ci-dessus permettent de vérifier
quelles garanties sont réellement assurées par le pipeline,
et de les distinguer des hypothèses de sécurité.

Sans cette distinction, il est impossible de déterminer
si un incident relève du code, du pipeline ou du runtime.

Ces artefacts rendent ces garanties explicites.

--- 
> **Principe d’architecture CI/CD —  
> Les garanties de sécurité d’un pipeline doivent être explicites.**
---


## [E001 — Définir l’artefact](./001.md)
Définir l’artefact, c’est définir le périmètre de responsabilité du pipeline.

## [E002 — Artefact est immuable](./002.md)
Cette garantie corresponde exactement à ce qui est livré.

## [E003 — Source de version unique et non ambiguë](./003.md)
Toute modification traçable dans le pipeline qui rompt l’immuabilité de l’artefact entraîne mécaniquement la production d’une nouvelle version.

## [E004 — Stabilité des identifiants de ressources](./004.md)
Les identifiants de ressources utilisés par des tiers (ex. : captcha) doivent rester inchangés entre les publications CI/CD.

## [E005 — Règles de sécurité appliquées par des contrôles bloquants](./005.md)
Les règles de sécurité sont appliquées par des vérifications automatiques et des erreurs bloquantes.  
Toute violation produit un signal exploitable, explicitement rattaché à son périmètre (build, déploiement ou exécution).

