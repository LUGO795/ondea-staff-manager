# Ondea Staff Manager

> Plateforme locale de gestion du personnel, des missions et de la communication interne.
> **100 % autonome, sans serveur, sans installation** : un seul fichier `index.html`.

![Version](https://img.shields.io/badge/version-1.0-c9a24b)
![Stack](https://img.shields.io/badge/stack-HTML%20%C2%B7%20CSS%20%C2%B7%20JavaScript-0b0d10)
![Hors--ligne](https://img.shields.io/badge/hors--ligne-100%25-5aa87a)
![Accessibilité](https://img.shields.io/badge/accessibilit%C3%A9-contraste%20%C3%A9lev%C3%A9%20%C2%B7%20clavier-86b6d4)

---

## Sommaire

1. [Présentation](#présentation)
2. [Points forts](#points-forts)
3. [Démarrage rapide](#démarrage-rapide)
4. [Comptes de démonstration](#comptes-de-démonstration)
5. [Rôles et droits](#rôles-et-droits)
6. [Fonctionnalités](#fonctionnalités)
7. [Accessibilité et confort](#accessibilité-et-confort)
8. [Données et sauvegarde](#données-et-sauvegarde)
9. [Configuration](#configuration)
10. [Architecture technique](#architecture-technique)
11. [Compatibilité](#compatibilité)
12. [Sécurité : à lire avant une mise en production](#sécurité--à-lire-avant-une-mise-en-production)
13. [Dépannage](#dépannage)
14. [Feuille de route](#feuille-de-route)
15. [Crédits et licence](#crédits-et-licence)

---

## Présentation

**Ondea Staff Manager** est une application web de gestion des ressources humaines pensée pour les TPE/PME, les associations et les équipes techniques. Elle regroupe dans une seule interface :

- le suivi du **personnel** (fiches, compétences, présence, statut du compte) ;
- le pilotage des **missions** en tableau Kanban ;
- le **planning** mensuel ;
- la **messagerie interne** et les **demandes** des salariés (congés, télétravail, matériel…) ;
- les **évaluations**, les **statistiques** et le **journal d'activité**.

Tout fonctionne **dans le navigateur**, sans base de données externe ni connexion Internet obligatoire. Les données restent sur le poste de l'utilisateur.

---

## Points forts

| | |
|---|---|
| **Zéro installation** | Un double-clic sur `index.html` suffit. |
| **Hors-ligne** | Polices intégrées, aucune dépendance externe. Seule la météo (optionnelle) utilise Internet. |
| **Deux espaces** | Un espace **Administration** (Direction, Manager, Administrateur) et un espace **Salarié**. |
| **Design « Obsidienne & Or »** | Thème sombre ou clair, verre dépoli, bordures dorées, micro-animations. |
| **Accessible** | Contraste élevé, navigation au clavier, lecteurs d'écran, respect de « réduire les animations ». |
| **Modulaire** | Chaque module (missions, messagerie, planning…) s'active ou se désactive dans les paramètres. |
| **Portable** | Export et import de toutes les données au format JSON. |

---

## Démarrage rapide

1. **Téléchargez** le fichier `index.html`.
2. **Ouvrez-le** dans un navigateur récent (Chrome, Edge, Firefox, Safari).
3. **Connectez-vous** avec l'un des comptes de démonstration ci-dessous, ou cliquez directement sur un compte dans la liste « Comptes de démonstration » de l'écran de connexion.

C'est tout. Au premier lancement, l'application crée automatiquement une entreprise fictive avec 9 collaborateurs, 7 missions, des messages, des demandes et des événements de planning.

> **Astuce** : pour un usage en équipe sur un même réseau, vous pouvez déposer `index.html` sur n'importe quel hébergement statique (serveur Apache/Nginx, NAS, GitHub Pages…). Chaque navigateur conserve **ses propres données** : il n'y a pas de synchronisation entre postes dans cette version.

---

## Comptes de démonstration

| Rôle | Identifiant | Mot de passe | Espace |
|---|---|---|---|
| Direction | `marie.martin` | `admin123` | Administration |
| Manager | `thomas.bernard` | `manager123` | Administration |
| Manager (RH) | `lea.moreau` | `manager123` | Administration |
| Salarié | `jean.dupont` | `staff123` | Salarié |
| Administrateur | `admin` | `admin` | Administration |

Les autres salariés de démonstration (`sophie.petit`, `paul.durand`, `hugo.lefevre`, `camille.roux`) utilisent aussi le mot de passe `staff123`.

> ⚠️ **Changez ou supprimez ces comptes** avant toute utilisation réelle (voir [Sécurité](#sécurité--à-lire-avant-une-mise-en-production)).

---

## Rôles et droits

| Fonction | Administrateur | Direction | Manager | Salarié |
|---|:---:|:---:|:---:|:---:|
| Tableau de bord de pilotage (KPI) | ✅ | ✅ | ✅ | — |
| Tableau de bord personnel | — | — | — | ✅ |
| Gérer le personnel (ajout, modification, photo) | ✅ | ✅ | ✅ | — |
| Activer / désactiver un compte salarié | ✅ | ✅ | — | — |
| Créer et suivre toutes les missions (Kanban) | ✅ | ✅ | ✅ | — |
| Voir et mettre à jour **ses** missions | — | — | — | ✅ |
| Planning | ✅ | ✅ | ✅ | ✅ |
| Messagerie interne | ✅ | ✅ | ✅ | ✅ |
| Traiter les demandes (accepter / refuser) | ✅ | ✅ | ✅ | — |
| Soumettre une demande | — | — | — | ✅ |
| Documents | ✅ | ✅ | ✅ | ✅ |
| Évaluations, statistiques, journal d'activité | ✅ | ✅ | ✅ | — |
| Paramètres, modules, sauvegarde | ✅ | ✅ | ✅ | — |
| Mon profil | — | — | — | ✅ |

Un compte **Administrateur** ne peut jamais être désactivé. Un compte **désactivé** ne peut plus se connecter et apparaît avec un repère « Désactivé » dans la liste du personnel.

---

## Fonctionnalités

### Espace Administration

- **Tableau de bord**
  - Cartes KPI cliquables : salariés, présents, missions actives, missions en retard, demandes en attente, salariés inactifs.
  - La carte « Missions en retard » clignote dès qu'une mission a dépassé son échéance.
  - Missions en cours, événements du jour et fil d'activité.
  - Mise à jour en temps réel après chaque action.
- **Personnel**
  - Tableau paginé (6 salariés par page).
  - Recherche, filtres par département, équipe et présence.
  - Fiche détaillée en panneau latéral : coordonnées, contrat, compétences avec niveau, photo, notes.
- **Missions (Kanban)**
  - Colonnes « À faire », « En cours », « Terminées », plus une colonne automatique **« En retard »**.
  - Glisser-déposer des cartes entre colonnes.
  - Priorité (haute, moyenne, basse), responsable, équipe assignée, dates, progression et check-list.
- **Planning** : calendrier mensuel avec réunions, congés, échéances de missions et formations, chacun avec sa couleur.
- **Messagerie** : conversations individuelles, compteur de messages non lus.
- **Demandes** : congé, absence, télétravail, matériel, formation, RH, demande exceptionnelle. La cloche de l'en-tête affiche le nombre de demandes en attente et ouvre directement la liste.
- **Documents** : dépôt et consultation de fichiers et médias, stockés localement.
- **Évaluations** : grille notée sur 5 (ponctualité, qualité, autonomie, communication, technique) et commentaire.
- **Statistiques** : indicateurs de performance, graphiques en barres et en anneau.
- **Journal d'activité** : traçabilité des connexions et des actions.
- **Paramètres** : informations de l'entreprise, activation des modules, sauvegarde et réinitialisation.

### Espace Salarié

- **Mon tableau de bord** : mes missions, mes échéances, mes messages.
- **Mes missions** : suivi de l'avancement et de la check-list.
- **Mon planning**, **Messages**, **Mes demandes**, **Documents**.
- **Mon profil** : mes informations et mes compétences.

### Fonctions communes

- **Recherche globale** dans l'en-tête : saisissez un nom de salarié ou de mission, puis `Entrée`.
- **Présence en temps réel** : l'utilisateur connecté passe « Absent » quand l'onglet est caché ou inactif. La présence des collègues est simulée dans la démonstration.
- **Horloge** avec les secondes dans la barre latérale.
- **Météo géolocalisée** (optionnelle, désactivée par défaut).
- **Notifications** par toasts.
- **Bouton « Retour en haut »** avec un triple retour à l'arrivée : un son, un flash visuel et une vibration sur mobile.
- **Fond animé** : des icônes discrètes défilent derrière le contenu. Un bouton Pause / Lecture dans l'en-tête les arrête ou les relance, et ce choix est mémorisé.

---

## Accessibilité et confort

- **Thème clair ou sombre** : bouton dans l'en-tête et sur l'écran de connexion. Le choix est mémorisé.
- **Contraste élevé** : bouton dédié dans l'en-tête, disponible en thème clair et sombre. Il retire les effets de transparence et les dégradés.
- **Réduire les animations** : si ce réglage est activé dans le système, animations et transitions sont désactivées automatiquement.
- **Pause des animations d'arrière-plan** : bouton dédié dans l'en-tête.
- **Clavier**
  - `Tab` / `Maj+Tab` : parcourir l'interface.
  - `Entrée` / `Espace` : activer un élément.
  - `Échap` : fermer une fenêtre, un panneau ou un menu.
  - `Entrée` dans le champ de recherche : lancer la recherche.
- **Lecteurs d'écran** : libellés ARIA sur les boutons, régions `aria-live` pour les notifications, décors masqués (`aria-hidden`).
- **Police Atkinson Hyperlegible**, conçue pour les personnes malvoyantes.

---

## Données et sauvegarde

### Où sont stockées les données ?

| Données | Emplacement | Clé |
|---|---|---|
| Salariés, missions, messages, demandes, planning, évaluations, paramètres | `localStorage` | `ondea_staff_v1` |
| Photos et documents | `IndexedDB` | base `OndeaStaffMediaDB`, magasin `media` |
| Thème | `localStorage` | `ondea_theme` |
| Contraste élevé | `localStorage` | `ondea_contrast` |
| Pause des animations d'arrière-plan | `localStorage` | `ondea_bg_icons` |

Si le navigateur bloque le stockage (navigation privée stricte, cadre isolé), l'application bascule automatiquement sur un **stockage en mémoire**. Elle reste utilisable, mais **les données sont perdues à la fermeture de l'onglet**.

### Sauvegarder et restaurer

Rendez-vous dans **Paramètres → Sauvegarde des données** :

- **Exporter (JSON)** : télécharge un fichier `ondea-staff-AAAA-MM-JJ.json`.
- **Importer** : remplace toutes les données actuelles par le contenu d'une sauvegarde.
- **Réinitialiser** : efface tout et recharge les données de démonstration. Cette action est **irréversible**.

> ⚠️ L'export JSON contient les données de `localStorage`, **pas les photos ni les documents** stockés dans IndexedDB. Conservez les fichiers originaux de votre côté.

> 💡 Vider le cache ou les données de site du navigateur **efface aussi les données** de l'application. Exportez régulièrement.

---

## Configuration

### Modules

Dans **Paramètres → Modules actifs**, vous pouvez activer ou désactiver :

- Missions & Kanban
- Messagerie interne
- Planning
- Évaluations
- Demandes des salariés
- Notifications
- Météo en ligne (désactivée par défaut)

Un module désactivé disparaît du menu pour tous les utilisateurs.

### Entreprise

Dans **Paramètres → Entreprise**, vous pouvez renseigner le nom, le téléphone, l'e-mail, l'adresse et le site web. Le nom de l'entreprise s'affiche dans la barre latérale.

### Météo (OpenWeather)

La météo utilise l'API OpenWeather et la géolocalisation du navigateur. Pour utiliser **votre propre clé** :

1. Créez un compte gratuit sur [openweathermap.org](https://openweathermap.org/api).
2. Ouvrez `index.html` dans un éditeur de texte et cherchez `OWM_KEY`.
3. Remplacez la valeur par votre clé.

```js
var OWM_KEY='VOTRE_CLE_ICI';
```

---

## Architecture technique

```
index.html
├── <style id="ondea-fonts">   Polices intégrées en base64 (Playfair Display,
│                              Atkinson Hyperlegible, JetBrains Mono)
├── <style>                    Design system « Obsidienne & Or » (variables CSS,
│                              thèmes clair / sombre / contraste élevé, couche « Signature 2026 »)
├── Écran de connexion (#login)
├── Application (#app)
│   ├── Barre latérale (#sidebar)  navigation, horloge, météo, utilisateur
│   ├── En-tête (.topbar)          recherche, pause animations, contraste, thème, cloche
│   └── Zone principale (#main)    vues rendues dynamiquement
├── Modale, panneau latéral, toasts
└── <script>                   Moteur applicatif + modules additifs
```

| Élément | Rôle |
|---|---|
| `STORE` | Accès au stockage avec repli automatique en mémoire. |
| `DB` | Objet unique contenant toutes les données, sauvegardé par `persist()`. |
| `IDB` | Surcouche IndexedDB pour les photos et les documents. |
| `VIEWS` | Une fonction de rendu par écran (`dashboard`, `personnel`, `missions`…). |
| `navigate(vue)` | Routeur : affiche la vue demandée. |
| `NAV_MGMT` / `NAV_STAFF` | Menus des espaces Administration et Salarié. |
| Modules additifs | Blocs `<script>` autonomes : colonne « En retard », comptes actifs/inactifs, KPI « Salariés inactifs », badges de demandes, bouton « Retour en haut », contraste, fond animé… Ils enveloppent les fonctions existantes sans les réécrire. |

**Technologies** : HTML5, CSS3 (variables, `color-mix`, `backdrop-filter`, `@property`, `:has()`), JavaScript vanilla (ES2020), `localStorage`, IndexedDB, Web Audio API, API Geolocation. **Aucun framework, aucune bibliothèque externe.**

---

## Compatibilité

| Navigateur | Version conseillée |
|---|---|
| Google Chrome / Microsoft Edge | 111 et plus |
| Mozilla Firefox | 113 et plus |
| Safari (macOS / iOS) | 16.4 et plus |

L'interface est **responsive** : sur mobile, la barre latérale se replie derrière un bouton menu. Sur un navigateur plus ancien, l'application reste fonctionnelle, mais certains effets visuels (verre dépoli, bordure tournante) peuvent être simplifiés.

---

## Sécurité : à lire avant une mise en production

Cette version est une **application de démonstration et de formation** qui fonctionne entièrement côté client. Avant de l'utiliser avec de vraies données :

- **Mots de passe** : ils sont stockés **en clair** dans le navigateur. N'y enregistrez pas de mots de passe réels et changez tous les comptes de démonstration.
- **Données personnelles** : toute personne ayant accès au poste et au navigateur peut lire les données (outils de développement). Réservez l'application à un poste protégé par session.
- **RGPD** : vous restez responsable des données saisies (information des salariés, durée de conservation, droit d'accès et d'effacement).
- **Clé météo** : la clé OpenWeather est visible dans le code source. Utilisez votre propre clé, restreinte à votre domaine, ou laissez la météo désactivée.
- **Verrouillage** : après 5 échecs de connexion, l'écran de connexion est bloqué sur ce navigateur.

Pour un usage multi-postes sécurisé (mots de passe hachés, sessions serveur, base de données partagée), voir la [feuille de route](#feuille-de-route).

---

## Dépannage

| Problème | Solution |
|---|---|
| **Les données disparaissent à la fermeture** | Le navigateur bloque le stockage (navigation privée, paramètres de confidentialité). Ouvrez le fichier dans une fenêtre normale ou autorisez les données de site. |
| **« Stockage des photos indisponible dans ce contexte »** | IndexedDB est bloqué. Même solution que ci-dessus. |
| **« Compte temporairement verrouillé après 5 tentatives »** | Le compteur d'échecs est enregistré dans les données locales. Pour débloquer : outils de développement (`F12`) → *Application* → *Local Storage* → supprimez la clé `ondea_staff_v1`. **Attention**, cela réinitialise toutes les données : exportez-les d'abord si vous le pouvez. |
| **La météo ne s'affiche pas** | Activez le module dans les paramètres, autorisez la géolocalisation et vérifiez la connexion Internet. Sans géolocalisation, la météo de Paris s'affiche par défaut. |
| **« Fichier invalide » à l'import** | Le fichier doit être un export JSON d'Ondea Staff Manager (il doit contenir une liste `employees`). |
| **Un compte ne peut plus se connecter** | Il a peut-être été désactivé. Un administrateur ou la Direction peut le réactiver depuis la fiche du salarié. |
| **Les animations gênent la lecture** | Utilisez le bouton Pause de l'en-tête, ou activez « réduire les animations » dans votre système. |

---

## Feuille de route

- **V1 (actuelle)** : application 100 % locale en un seul fichier.
- **V2 (prévue)** : version **PHP · PDO · MVC** avec base de données MySQL/MariaDB :
  - mots de passe hachés (`password_hash`) et sessions serveur ;
  - données partagées entre tous les postes ;
  - protection CSRF et requêtes préparées ;
  - import des sauvegardes JSON de la V1.

---

## Crédits et licence

**Conception et développement** : Jean-Claude Lugo, [Ondea Web Studio](https://ljcwhisper8.gumroad.com)
**Design system** : « Obsidienne & Or »
**Polices** : Playfair Display, Atkinson Hyperlegible (Braille Institute), JetBrains Mono, toutes sous licence SIL Open Font License 1.1
**Météo** : [OpenWeather](https://openweathermap.org) (service tiers optionnel)

© 2026 Ondea Web Studio. Tous droits réservés.
L'utilisation de ce fichier est régie par la licence fournie avec votre achat.
