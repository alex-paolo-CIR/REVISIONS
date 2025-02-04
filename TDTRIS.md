```c
#ifndef TRI_H
#define TRI_H

#include <stdio.h>      // Pour les fonctions d'entrée/sortie standard (printf, fprintf)
#include <stdlib.h>     // Pour les fonctions d'allocation de mémoire (malloc, free, rand)
#include <stdbool.h>    // Pour le type booléen (true, false)
#include <time.h>       // Pour la fonction time (utilisée pour initialiser le générateur de nombres aléatoires)
#include <math.h>       // Pour la fonction log2 (utilisée dans le tri insertion dichotomique)

// Fonction pour échanger deux entiers (swap)
void swap(int* a, int* b) {
    int temp = *a;  // Stocke temporairement la valeur pointée par a
    *a = *b;        // Remplace la valeur pointée par a par la valeur pointée par b
    *b = temp;      // Remplace la valeur pointée par b par la valeur temporaire (ancienne valeur de a)
}

// Fonction pour initialiser un tableau avec des valeurs aléatoires
int initRandTab(int* tab, int tabsize) {
    if (tab == NULL || tabsize <= 0) return -1; // Vérifie si le tableau est valide et la taille positive, sinon retourne une erreur
    srand(time(NULL)); // Initialise le générateur de nombres aléatoires avec une seed basée sur le temps courant
    for (int i = 0; i < tabsize; i++) { // Boucle à travers chaque élément du tableau
        tab[i] = rand() % 1000; // Assigne à chaque élément une valeur aléatoire entre 0 et 999
    }
    return 0; // Retourne 0 pour indiquer le succès
}

// Fonction pour afficher une partie d'un tableau
void displayPartTab(int* tab, int tabsize, int begin, int end) {
    if (tab == NULL || tabsize <= 0 || begin < 0 || end >= tabsize || begin > end) return; // Vérifie les paramètres
    printf("["); // Affiche le crochet ouvrant
    for (int i = begin; i <= end; i++) { // Boucle de l'indice de début à l'indice de fin
        printf("%d", tab[i]); // Affiche la valeur de l'élément courant
        if (i < end) { // Si ce n'est pas le dernier élément
            printf(", "); // Affiche une virgule et un espace
        }
    }
    printf("]\n"); // Affiche le crochet fermant et un retour à la ligne
}

// Fonction pour afficher tout le tableau
void dispTabInt(int* tab, int tabsize) {
    displayPartTab(tab, tabsize, 0, tabsize - 1); // Appelle displayPartTab pour afficher tout le tableau
}

// Tri Naïf (Très lent, à des fins pédagogiques)
int triNaif(int* tab, int tabsize) {
    if (tab == NULL || tabsize <= 0) return -1; // Vérifie si le tableau est valide
    int comparisons = 0, permutations = 0; // Initialise les compteurs de comparaisons et permutations
    for (int i = 0; i < tabsize; i++) { // Boucle à travers chaque élément du tableau
        for (int j = 0; j < tabsize; j++) { // Boucle à travers chaque élément du tableau (comparaison avec tous les autres)
            comparisons++; // Incrémente le compteur de comparaisons
            if (tab[i] < tab[j]) { // Si l'élément à l'indice i est plus petit que l'élément à l'indice j
                permutations++; // Incrémente le compteur de permutations
                swap(&tab[i], &tab[j]); // Échange les deux éléments
            }
        }
    }
    printf("Tri Naif: n=%d, comparaisons=%d, permutations=%d\n", tabsize, comparisons, permutations); // Affiche les statistiques
    return 0; // Retourne 0 pour indiquer le succès
}

// Tri à Bulle
int triBulle(int* tab, int tabsize) {
    if (tab == NULL || tabsize <= 0) return -1; // Vérifie si le tableau est valide
    int comparisons = 0, permutations = 0; // Initialise les compteurs de comparaisons et permutations
    for (int i = 0; i < tabsize - 1; i++) { // Boucle à travers le tableau (mais pas jusqu'au dernier élément)
        for (int j = 0; j < tabsize - i - 1; j++) { // Boucle à travers la partie non triée du tableau
            comparisons++; // Incrémente le compteur de comparaisons
            if (tab[j] > tab[j + 1]) { // Si l'élément courant est plus grand que l'élément suivant
                permutations++; // Incrémente le compteur de permutations
                swap(&tab[j], &tab[j + 1]); // Échange les deux éléments
            }
        }
    }
    printf("Tri Bulle: n=%d, comparaisons=%d, permutations=%d\n", tabsize, comparisons, permutations); // Affiche les statistiques
    return 0; // Retourne 0 pour indiquer le succès
}

// Tri à Bulle Optimisé
int triBulleOpt(int* tab, int tabsize) {
    if (tab == NULL || tabsize <= 0) return -1; // Vérifie si le tableau est valide
    int comparisons = 0, permutations = 0; // Initialise les compteurs de comparaisons et permutations
    bool swapped; // Variable pour suivre si des échanges ont eu lieu
    for (int i = 0; i < tabsize - 1; i++) { // Boucle à travers le tableau (mais pas jusqu'au dernier élément)
        swapped = false; // Réinitialise le drapeau d'échange pour cette passe
        for (int j = 0; j < tabsize - i - 1; j++) { // Boucle à travers la partie non triée du tableau
            comparisons++; // Incrémente le compteur de comparaisons
            if (tab[j] > tab[j + 1]) { // Si l'élément courant est plus grand que l'élément suivant
                permutations++; // Incrémente le compteur de permutations
                swap(&tab[j], &tab[j + 1]); // Échange les deux éléments
                swapped = true; // Met le drapeau à vrai car un échange a eu lieu
            }
        }
        if (swapped == false) break; // Si aucun échange n'a eu lieu, le tableau est trié, donc on sort de la boucle
    }
    printf("Tri Bulle Optimisé: n=%d, comparaisons=%d, permutations=%d\n", tabsize, comparisons, permutations); // Affiche les statistiques
    return 0; // Retourne 0 pour indiquer le succès
}

// Tri par Sélection Ordinaire
int TriSelection(int* tab, int tabsize) {
    if (tab == NULL || tabsize <= 0) return -1; // Vérifie si le tableau est valide
    int comparisons = 0, permutations = 0; // Initialise les compteurs de comparaisons et permutations
    for (int i = 0; i < tabsize - 1; i++) { // Boucle à travers le tableau (mais pas jusqu'au dernier élément)
        int min_index = i; // Suppose que l'élément courant est le minimum
        for (int j = i + 1; j < tabsize; j++) { // Boucle à travers le reste du tableau
            comparisons++; // Incrémente le compteur de comparaisons
            if (tab[j] < tab[min_index]) { // Si un élément plus petit est trouvé
                min_index = j; // Met à jour l'indice du minimum
            }
        }
        if (min_index != i) { // Si un minimum plus petit a été trouvé
            permutations++; // Incrémente le compteur de permutations
            swap(&tab[i], &tab[min_index]); // Échange l'élément courant avec le minimum trouvé
        }
    }
    printf("Tri Selection: n=%d, comparaisons=%d, permutations=%d\n", tabsize, comparisons, permutations); // Affiche les statistiques
    return 0; // Retourne 0 pour indiquer le succès
}

// Tri par Insertion Séquentielle
int TriInsertionSequentiel(int* tab, int tabsize) {
    if (tab == NULL || tabsize <= 0) return -1; // Vérifie si le tableau est valide
    int comparisons = 0, permutations = 0; // Initialise les compteurs de comparaisons et permutations
    for (int i = 1; i < tabsize; i++) { // Boucle à travers le tableau, en commençant au deuxième élément
        int key = tab[i]; // Stocke l'élément courant (à insérer)
        int j = i - 1; // Initialise l'indice pour parcourir la partie triée du tableau

        while (j >= 0 && tab[j] > key) { // Tant qu'on n'a pas atteint le début du tableau et que l'élément à la position j est plus grand que la clé
            comparisons++; // Incrémente le compteur de comparaisons
            permutations++; // Incrémente le compteur de permutations
            tab[j + 1] = tab[j]; // Décale l'élément à la position j vers la droite
            j = j - 1; // Décrémente j pour continuer à parcourir la partie triée
        }
        tab[j + 1] = key; // Insère la clé à la bonne position
    }
    printf("Tri Insertion Sequentiel: n=%d, comparaisons=%d, permutations=%d\n", tabsize, comparisons, permutations); // Affiche les statistiques
    return 0; // Retourne 0 pour indiquer le succès
}

// Recherche dichotomique pour trouver la position d'insertion
int rang(int* tab, int indmin, int indmax, int valeur) {
    int milieu; // Variable pour stocker l'indice du milieu
    while (indmin <= indmax) { // Tant que l'indice minimum est inférieur ou égal à l'indice maximum
        milieu = indmin + (indmax - indmin) / 2; // Calcule l'indice du milieu (évite le dépassement d'entier)
        if (tab[milieu] == valeur) return milieu; // Si l'élément au milieu est égal à la valeur recherchée, retourne l'indice du milieu
        else if (tab[milieu] < valeur) indmin = milieu + 1; // Si l'élément au milieu est plus petit que la valeur recherchée, met à jour l'indice minimum
        else indmax = milieu - 1; // Si l'élément au milieu est plus grand que la valeur recherchée, met à jour l'indice maximum
    }
    return indmin;  // Retourne la position d'insertion (si la valeur n'est pas trouvée)
}

// Tri par Insertion Dichotomique
int TriInsertionDichotomique(int* tab, int tabsize) {
    if (tab == NULL || tabsize <= 0) return -1; // Vérifie si le tableau est valide
    int comparisons = 0, permutations = 0; // Initialise les compteurs de comparaisons et permutations
    for (int i = 1; i < tabsize; i++) { // Boucle à travers le tableau, en commençant au deuxième élément
        int key = tab[i]; // Stocke l'élément courant (à insérer)
        int insert_pos = rang(tab, 0, i - 1, key); // Trouve la position d'insertion en utilisant la recherche dichotomique
        comparisons += (i > 1) ? (int)(log2(i) + 1) : 1; // Approximation du nombre de comparaisons pour la recherche dichotomique
        for (int j = i; j > insert_pos; j--) { // Décale les éléments pour faire de la place pour l'insertion
            permutations++; // Incrémente le compteur de permutations
            tab[j] = tab[j - 1]; // Décale l'élément à la position j vers la droite
        }
        tab[insert_pos] = key; // Insère l'élément à la bonne position
    }
    printf("Tri Insertion Dichotomique: n=%d, comparaisons=%d, permutations=%d\n", tabsize, comparisons, permutations); // Affiche les statistiques
    return 0; // Retourne 0 pour indiquer le succès
}

#endif // TRI_H
```
