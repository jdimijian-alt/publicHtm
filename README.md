# Le Compte Est Bon

> Implémentation web du célèbre jeu de calcul mental de l'émission *Des Chiffres et des Lettres*.

**Version 1.0** — par Joseph Dimijian · Portage web avec Claude (Anthropic)

---

## Présentation

*Le Compte Est Bon* est un jeu de calcul mental : à partir de 6 plaques tirées aléatoirement, le joueur doit atteindre un nombre cible en utilisant les quatre opérations arithmétiques (+, −, ×, /).

Ce projet est la version web d'un programme ABAP/SAP original écrit en 2011, porté successivement en Python puis en application web HTML/JS autonome.

---

## Caractéristiques techniques

- **Fichier unique** : `index.html` — aucune dépendance externe, aucun serveur nécessaire
- **PWA** : installable sur iPhone (Safari) et Android (Chrome) via "Ajouter à l'écran d'accueil"
- **Offline** : fonctionne sans connexion après la première ouverture
- **Compatible** : Chrome, Firefox, Safari, Edge — desktop et mobile

---

## Modes de jeu

### 🔵 Partie libre
Tirages illimités, pas de score comptabilisé, le bouton Résoudre est toujours accessible. Idéal pour s'entraîner.

### 🔴 Compétition
Partie avec graine (numéro fixe ou tiré au sort 🎲), nombre de tirages défini (30 par défaut). Score calculé selon les résultats et le temps. Fin de partie avec récapitulatif. Un tirage doit être validé avant de passer au suivant.

### ⬜ Solveur
Saisie libre des plaques et de la cible. Le solveur calcule la meilleure solution. Aucune contrainte de temps ni de score.

---

## Fonctionnalités

### Tirage
- **CEB 24** : tirage classique (1–10 ×2, 25/50/75/100 ×1)
- **CEB 28** : grands nombres en double (25/50/75/100 ×2)
- **Aléatoire 20** : 1–10 ×2 + 8 nombres entre 11 et 99
- Cible forcément atteignable (option)
- Plage cible configurable (101–999 par défaut)
- Graine reproductible : même graine = même séquence de tirages

### Saisie interactive
- Sélection des plaques par clic
- Opérateurs +, −, ×, /
- Affichage de l'opération en cours en temps réel
- **Phase 4 — révision** : quand on remonte une ligne précédente via ⌫, la ligne entière s'affiche avec code couleur (op1 jaune, opérateur orange modifiable, op2 bleu modifiable)
- Reprise automatique du résultat comme premier opérande du calcul suivant

### Correction (⌫)
Effacement granulaire phase par phase :
- ⌫ en phase 3 → efface l'opérateur
- ⌫ en phase 2 → efface op1 et remonte la ligne précédente si elle existe
- ⌫ en phase 4 → efface op2 (retour phase 3)
- 🗑 dans la boîte Calculs → remet toutes les plaques à zéro

### Solveur intégré
- **Meilleure solution** : trouve la solution la plus proche en un minimum d'étapes
- **Première exacte** : s'arrête dès qu'un compte exact est trouvé
- **Toutes (récur ≤ 3)** : explore tous les chemins alternatifs (fidèle au comportement ABAP v1.30)
- Popup de solution avec détail, nombre d'opérations testées, solutions exactes alternatives

### Scores
- In time / Out of time selon le temps limite configuré
- Grille de points configurable (exact / approché ±1-3 / raté)
- Timeout global en compétition (warning à N secondes)

### Statistiques
- Globales : parties, tirages, score total, précision, temps moyen
- Par partie : historique des 100 dernières parties
- Par mode et par graine

### Options
Deux onglets dans le panneau Options :
- **Partie & Plaques** : mode de jeu, graine, modèle de plaques, nombre de plaques, plage cible
- **Temps & Scores** : temps limite, timeout global, grille de scores, mode solveur, orientation écran

---

## Générateur aléatoire

Le tirage utilise le générateur pseudo-aléatoire de la calculatrice **HP-11C**, implémenté en BigInt JavaScript pour une fidélité exacte au programme ABAP original :

```
next = (next × 1574352261 + 1017980433) mod 10000000000
```

Une graine fixe garantit la reproductibilité complète d'une partie.

---

## Installation

### Utilisation directe
Télécharge `index.html` et ouvre-le dans un navigateur. Aucune installation requise.

### GitHub Pages
Le fichier est déployé automatiquement via GitHub Pages à l'adresse :
```
https://<username>.github.io/<repository>/
```

### PWA (iPhone / Android)
1. Ouvre l'URL dans Safari (iOS) ou Chrome (Android)
2. "Partager" → "Ajouter à l'écran d'accueil" (iOS) ou "Installer l'application" (Android)
3. L'icône apparaît sur l'écran d'accueil, l'appli fonctionne hors ligne

---

## Historique des versions

| Version | Description |
|---------|-------------|
| **1.0** | Version web initiale — moteur complet, 3 modes, solveur, stats, PWA |

---

## Crédits

- **Concept & logique originale** : Joseph Dimijian — programme ABAP/SAP, 2011
- **Portage web** : Joseph Dimijian + Claude (Anthropic), 2024–2025
- **Algorithme de résolution** : récursion fidèle à la version ABAP 1.30
- **Générateur aléatoire** : HP-11C RNG (BigInt)

---

## Licence

© Joseph Dimijian — Tous droits réservés.  
Usage personnel autorisé. Redistribution ou usage commercial interdits sans autorisation.
