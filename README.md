# publicHtm
```text
================================================================================
                    LE COMPTE EST BON - Solveur & Jeu
================================================================================

Auteur : J.Dimijian
Version : 1.0
Langage : HTML5 / JavaScript (conversion depuis ABAP avec l'aide de Claude)

================================================================================
                            PRÉSENTATION
================================================================================

Cette application web permet de jouer au "Compte est bon" (célèbre jeu de calcul
mental) ou de laisser un solveur automatique trouver la meilleure solution.
Elle propose à la fois un mode libre, un mode compétition chronométré, ainsi
que de nombreuses options de personnalisation.

L'interface est responsive et fonctionne sur ordinateur comme sur smartphone
(iPhone, Android).

================================================================================
                            MODES DE JEU
================================================================================

1. MODE LIBRE
   - Vous saisissez manuellement une cible et jusqu'à 6 plaques
   - Vous pouvez jouer vous-même en cliquant sur les plaques puis les opérateurs
   - Vous pouvez demander au solveur de trouver la (meilleure) solution

2. MODE COMPÉTITION
   - Une graine aléatoire génère une série de tirages successifs
   - Chaque tirage est chronométré (temps paramétrable)
   - Un système de score récompense la rapidité et la précision
   - Les scores sont différenciés selon que vous trouvez la solution dans les
     temps ou hors temps

================================================================================
                        OPTIONS DISPONIBLES
================================================================================

📊 PARTIE & PLAQUES
   - Modèle de plaques :
        • CEB24 : sélection classique (1,2,3,4,5,6,7,8,9,10,25,50,75,100)
        • CEB28 : sélection étendue (28 plaques spécifiques)
        • Aléatoire complet : plaques totalement aléatoires (hors modèles)
   - Nombre de plaques (variable selon le mode)
   - Bornes min/max pour la cible
   - Option "Cible forcément atteignable" (génération d'un tirage soluble)

⏱ TEMPS & SCORES
   - Temps limite par tirage (en secondes)
   - Score exact / ±1-3 / >3 (dans les temps)
   - Score exact / ±1-3 / >3 (hors temps)
   - Réglages fins des barèmes

🎲 BOUTONS SPÉCIFIQUES
   - "🌸 Sylvie" : Mode simplifié avec cible comprise entre 25 et 100
                 (hommage personnel à la compagne du développeur)
   - "↺ Défaut" : Retour à la configuration classique du jeu

================================================================================
                        FONCTIONNALITÉS DU SOLVEUR
================================================================================

Le solveur automatique propose trois stratégies de résolution :

• MEILLEURE SOLUTION
  Trouve la solution la plus précise possible (compte exact si disponible,
  sinon meilleure approximation). C'est le mode par défaut.

• PREMIÈRE EXACTE
  S'arrête dès qu'une solution exacte est trouvée. Plus rapide, mais ne garantit
  pas la solution la plus courte ou élégante.

• TOUTES (RÉCUR ≤ 3)
  Explore toutes les solutions exactes. Élagage des alternatives triviales
  jusqu'au niveau 3, puis conservation et affichage de toutes les solutions
  alternatives. Idéal pour comprendre la diversité des chemins possibles.

PERFORMANCES :
  - Résolution en moins de 50 ms sur iPhone pour le mode classique (6 plaques)
  - Algorithme optimisé avec élagage agressif :
        • Divisions non entières ignorées
        • Résultats négatifs ou nuls ignorés
        • Commutativité gérée (a+b = b+a testé une seule fois)

================================================================================
                        INTERACTION MANUELLE
================================================================================

Vous pouvez jouer sans le solveur :
  1. Cliquez sur une plaque
  2. Cliquez sur un opérateur (+, -, ×, /)
  3. Cliquez sur une autre plaque
  4. Le résultat s'affiche et devient une nouvelle plaque virtuelle
  5. Recommencez jusqu'à approcher ou atteindre la cible
  6. Cliquez sur "Valider" pour que le programme évalue votre proposition

Le bouton "Résoudre" lance instantanément le solveur selon le mode choisi.
Le bouton "Détail…" affiche le déroulement complet des opérations.

================================================================================
                        STATISTIQUES
================================================================================

L'onglet "Statistiques" permet de suivre vos performances sur la durée :
  - Globales (tous tirages confondus)
  - Par partie (session de compétition)
  - Par mode de jeu (libre / compétition)

Possibilité de réinitialiser les statistiques.

================================================================================
                            RACCOURCIS
================================================================================

Le jeu propose des "Raccourcis" paramétrables pour une prise en main rapide
des fonctionnalités fréquentes (non détaillés ici car dépendants de votre
implémentation finale).

================================================================================
                        EXIGENCES TECHNIQUES
================================================================================

- Navigateur web moderne (Chrome, Firefox, Safari, Edge)
- JavaScript activé
- Aucune connexion Internet requise après chargement initial
- Fonctionne localement (pas de serveur nécessaire)

================================================================================
                    HISTORIQUE ET REMERCIEMENTS
================================================================================

Ce jeu a été initialement développé en ABAP, puis converti en HTML5/JavaScript
avec l'assistance de Claude (IA d'Anthropic). L'application inclut des options
personnalisées (bouton "Sylvie") et une attention particulière à l'expérience
utilisateur.

Merci de jouer et bonne chance pour vos calculs !

================================================================================
                          LICENCE ET CONTACT
================================================================================

Projet libre d'utilisation et de modification.
Pour toute question ou suggestion : [votre contact GitHub]

================================================================================