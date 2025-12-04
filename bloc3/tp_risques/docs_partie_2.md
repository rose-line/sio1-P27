## Documents relatifs à la partie 2

### Document 7 - Démarche PIA (_Privacy Impact Assemsment_)

Une « analyse d'impact relative à la protection des données » (voir article 35 du RGPD), plus communément appelée _Privacy Impact Assesment_, décrit la manière d'employer la méthode EBIOS (Expression des Besoins et Identification des Objectifs de Sécurité) préconisée par l'ANSSI. Quatre phases permettent de mener un PIA :

1. Délimiter et décrire le **contexte** du traitement considéré
2. Analyser les mesures garantissant le respect des **principes fondamentaux** (pertinence et nécessité du traitement, protection des droits des personnes concernées)
3. Apprécier les **risques** sur la vie privée liés à la sécurité des données
4. Formaliser la **validation** du PIA

---

### Document 8 - Contexte du PIA relatif au traitement d'une étude de marché chez KLIENTE

Le PIA porte sur le processus d'étude de marché mis en oeuvre par KLIENTE. Le DSI est **responsable du traitement des données** manipulées dans le cadre de ce processus. L'objectif des études de marché est de collecter et d'analyser des informations qui identifient les caractéristiques d'un marché. Les données traitées sont ensuite mises à disposition des différents clients.

- **Données traitées** : informations personnelles, réponses au questionnaire, enregistrement audio de l'entretien, analyse des résultats de l'étude de marché
- **Destinataires** : KLIENTE et clients de l'étude de marché
- **Durée de conservation** : 1 an

#### Cycle de vie des données

- Demande d'enregistrement de l'appel : la personne contactée notifie son acceptation ou non de l'enregistrement de l'entretien, et elle est informée des conditions de traitement de ses DCP
- Collecte des réponses au questionnaire : les données sont collectées par l'opérateur par saisie sur son ordinateur de bureau, puis enregistrées sur un serveur de base de données hébergé par KLIENTE
- Vérification de l'enregistrement audio de l'entretien : l'enregistrement audio est vérifié puis sauvegardé sur un serveur de fichiers hébergé par KLIENTE
- Analyse des résultats de l'étude de marché

#### Support des données

- Un téléphone IP est utilisé pour la conversation
- Un ordinateur de bureau est mobilisé lors de l'enregistrement des réponses et de l'entretien
- Plusieurs serveurs de base de données redondants stockent les réponses aux questionnaires, et un serveur de fichiers stocke l'enregistrement audio de l'entretien

---

### Document 9 - Risques identifiés sur les DCP

#### Scénario 1

Usurpation d'un compte d'authentification d'un opérateur par un intervenant extérieur lors d'une opération de maintenance sur un ordinateur, pour récupérer des données confidentielles.

_Les données se trouvent sur le serveur de base de données et non sur le poste de l'opérateur ; la menace reste peu probable. Par contre, les données confidentielles peuvent bénéficier à une entité malveillante avec des conséquences importantes pour KLIENTE._

#### Scénario 2

Suppression ou vol de données dans la base de données par un salarié mécontent, dans l'objectif de nuire à KLIENTE, voire de les communiquer à un concurrent.

_L'action est facile à mener avec des conséquences importantes._

#### Scénario 3

Consultation de données par un employé non-habilité due à une erreur de manipulation.

_La consultation de données sans habilitation est peu probable, parce qu'une politique de sécurité rigoureuse dans ce domaine est mise en place par la DSI. Cependant, dans le cas d'une faiblesse temporaire dans ce domaine, les risques sont limités car le périmètre d'habilitation de chaque utilisateur est restreint._

#### Scénario 4

Altération de données sur le serveur de base de données par un attaquant extérieur à l'organisation afin de déstabiliser les campagnes d'études de marché.

_Les serveurs de base de données sont actuellement peu protégés des menaces qui viendraient de l'extérieur de l'organisation. Une attaque de ce type provoquerait d'importantes conséquences, notamment sur la qualité et la crédibilité des futures synthèses d'études de marché._

#### Scénario 5

Arrêt du serveur de base de données par une attaque extérieure due à une multitude de requêtes.

_Actuellement, le serveur de base de données pourrait être arrêté pour cette raison. Le risque serait alors maximal, car le travail de tous les opérateurs et des_ Call managers _dépend de l'accès aux données hébergées sur le serveur._

---

### Document 10 - Analyse des scénarios de menaces

| Source de menace                                         | Type de menace | Bien support              | Niveau de vraisemblance                                                             | Confidentialité                                                       | Disponibilité | Intégrité |
| -------------------------------------------------------- | -------------- | ------------------------- | ----------------------------------------------------------------------------------- | --------------------------------------------------------------------- | ------------- | --------- |
| Scénario de menace lié au risque 1 : attaquant extérieur | Espionnage     | Ordinateur de l'opérateur | **2** : limité (les données ne sont présentes que sur le serveur de base de données | L'authentification n'est plus assurée aux seules personnes habilitées |               |           |
|                                                          | ...            |                           |                                                                                     |                                                                       |               |           |

Échelle de niveaux de vraisemblance : 1 (faible), 2 (limité), 3 (important), 4 (maximal).

---

### Document 11 - Événements redoutés

| Valeur métier ou scénario | Événement redouté     | Impacts                                                                         | Niveau gravité    |
| ------------------------- | --------------------- | ------------------------------------------------------------------------------- | ----------------- |
| Exemple : scénario 1      | Usurpation d'identité | Les données confidentielles peuvent être exploitées par une entité malveillante | **3** (important) |
| ...                       | ...                   |                                                                                 |                   |

Échelle de niveaux de gravité : 1 (faible), 2 (limité), 3 (important), 4 (maximal).
