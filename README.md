# publicHtm
Son fonctionnement combine une interface interactive avec un moteur de résolution algorithmique puissant. Voici comment il agit, décryptage étape par étape.

1. Mode de jeu : "Partie libre" vs "Compétition"

Le programme offre deux grands modes via l'onglet "⚙ Options du jeu" :

· Partie libre : Vous saisissez manuellement la Cible (ex: 543) et jusqu'à 6 Plaques (ex: 2, 50, 75, 100, 6, 6). C'est le terrain de jeu classique.
· Compétition : Vous choisissez une graine (nombre qui initialise le hasard) et un nombre de tirages. Le programme génère automatiquement les cibles et plaques. Un système de score et de temps limite s'active alors.

2. Le Moteur de Résolution (Solveur)

C'est le cœur algorithmique. Quatre options sont proposées sous "SOLVEUR > Mode résolution" :

· Meilleure solution : Cherche la solution la plus précise (compte exact, sinon l'approche la plus proche possible). C'est le mode standard.
· Première exacte : S'arrête dès qu'une solution parfaite est trouvée. Plus rapide, mais ne garantit pas la solution la plus courte ou élégante.
· Toutes (récur ≤ 3) : Trouve toutes les solutions exactes, mais limite la profondeur de recherche à 3 étapes (pour éviter l'explosion combinatoire). Moins exhaustif.

Mécanisme interne probable :
Il utilise un algorithme de recherche arborescente (backtracking). Il génère toutes les combinaisons possibles de plaques avec les opérations (+, -, ×, ÷), en vérifiant les divisions exactes et les résultats positifs. Il compare ensuite chaque résultat à la cible.

3. Interaction utilisateur

Vous pouvez aussi jouer à la main :

· Cliquez sur une plaque.
· Cliquez sur une opération (+, -, ×, /).
· Cliquez sur une autre plaque.
· Le calcul s'affiche et le résultat devient une nouvelle "plaque" virtuelle.
  Le programme valide alors si vous approchez ou atteignez la cible.

4. Les "Options" avancées (très intéressantes)

Sous "⚙ Options du jeu", vous modifiez des paramètres profonds du solveur :

· Modèle de plaques : Classique CEB 24 (1,2,3,4,5,6,7,8,9,10,25,50,75,100) ou CEB 28 (ajoute 11-20, 30, 35, 40, 45, 60-90).
· Cible forcément atteignable : Le programme garantit la génération d'un tirage soluble.
· Temps limite : Pour le mode compétition, avec une logique de score différente si vous êtes "dans les temps" ou "hors temps".

Performances (basé sur l'analyse de son interface)

· Solveur exhaustif : Pour 6 plaques, la recherche de la meilleure solution est quasi instantanée (moins d'une seconde).
· Mode "Toutes" : L'option Toutes (récur ≤ 3) limite délibérément l'exploration pour rester fluide. Une recherche vraiment exhaustive de toutes les solutions exactes (sans limite) prendrait plus de temps et n'est pas proposée.
· Le confort : Le bouton "Résoudre" lance le solveur. Le bouton "Détail…" montre le déroulement des opérations.

En résumé : un solveur "semi-exhaustif"

Ce programme agit comme un solveur intelligent qui, pour le mode classique, explore toutes les branches les plus prometteuses pour dénicher la meilleure solution très vite. Il ne s'arrête pas à la première solution exacte (sauf si vous le demandez), ce qui lui permet parfois de trouver la combinaison d'opérations la plus courte ou la plus élégante.

C'est un excellent outil, aussi bien pour apprendre (mode manuel) que pour analyser (solveur paramétrable). Si vous voulez que je détaille un point spécifique (comme la génération des plaques en mode compétition, ou le calcul du score), n'hésitez pas !