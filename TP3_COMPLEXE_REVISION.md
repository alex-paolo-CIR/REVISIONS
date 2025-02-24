# Récapitulatif des Fonctions et Concepts du TP sur les Nombres Complexes

## 1. Nombres Complexes dans SageMath
   - **Constantes** : `i` ou `I` représente l’unité imaginaire dans SageMath.
   - **Caractéristiques des Nombres Complexes** :
     - **Partie Réelle** : Utiliser `real_part(z)` pour obtenir la partie réelle d’un nombre complexe \( z \).
     - **Partie Imaginaire** : Utiliser `imag_part(z)` pour obtenir la partie imaginaire.
     - **Module** : `abs(z)` donne la norme ou le module d'un nombre complexe \( z \).
     - **Argument** : `arg(z)` retourne l’argument de \( z \) en radians, soit l’angle avec l’axe des abscisses dans le plan complexe.

## 2. Résolution d’Équations Complexes
   - **Fonction `solve`** : Permet de résoudre des équations complexes. Exemple :
     ```python
     x = var('x')
     solve(x^2 - 1, x)
     ```
     Cette commande résout l'équation \( x^2 - 1 = 0 \).

## 3. Géométrie du Plan Complexe
   - **Points et Affixes** : Les points dans le plan complexe sont représentés par leurs affixes (leurs coordonnées complexes).
   - **Fonction `point`** : Utilisée pour placer un point dans le plan complexe. Exemple :
     ```python
     point((2,3))
     ```
   - **Fonction `text`** : Permet d’ajouter du texte sur le graphe.
   - **Distance et Différence de Points** : Calcul de distances entre points par l’affixe de chacun et interprétation géométrique de ces distances.

## 4. Transformations dans le Plan Complexe
   - **Transformations** : Définir des fonctions qui transforment un point \( z \) dans le plan complexe.
     - **Exemple de Fonctions** :
       - \( f_1(z) = z + i \) : Translation.
       - \( f_2(z) = 3z \) : Homothétie (agrandissement ou réduction).
       - \( f_3(z) = i \cdot z \) : Rotation.
   - **Représentation Graphique** :
     - **Segments** : Utiliser `line` pour tracer des segments reliant des points (ex., segments \( OA \), \( OA_1 \), etc.).
   - **Nature des Transformations** :
     - Identifier si les transformations sont des translations, rotations, homothéties, ou des combinaisons de ces transformations.

## 5. Représentation des Racines n-ièmes de l’Unité
   - **Fonction `racines_n_eme_unite`** : Créer une fonction pour calculer les racines n-ièmes de l’unité (c’est-à-dire, les solutions de \( z^n = 1 \) dans le plan complexe).
   - **Polygone Régulier** : La fonction `polygone_n` dessine un polygone régulier de \( n \) côtés, en reliant les racines n-ièmes de l’unité dans le plan complexe.

## Récapitulatif des Exercices
   - **Exercice 1** : Calculer les parties réelle et imaginaire, module et argument d’une suite de nombres complexes \( z_0, z_1, \ldots, z_{10} \) avec une boucle.
   - **Exercice 2** : Résoudre des équations complexes spécifiques.
   - **Exercice 3** : Placer des points dans le plan complexe, calculer des différences de points et interpréter géométriquement ces résultats.
   - **Exercice 4** : Définir et appliquer des transformations du plan complexe, et représenter les images graphiquement.
   - **Exercice 5** : Définir et dessiner des racines de l’unité et des polygones réguliers associés.
