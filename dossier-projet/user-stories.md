# User Stories — Crew

> Toutes les fonctionnalités exprimées du point de vue utilisateur.
> Format Connextra : **En tant que** … **je veux** … **afin de** …

---

## 🔓 Authentification

### US-01 — Création de compte
**En tant que** visiteur sans compte,
**je veux** m'inscrire avec mon email, un mot de passe, mon prénom et nom, et
préciser si je suis « Employé (j'ai un code) » ou « Patron de restaurant »,
**afin d'**accéder à Crew et démarrer avec le bon parcours (rejoindre vs créer
une équipe).

**Critères d'acceptation** :
- L'email est validé côté front et back (`validators/auth`)
- Le mot de passe doit faire au moins 8 caractères
- Si l'email est déjà pris → « Cet email est déjà utilisé » (409)
- À la création réussie, je suis automatiquement connecté (JWT retourné)
- Un `calendar_token` unique est généré pour mon flux iCal personnel

### US-02 — Connexion
**En tant qu'**utilisateur enregistré,
**je veux** me connecter avec email et mot de passe,
**afin de** retrouver mon planning et mon équipe.

**Critères** : identifiants incorrects → message générique « Identifiants
incorrects » (401), pas de distinction email inconnu / mauvais mot de passe
(anti-énumération) ; rate limiting sur `/login` et `/register`.

---

## 👥 Équipes

### US-03 — Créer une équipe
**En tant que** patron de restaurant,
**je veux** créer une équipe en lui donnant un nom,
**afin de** devenir manager admin et obtenir un code d'invitation à partager
avec mon personnel.

**Critères** : je suis automatiquement ajouté comme `role=manager,
is_admin=true, status=active` ; un `invite_code` unique est généré.

### US-04 — Rejoindre une équipe
**En tant qu'**employé disposant d'un code,
**je veux** saisir le code d'invitation de mon restaurant,
**afin d'**envoyer une demande de rattachement à l'équipe.

**Critères** : statut initial `pending` ; je ne peux pas envoyer deux
demandes pour la même équipe (409 si déjà membre ou en attente).

### US-05 — Approuver un membre
**En tant que** manager,
**je veux** voir la liste des demandes en attente et choisir le rôle
(manager ou équipier) à l'approbation,
**afin d'**intégrer un nouvel équipier dans le planning.

**Critères** : un membre `pending` n'apparaît jamais dans le Smart Planner
ni sur le planning visible tant qu'il n'est pas `active`.

### US-06 — Configurer un équipier
**En tant que** manager,
**je veux** définir pour chaque membre son poste primaire (cuisine, salle,
bar, plonge, administration), son niveau (junior/confirmé/chef), son shift
habituel, ses heures cibles hebdomadaires et sa polyvalence (skills),
**afin que** le Smart Planner produise des propositions réalistes.

### US-07 — Régénérer le code d'invitation
**En tant qu'**admin d'équipe,
**je veux** régénérer le code d'invitation,
**afin de** révoquer l'accès à un ancien code (ex. fuite, ancien salarié).

---

## 📅 Planning & Smart Planner

### US-08 — Générer un planning automatiquement
**En tant que** manager,
**je veux** lancer le Smart Planner sur une semaine en choisissant une
densité de service (calme/normal/chargé),
**afin d'**obtenir en quelques secondes une proposition de planning qui
respecte la couverture cible, la polyvalence, le coût salarial et le droit
du travail (plafond HCR, repos), sans avoir à tout affecter manuellement.

**Critères d'acceptation** :
- Le solver ne crée rien directement : il retourne un aperçu
  (`suggested[]`, `uncovered[]`, `hours{}`)
- Les créneaux non couverts sont signalés explicitement
- Option « Repartir d'un planning vierge » pour ignorer l'existant

### US-09 — Appliquer le planning proposé
**En tant que** manager,
**je veux** valider la proposition du Smart Planner,
**afin de** créer réellement les shifts en base, visibles par les équipiers.

**Critères** : les doublons (même équipier/jour/type de shift) sont ignorés
silencieusement, pas d'erreur bloquante.

### US-10 — Modifier un shift manuellement
**En tant que** manager,
**je veux** ajouter, déplacer ou supprimer un shift directement sur la
grille planning,
**afin de** corriger un cas particulier que l'automatisation n'a pas
anticipé.

### US-11 — Dupliquer / vider une semaine
**En tant que** manager,
**je veux** copier le planning de la semaine précédente ou tout effacer,
**afin de** gagner du temps sur les semaines récurrentes ou repartir de
zéro en cas d'erreur globale.

### US-12 — Consulter mon planning
**En tant qu'**équipier,
**je veux** voir mes prochains shifts (jour, créneau, poste) depuis mon
tableau de bord,
**afin de** connaître mes horaires de travail sans appeler mon manager.

---

## 📲 Synchronisation calendrier

### US-13 — S'abonner à son flux iCal personnel
**En tant qu'**équipier,
**je veux** scanner un QR code ou copier une URL depuis mon profil,
**afin que** mes shifts apparaissent automatiquement dans mon application
calendrier native (iPhone/Android), avec rappel avant chaque service.

**Critères** : aucune app à installer, mise à jour automatique (polling
1-4h selon l'OS), variante « toute mon activité » ou « une équipe précise ».

### US-14 — Exporter le planning d'équipe
**En tant que** manager,
**je veux** obtenir un flux iCal de l'ensemble du planning d'équipe,
**afin de** le partager en lecture seule (ex. affichage cuisine).

---

## 📊 Statistiques

### US-15 — Suivre la répartition des shifts
**En tant que** manager,
**je veux** consulter la répartition des shifts par poste (90 jours) et par
équipier (30 jours), ainsi que l'évolution du volume,
**afin de** repérer les déséquilibres de charge et ajuster les effectifs.

**Critères** : page réservée aux managers (`stats.managersOnly`).

---

## 👤 Profil & sécurité

### US-16 — Modifier mon profil
**En tant qu'**utilisateur,
**je veux** modifier mon prénom, nom et mot de passe,
**afin de** garder mes informations à jour.

### US-17 — Réinitialiser le mot de passe d'un équipier
**En tant que** manager,
**je veux** générer un mot de passe temporaire pour un membre qui a perdu
ses accès,
**afin de** débloquer la situation sans dépendre d'un support technique.

---

## 🌍 Internationalisation

### US-18 — Utiliser l'application dans sa langue
**En tant qu'**équipier non francophone,
**je veux** basculer l'interface en anglais,
**afin de** comprendre mon planning sans barrière de langue.

**Critères** : couverture complète des textes via `fr.json` / `en.json`,
aucun texte codé en dur dans les composants.
