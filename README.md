# 🍔 Le Défi du Burger — EPI EPS × SVT
### Outil numérique pour la classe de 4ème

---

## Présentation

Cet outil accompagne le projet interdisciplinaire **EPS × SVT** inspiré de l'article *« Le défi du burger »* (Buchs & Mayeko, Revue EPS n°372, 2016).

Il permet de **relier alimentation, activité physique et santé** à travers une interface numérique accessible aux élèves et aux enseignants, sans serveur ni compte requis.

---

## Architecture du projet

```
defi_burger_epi.html    ← fichier unique, tout-en-un (HTML/CSS/JS)
README.md               ← ce fichier
```

Toutes les données sont stockées localement dans le navigateur (`localStorage`). Aucune donnée n'est envoyée sur Internet.

---

## Les trois interfaces

### 🧑‍🎓 Espace Élève

L'élève saisit :
- Son **identité** (prénom, poids, semaine concernée)
- Son **alimentation** de la semaine : aliments ajoutés un par un, avec estimation automatique des calories (base de ~50 aliments courants + interpolation par mots-clés)
- Ses **activités sportives** hors EPS : sport + durée + intensité → estimation MET
- Le **nombre de pas** de la semaine (facultatif, converti en kcal)
- Ses **tours de stade** cumulés sur le cycle EPS

Le **bilan** affiché en temps réel comprend :
- Kcal ingérées (estimation)
- Kcal dépensées (sport + pas + EPS)
- Balance calorique
- **Baromètre burger** : la dépense EPS est comparée à l'apport calorique d'un double burger (500 kcal) via la formule officielle de l'article :

> **Dépense EPS (Kcal) = Poids (kg) × Distance (km)**

---

### 🏃 Interface Enseignant EPS

L'enseignant saisit :
- La **date** et le **type de séance** : fractionné / 1 600 m (4 tours) / trottinement 20 min / échauffement / autre
- Le **périmètre du terrain** (par défaut 400 m)
- Pour chaque élève : **prénom + nombre de tours réalisés** → calcul automatique de la distance et de la dépense énergétique, avec détection du poids si l'élève a enregistré ses données

L'interface génère :
- Un **tableau par séance** avec l'équivalent alimentaire de chaque dépense
- Un **historique** des séances enregistrées
- Un **classement cumulé du cycle** (km + kcal) avec podium

---

### 🔬 Interface Enseignant SVT

Vue synthétique de la classe pour exploitation pédagogique :
- **Statistiques moyennes** : kcal ingérées, dépensées, tours EPS
- **Tableau individuel** de tous les élèves ayant saisi leurs données
- **Équivalences burger** par élève (dépense EPS du cycle ≈ quel aliment ?)
- **Repères nutritionnels** (aliments à favoriser / à limiter)
- **Connexions programme SVT 4ème** (digestion, métabolisme, glycémie…)
- **Export** du tableau de bord (copie presse-papiers → Excel/Sheets)

---

## Séquence EPS intégrée

Trois APSA de demi-fond sont pré-paramétrées :

| Type de séance       | Usage pédagogique |
|----------------------|-------------------|
| Fractionné           | Développer la VMA ; alterner zones course/marche |
| 1 600 m (4 tours)   | Performance mesurable, calcul direct de la dépense |
| Trottinement 20 min  | Endurance fondamentale, estimation via temps × allure |

La formule `Kcal = Poids × Distance` est affichée en en-tête de l'interface EPS.

---

## Base calorique des aliments

La base intégrée contient ~50 aliments courants (fast-food, repas, snacks, boissons, fruits), conformément aux valeurs de l'article (ex : burger 250 kcal, double burger 500 kcal, milkshake 380 kcal…).

Pour les aliments non reconnus, le système applique une estimation par **correspondance partielle** (mots-clés : pizza, sandwich, riz, poulet…) ou retourne une valeur par défaut de **250 kcal** en signalant l'incertitude.

> ⚠️ Ces estimations sont volontairement approximatives. L'objectif est la **sensibilisation**, pas la précision diététique.

---

## Déploiement

**Aucune installation requise.** Il suffit d'ouvrir le fichier `.html` dans un navigateur (Chrome, Firefox, Edge, Safari).

En contexte scolaire :
- Ouvrir sur les postes informatiques de la salle
- Ou héberger sur l'ENT (déposer le fichier dans un espace partagé)
- Sur tablette, le site est responsive (colonne unique sur mobile)

---

## Connexions interdisciplinaires suggérées

| Discipline | Thème |
|---|---|
| **SVT** | Digestion, métabolisme énergétique, obésité, diabète type II |
| **Maths** | Calcul de la dépense : poids × distance, proportionnalité |
| **Anglais** | *Junk food*, lecture d'étiquettes, santé publique |
| **Histoire-Géo** | *Nourrir la planète*, inégalités alimentaires |
| **Technologie** | Tableurs, bases de données, traitement de l'information |

---

## Auteurs de la démarche pédagogique

William **Buchs**, Professeur agrégé d'EPS, Lycée Pauline Roland, Chevilly-Larue (94)  
Teddy **Mayeko**, Professeur agrégé d'EPS, Collège Montesquieu, Beauchamp (95)

*Revue EPS n°372, septembre-octobre 2016*

---

## Données & confidentialité

- Les données sont stockées **localement** dans le navigateur de chaque poste.
- Elles ne sont pas transmises à un serveur externe.
- Pour partager les données entre postes, utiliser la fonction **Export** (onglet SVT) et copier dans un tableur partagé.
- Effacer les données : ouvrir la console du navigateur → `localStorage.clear()`

---

*Outil développé dans le cadre d'un EPI EPS-SVT, classe de 4ème.*
