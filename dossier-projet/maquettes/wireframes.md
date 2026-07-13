# Wireframes — Crew

> Wireframes basse fidélité (ASCII) des écrans clés, reconstitués à partir
> des pages réelles (`front/src/pages/`) et des textes d'interface définis
> dans `front/src/locales/fr.json`.

---

## 1. Connexion (`Login.jsx`)

```
┌──────────────────────────────────────────┐
│                  Crew 🍽️                   │
│                                            │
│              Connexion                    │
│                                            │
│  Email        [_____________________]     │
│  Mot de passe [_____________________]     │
│                                            │
│              [   Se connecter   ]          │
│                                            │
│  Pas encore de compte ? Créer un compte    │
└──────────────────────────────────────────┘
```

## 2. Inscription (`Register.jsx`)

```
┌──────────────────────────────────────────┐
│              Créer un compte               │
│                                            │
│  Tu es ?                                  │
│  ( ) Employé (j'ai un code)                │
│      Ton manager t'a donné un code —       │
│      tu rejoindras une équipe existante    │
│  ( ) Patron de restaurant                  │
│      Tu créeras ta propre équipe            │
│                                            │
│  Prénom  [__________]  Nom [__________]    │
│  Email        [_____________________]     │
│  Mot de passe [_____________________]      │
│  (Au moins 8 caractères)                   │
│                                            │
│             [  Créer mon compte  ]          │
│  Déjà un compte ? Se connecter             │
└──────────────────────────────────────────┘
```

## 3. Dashboard — état sans équipe

```
┌──────────────────────────────────────────┐
│ Crew   Tableau de bord  Planning  Stats … │
├──────────────────────────────────────────┤
│  Bienvenue, Julien !                       │
│  Vous n'êtes encore dans aucune équipe.    │
│  Demandez le code d'invitation à votre     │
│  manager pour rejoindre la vôtre.          │
│                                            │
│  [ Créer une équipe ]  [ Rejoindre une équipe ] │
│                                            │
│  Vous êtes patron de restaurant ?          │
│  Reconnectez-vous en choisissant « Patron  │
│  de restaurant » à l'inscription.          │
└──────────────────────────────────────────┘
```

## 4. Dashboard Manager (`ManagerDashboard.jsx`)

```
┌──────────────────────────────────────────┐
│ Crew   Tableau de bord  Planning  Stats … │
│                          🔔 2 demandes    │
├──────────────────────────────────────────┤
│  Bonjour Sophie, vous êtes manager.        │
│                                            │
│  ┌────────────┐ ┌────────────┐ ┌────────┐ │
│  │ Heures      │ │ Membres     │ │ Sous-   │ │
│  │ planifiées  │ │ actifs      │ │ couvert.│ │
│  │ 148 / 175h  │ │ 12          │ │ 3 slots │ │
│  └────────────┘ └────────────┘ └────────┘ │
│                                            │
│              [ Ouvrir le planning ]        │
└──────────────────────────────────────────┘
```

## 5. Dashboard Équipier (`EquipierDashboard.jsx`)

```
┌──────────────────────────────────────────┐
│ Crew   Tableau de bord  Planning  Profil  │
├──────────────────────────────────────────┤
│  👋 Salut Elena !                          │
│  Tu fais partie de l'équipe                │
│  « Bistrot du Vieux Port »                 │
│                                            │
│  Tes prochains shifts :                    │
│  ┌────────────────────────────────────┐   │
│  │ Lun 14/07  Midi   Salle  11h30-15h  │   │
│  │ Mer 16/07  Soir   Salle  18h-23h    │   │
│  └────────────────────────────────────┘   │
└──────────────────────────────────────────┘
```

## 6. Planning (`Planning.jsx`) + Smart Planner

```
┌──────────────────────────────────────────────────────┐
│ Planning de service      « Semaine précédente »  Cette│
│                            semaine  « Semaine suivante»│
│                        Du 14/07 au 20/07                │
│                                    [⚡ Générer]          │
├──────────┬──────┬──────┬──────┬──────┬──────┬──────┬───┤
│ Équipier │ Lun  │ Mar  │ Mer  │ Jeu  │ Ven  │ Sam  │Dim│
├──────────┼──────┼──────┼──────┼──────┼──────┼──────┼───┤
│ Ahmed     │      │Midi  │      │Soir  │Midi  │Soir  │   │
│ (Chef)    │      │Cuis. │      │Cuis. │Cuis. │Cuis. │   │
│ Elena     │      │Midi  │Soir  │      │Midi  │Soir  │   │
│ (Confirmé)│      │Salle │Salle │      │Salle │Salle │   │
│ Clara     │      │      │Midi  │Midi  │      │      │   │
│ (Junior)  │      │      │Plong.│Plong.│      │      │   │
├──────────┴──────┴──────┴──────┴──────┴──────┴──────┴───┤
│           [ + Ajouter un shift ]                         │
└──────────────────────────────────────────────────────┘

┌─── Smart Planner (modale) ─────────────────────────────┐
│  Planificateur automatique                                │
│  Pour la semaine du 14/07 au 20/07                        │
│                                                            │
│  Densité de service :  ○ Calme  ● Normal  ○ Chargé         │
│  50 % = service tranquille · 100 % = jour plein            │
│                                                            │
│  ☐ Repartir d'un planning vierge                           │
│                                                            │
│              [ Calcul en cours… ]                          │
│                                                            │
│  Proposés : 24     Non couverts : 2                        │
│  ┌──────────────────────────────────────────────────┐    │
│  │ Services non pourvus (en dessous du seuil mini)    │    │
│  │  • Mer — Midi — Cuisine                             │    │
│  │  • Sam — Soir — Bar                                 │    │
│  └──────────────────────────────────────────────────┘    │
│                                                            │
│              [ Appliquer (24 shifts) ]                     │
└────────────────────────────────────────────────────────┘
```

## 7. Équipes (`Teams.jsx`) / Créer (`TeamCreate.jsx`) / Rejoindre (`TeamJoin.jsx`)

```
┌── Créer une équipe ────────────┐   ┌── Rejoindre une équipe ────────┐
│  Nom de l'équipe                │   │  Code d'invitation              │
│  [ ex. Bistrot du Vieux Port ]  │   │  [ CREW-XXXX-XXXX ]             │
│                                  │   │  Demandez ce code à un manager. │
│         [ Créer ]               │   │      [ Demander à rejoindre ]   │
└──────────────────────────────┘   └────────────────────────────────┘
```

## 8. Détail équipe (`TeamDetail.jsx`) — vue manager

```
┌──────────────────────────────────────────┐
│ Bistrot du Vieux Port                       │
│ Code d'invitation : CREW-8F3K-2QXZ  [↻]     │
├──────────────────────────────────────────┤
│  ⏳ En attente (2)                          │
│   • Clara Dupont     [Approuver ▾] [Refuser]│
│   • Ahmed Nasri      [Approuver ▾] [Refuser]│
│                                            │
│  ✅ Membres actifs (12)                     │
│   • Sophie — Manager — Confirmé — Salle    │
│   • Julien — Manager (Admin) — Chef — Cuis.│
│   • Elena  — Équipier — Confirmé — Salle   │
└──────────────────────────────────────────┘
```

## 9. Paramètres équipe (`TeamSettings.jsx`)

```
┌──────────────────────────────────────────┐
│ Paramètres — Bistrot du Vieux Port          │
├──────────────────────────────────────────┤
│  Coefficients de couverture                │
│   Junior   [0.15]  Confirmé [0.40]  Chef [0.60] │
│                                            │
│  Taux horaires (€/h)                        │
│   Junior [11,88]  Confirmé [13,50]  Chef [17,00]│
│                                            │
│  Capacité de service                        │
│   Couverts à 100 % [100]                    │
│                                            │
│  Jours d'ouverture                          │
│   Lun ☐  Mar ☑  Mer ☑  Jeu ☑  Ven ☑  Sam ☑  Dim ☑ │
│                                            │
│              [ Enregistrer ]               │
└──────────────────────────────────────────┘
```

## 10. Statistiques (`Stats.jsx`) — réservé managers

```
┌──────────────────────────────────────────┐
│ Statistiques — Bistrot du Vieux Port        │
├──────────────────────────────────────────┤
│  Shifts par poste (90j)      Par équipier   │
│  ┌─────────────────┐        (30 derniers j) │
│  │ ▓▓▓▓▓▓ Cuisine    │       ┌─────────────┐ │
│  │ ▓▓▓▓▓ Salle       │       │ Ahmed  ▓▓▓▓ │ │
│  │ ▓▓ Bar            │       │ Elena  ▓▓▓  │ │
│  │ ▓ Plonge          │       │ Clara  ▓▓   │ │
│  └─────────────────┘        └─────────────┘ │
│                                            │
│  Évolution sur 30 jours                     │
│  ┌────────────────────────────────────┐   │
│  │      ╱╲    ╱╲╱╲                     │   │
│  │  ╱╲╱╲╱  ╲╱╱    ╲╱╲                  │   │
│  └────────────────────────────────────┘   │
└──────────────────────────────────────────┘
```

## 11. Profil (`Profile.jsx`) — synchronisation calendrier

```
┌──────────────────────────────────────────┐
│ Mon profil                                 │
├──────────────────────────────────────────┤
│  Informations personnelles                  │
│   Prénom [Elena]   Nom [Martin]             │
│   [ Enregistrer ]                           │
│                                            │
│  Mot de passe                               │
│   Actuel [_____]  Nouveau (8 car. min) [___]│
│   [ Modifier ]                              │
│                                            │
│  📲 Synchronisation calendrier               │
│   ( ) Tout — tous mes shifts                │
│   ( ) Équipe Bistrot du Vieux Port           │
│   [QR code]  [ Ouvrir dans Calendrier ]      │
│              [ Copier l'URL ]                │
│                                            │
│   Comment s'abonner ?                       │
│   iPhone : « Ouvrir dans Calendrier » →     │
│   ajout direct depuis Safari.               │
│   Android : calendar.google.com → coller    │
│   l'URL.                                    │
└──────────────────────────────────────────┘
```

---

## Cohérence responsive

Tous les écrans suivent trois points de rupture (cf. `variables.css`,
`--container-w: 1180px`) :
- **Mobile (< 768px)** : navigation en drawer, grille planning en liste
  verticale par jour (une carte par shift), Smart Planner en plein écran.
- **Tablette (768–1024px)** : grille planning scrollable horizontalement,
  cartes stats en 2 colonnes.
- **Desktop (≥ 1024px)** : grille planning complète 7 jours, cartes stats
  en 3-4 colonnes, modales centrées (`--container-w`).
