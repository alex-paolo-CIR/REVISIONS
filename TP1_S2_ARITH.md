# Fiche de Révision - Arithmétique dans Z

## I. Division Euclidienne

*   **Définition :** Pour  `a ∈ ℤ` et `b ∈ ℕ*`, il existe `q ∈ ℤ` et `r ∈ ℕ` tels que :
    ```
    a = bq + r  avec  0 ≤ r < b
    ```
*   **Python :**
    *   `a // b` : Quotient
    *   `a % b` : Reste

*   **Exemple :** `14 // 3` donne `4`, et `14 % 3` donne `2`, car `14 = 3 * 4 + 2`.

## II. Écriture Décimale des Nombres

*   **Définition :**  `N = a_n * 10^n + a_{n-1} * 10^{n-1} + ... + a_1 * 10 + a_0`
*   **Listes Python :**
    *   `tab = [a, b, c, ...]`
    *   `tab[i]` : Accès à l'élément
    *   `len(tab)` : Longueur
    *   `for i in range(len(tab)): ...` : Parcours
    *   `tab.append(x)` : Ajout d'un élément
*   **Fonctions (Exemples) :**
    ```python
    def liste_vers_entier(liste_chiffres):
        N = 0
        for chiffre in liste_chiffres:
            N = N * 10 + chiffre
        return N

    def entier_vers_liste(N):
        chiffres = []
        while N > 0:
            chiffres.insert(0, N % 10)
            N //= 10
        return chiffres
    ```

## III. Algorithme d'Euclide

*   **Principe :** `pgcd(a, b) = pgcd(b, r)` et `pgcd(c, 0) = c`
*   **Fonction Récursive :**

    ```python
    def pgcd(a, b):
        if b == 0:
            return a
        return pgcd(b, a % b)
    ```
*   **Vérification :**
    ```python
    from math import gcd
    gcd(a, b)
    ```
*   **Simplification de Fractions :** Diviser numérateur et dénominateur par leur PGCD.

## IV. Nombres Parfaits

*   **Définition :** Somme des diviseurs propres = Nombre
*   **Fonction (Exemple) :**
    ```python
    def est_parfait(n):
        if n <= 1:
            return False
        somme_diviseurs = 1
        for i in range(2, int(n**0.5) + 1):
            if n % i == 0:
                somme_diviseurs += i + n // i
        return somme_diviseurs == n
    ```

## Points Clés

*   Division Euclidienne :  `//` et `%`
*   Listes Python
*   PGCD (algorithme récursif)
*   Définition nombres parfaits
