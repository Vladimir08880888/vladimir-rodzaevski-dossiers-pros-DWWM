# Charte graphique — Crew

> Identité visuelle de l'application. Les valeurs sont définies une seule fois
> dans `front/src/styles/variables.css` et consommées via custom properties
> CSS, garantissant la cohérence visuelle sur l'ensemble de l'interface.

---

## 🎨 Concept : « Bistro / Éditorial »

**Inspiration** : Eater, Le Fooding, Chefs Pencil — la chaleur d'un bistrot
marseillais, sans renoncer à la rigueur d'une interface professionnelle de
gestion de planning.

| Choix | Justification |
|---|---|
| Fond crème | Chaleur, lisibilité dans la durée (utilisation quotidienne en cuisine/salle) |
| Accent terracotta | Vivacité, gourmandise, identité forte et différenciante face aux outils RH génériques |
| Vert romarin (validation) | Naturel, calme — évite le vert saturé « corporate » |
| Bordeaux (urgence) | Réduit la fatigue visuelle par rapport au rouge pur, reste dans la palette terroir |

### Couleurs primaires

| Variable | Hex (clair) | Hex (sombre) | Usage |
|---|---|---|---|
| `--primary` | `#c3553a` | `#d96b4e` | Boutons d'action, liens, focus |
| `--primary-hover` | `#a8442e` | `#c3553a` | État survol |
| `--primary-grad` | `linear-gradient(135deg, #c3553a → #d4a514 → #8b2c14)` | idem, tons éclaircis | Branding, header, CTAs majeurs |

### Couleurs sémantiques (statuts)

| Variable | Hex | Sens |
|---|---|---|
| `--success` | `#4a5c3f` (vert romarin) | Shift confirmé, action réussie |
| `--warning` | `#d4a514` (safran) | Membre en attente d'approbation, créneau à risque |
| `--danger` | `#8b2c14` (bordeaux) | Créneau non couvert, erreur, suppression |
| `--info` | `#4a6b7a` (bleu ardoise) | Notification informative |

### Couleurs par poste (planning)

| Variable | Hex | Poste |
|---|---|---|
| `--cat-Santé` (réutilisé) | `#8b2c14` | Urgent / non couvert |
| `--cat-Finances` | `#d4a514` | Bar |
| `--cat-Administratif` | `#4a6b7a` | Administration |
| `--cat-Véhicule` | `#4a5c3f` | Salle |
| `--cat-Logement` | `#7c4d2e` | Plonge |
| `--cat-Corvée` | `#c3553a` | Cuisine |

### Surfaces (glass papier crème)

| Variable | Valeur | Usage |
|---|---|---|
| `--glass` | `rgba(255, 251, 240, 0.72)` | Cartes, panneaux |
| `--glass-strong` | `rgba(255, 251, 240, 0.88)` | Modales |
| `--glass-elevated` | `rgba(255, 252, 244, 0.96)` | Popovers, dropdowns |
| `--glass-border` | `rgba(195, 85, 58, 0.18)` | Bordures discrètes |

### Mode sombre — « bistrot de nuit »

Le thème sombre n'est pas une simple inversion : les tons terracotta
deviennent plus lumineux (`#d96b4e`) pour rester lisibles sur fond brun
très sombre (`#1c1612`), et les ombres passent en noir pur pour un rendu
plus profond (`0 20px 50px rgba(0,0,0,0.65)` en `--shadow-lg`).

---

## ✍️ Typographies

| Rôle | Police | Fallback | Usage |
|---|---|---|---|
| Titres (h1-h3) | Cormorant Garamond | EB Garamond, Georgia, serif | Identité éditoriale forte, en-têtes de page |
| Corps de texte | Inter | -apple-system, Segoe UI, Roboto | Lisibilité optimale, formulaires, tableaux |
| Données / code | JetBrains Mono | Fira Code, ui-monospace | Heures, montants, tokens techniques |

### Échelle typographique

| Niveau | Taille | Line-height |
|---|---|---|
| `h1` | 2.25rem | 1.15 |
| `h2` | 1.75rem | 1.2 |
| `h3` | 1.35rem | 1.25 |

---

## 🧱 Système d'espacement et de forme

| Variable | Valeur |
|---|---|
| `--r-xs` … `--r-xl` | 4px → 24px (registre éditorial, coins plus serrés qu'un SaaS classique) |
| `--r-full` | 9999px (pastilles de statut, avatars) |
| `--nav-h` | 64px |
| `--container-w` | 1180px |

## 🌊 Ombres et flous

Ombres chaudes (teinte brune plutôt que noir pur) pour rester cohérentes
avec la palette bistrot : `--shadow-md: 0 8px 28px rgba(124, 77, 46, 0.14)`.
Glassmorphism via `backdrop-filter: blur(14px) saturate(160%)`.

## 🎬 Animations

| Variable | Valeur | Usage |
|---|---|---|
| `--ease` | `cubic-bezier(0.4, 0, 0.2, 1)` | Transitions standard |
| `--ease-bounce` | `cubic-bezier(0.34, 1.56, 0.64, 1)` | Confirmations, succès |
| `--t-fast` / `--t-base` / `--t-slow` | 120ms / 220ms / 400ms | Durées standardisées |

**Accessibilité** : `@media (prefers-reduced-motion: reduce)` désactive
toutes les animations (`animation-duration: 0.01ms !important`).

---

## Historique de la palette

Le thème a évolué en cours de projet : une première itération indigo/SaaS
générique a été testée, puis abandonnée au profit de la palette
« Bistro/Éditorial » actuelle, jugée plus différenciante et alignée avec le
persona utilisateur (restauration indépendante, ambiance « Bistrot du Vieux
Port »).
