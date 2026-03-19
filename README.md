# Banc
Renouvellement des bancs, état du parc, bancs à remplacer sous 2 ans, estimation budgétaire.
# Gestion du mobilier urbain — Données & suivi

Ce dépôt contient des fichiers Excel servant de **modèles de données** (templates) pour gérer :
- l’inventaire du mobilier urbain,
- les signalements,
- les interventions,
- les contacts fournisseurs.

---

## Contenu du dépôt

- `inventaire_mobilier.xlsx` : inventaire du mobilier (bancs, poubelles, lampadaires, etc.)
- `signalements.xlsx` : signalements (source, urgence, statut)
- `interventions.xlsx` : interventions réalisées (type, technicien, durée, coûts)
- `fournisseurs_contacts.xlsx` : annuaire fournisseurs + type de matériel + remarques

> Ces fichiers peuvent être utilisés tels quels comme “seed data” ou comme modèles pour ajouter des entrées.

---

## Conventions de saisie (important)

- **Identifiants (`id`)** : doivent être **uniques** (ex: `B-001`).
- **Dates** : idéalement au format `YYYY-MM-DD` (les formats Excel restent acceptés).
- **Coordonnées** : `latitude` et `longitude` sont **optionnelles**.
- **Statuts** (recommandé) :
  - `statut` (signalements) : `en attente` / `fait`
  - `etat` (inventaire) : `bon` / `usé` / `à remplacer`

---

## Dictionnaire des colonnes

### `inventaire_mobilier.xlsx` (sheet: `Inventaire`)

| Colonne | Description |
|---|---|
| `id` | Identifiant unique (ex: B-001, 1002, B_3) |
| `type` | Type d’objet (banc, lampadaire, etc.) |
| `materiau` | Matériau (bois, métal, …) |
| `lieu` | Localisation textuelle |
| `latitude` / `longitude` | Coordonnées GPS (optionnel) |
| `date_installation` | Date d’installation |
| `etat` | État (ex: bon, usé, à remplacer) |
| `remarques` | Notes libres |

---

### `signalements.xlsx` (sheet: `Signalements`)

| Colonne | Description |
|---|---|
| `date` | Date du signalement |
| `signale_par` | Source (citoyen, patrouille, concierge, etc.) |
| `objet` | Objet concerné (ex: lampadaire…, banc…) |
| `description` | Description du problème |
| `urgence` | Niveau d’urgence (optionnel si non renseigné) |
| `statut` | Statut (ex: en attente, fait) |

---

### `interventions.xlsx` (sheet: `Interventions`)

| Colonne | Description |
|---|---|
| `date` | Date de l’intervention |
| `objet` | Objet concerné |
| `type_intervention` | Type (peinture, réparation, nettoyage, etc.) |
| `technicien` | Responsable / équipe |
| `duree` | Durée (ex: 1h, 1h30, 2h) |
| `cout_materiel` | Coût du matériel |
| `remarques` | Notes |

---

### `fournisseurs_contacts.xlsx` (sheet: `Fournisseurs`)

| Colonne | Description |
|---|---|
| `entreprise` | Nom fournisseur |
| `contact` | Personne de contact |
| `telephone` | Téléphone |
| `email` | Email (peut être vide) |
| `type_materiel` | Matériel fourni (bancs, poubelles, LED, bornes EV…) |
| `remarques` | Notes (ex: fermé, délais, contrat maintenance…) |

---

## Exemple d’usage

Ces fichiers peuvent être importés dans un script (Python/JS) ou une base de données pour :
- transformer des `signalements` en `interventions`,
- relier un `type` d’objet (inventaire) à un `fournisseur`,
- suivre l’historique d’entretien par objet (`objet`).

---

## Structure du dépôt (exemple)

.
├── inventaire_mobilier.xlsx
├── signalements.xlsx
├── interventions.xlsx
├── fournisseurs_contacts.xlsx
└── README.md
