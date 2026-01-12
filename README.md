# Artefacts

> **Principe d’architecture CI/CD —  
> Les garanties de sécurité d’un pipeline doivent être explicites.**

---

## [E001 — Artefact de build immuable par conception](./001.md)
Un artefact de build n’est jamais modifié ; toute modification implique la production d’un nouvel artefact, c’est-à-dire d’une nouvelle version.

## [E002 — Frontière explicite de clôture de l’artefact (build / runtime)](./002.md)
Le pipeline doit rendre explicite la frontière à partir de laquelle l’artefact est défini comme immuable et toute modification par le runtime est interdite.

## [E003 — Source de version unique et non ambiguë](./003.md)
La version déployée doit provenir d’une source unique, explicite et traçable.  
Toute divergence déclenche une erreur explicite.

## [E004 — Stabilité des identifiants de ressources](./004.md)
Les identifiants de ressources utilisés par des tiers (ex. : captcha) doivent rester inchangés entre les publications CI/CD.

## [E005 — Règles de sécurité appliquées par des contrôles bloquants](./005.md)
Les règles de sécurité sont appliquées par des vérifications automatiques et des erreurs bloquantes.  
Toute violation produit un signal exploitable, explicitement rattaché à son périmètre (build, déploiement ou exécution).

---

## Quand et pourquoi ce travail est utile pour le projet ? 

Les points ci-dessus permettent de vérifier
quelles garanties sont réellement assurées par le pipeline,
et de les distinguer des hypothèses de sécurité.

Sans cette distinction, il est impossible de déterminer
si un incident relève du code, du pipeline ou du runtime.

Ces artefacts rendent ces garanties explicites.
