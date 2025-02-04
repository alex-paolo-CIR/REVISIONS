Parfait, voici une fiche de révision plus détaillée, tout en restant concise et organisée :

Fiche de Révision - Arithmétique dans Z (Détaillée)
I. Division Euclidienne

Définition : Pour 
𝑎
∈
𝑍
a∈Z
 (dividende) et 
𝑏
∈
𝑁
∗
b∈N
∗
 (diviseur), il existe un unique quotient 
𝑞
∈
𝑍
q∈Z
 et un unique reste 
𝑟
∈
𝑁
r∈N
 tels que :

𝑎
=
𝑏
𝑞
+
𝑟
avec
0
≤
𝑟
<
𝑏
a=bq+ravec0≤r<b

Python :

a // b : Quotient de la division euclidienne de a par b (division entière).

a % b : Reste de la division euclidienne de a par b (modulo).

Exemple : 14 // 3 donne 4, et 14 % 3 donne 2, car 
14
=
3
×
4
+
2
14=3×4+2
.

Applications : Conversion d'unités (minutes en heures et minutes), algorithmes de cryptographie.

II. Écriture Décimale des Nombres

Définition : Tout entier naturel 
𝑁
N
 peut être exprimé en base 10 sous la forme :

𝑁
=
𝑎
𝑛
⋅
1
0
𝑛
+
𝑎
𝑛
−
1
⋅
1
0
𝑛
−
1
+
⋯
+
𝑎
1
⋅
1
0
1
+
𝑎
0
⋅
1
0
0
N=a
n
	​

⋅10
n
+a
n−1
	​

⋅10
n−1
+⋯+a
1
	​

⋅10
1
+a
0
	​

⋅10
0

où 
𝑎
𝑖
a
i
	​

 sont les chiffres de 
𝑁
N
 en base 10 ( 
0
≤
𝑎
𝑖
≤
9
0≤a
i
	​

≤9
).

Listes en Python :

tab = [a, b, c, ...] : Création d'une liste. Les éléments peuvent être de différents types.

tab[i] : Accès à l'élément d'indice i (attention, l'indexation commence à 0).

len(tab) : Retourne le nombre d'éléments dans la liste.

for i in range(len(tab)): ... : Boucle pour parcourir les indices de la liste.

tab.append(x) : Ajoute l'élément x à la fin de la liste.

tab = tab + [x] : Concatène x (dans une liste) à la fin de tab.

Fonctions :

Conversion Liste Chiffres -> Entier :

def liste_vers_entier(liste_chiffres):
    N = 0
    for chiffre in liste_chiffres:
        N = N * 10 + chiffre
    return N
content_copy
download
Use code with caution.
Python

Conversion Entier -> Liste Chiffres :

def entier_vers_liste(N):
    chiffres = []
    while N > 0:
        chiffres.insert(0, N % 10)  # Ajoute en tête
        N //= 10
    return chiffres
content_copy
download
Use code with caution.
Python
III. Algorithme d'Euclide

Principe : Le PGCD de deux nombres ne change pas si le plus grand est remplacé par sa différence avec le plus petit. On utilise le reste pour une convergence plus rapide. Si 
𝑎
=
𝑏
𝑞
+
𝑟
a=bq+r
, alors 
pgcd
(
𝑎
,
𝑏
)
=
pgcd
(
𝑏
,
𝑟
)
pgcd(a,b)=pgcd(b,r)
. L'algorithme s'arrête quand le reste est nul: 
pgcd
(
𝑐
,
0
)
=
𝑐
pgcd(c,0)=c
.

Fonction Récursive (Python) :

def pgcd(a, b):
    if b == 0:
        return a
    return pgcd(b, a % b)
content_copy
download
Use code with caution.
Python

Vérification : Utiliser la fonction gcd du module math :

from math import gcd
print(gcd(a, b))
content_copy
download
Use code with caution.
Python

Simplification de Fractions : Diviser le numérateur et le dénominateur par leur PGCD.

IV. Nombres Parfaits

Définition : Un entier positif est dit parfait s'il est égal à la somme de ses diviseurs propres (diviseurs positifs, excluant le nombre lui-même).

Exemples : 6 (1 + 2 + 3 = 6), 28 (1 + 2 + 4 + 7 + 14 = 28).

Fonction (Python) :

def est_parfait(n):
    if n <= 1: # 1 n'est pas considéré comme parfait
        return False
    somme_diviseurs = 1  # 1 est toujours un diviseur
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            somme_diviseurs += i + n // i  # Ajouter i et son quotient
    return somme_diviseurs == n
content_copy
download
Use code with caution.
Python

Remarques : La recherche de diviseurs peut être optimisée en ne testant que jusqu'à la racine carrée de n.

Points Clés à Maîtriser

Division Euclidienne : Calcul du quotient et du reste, applications.

Listes Python : Création, accès, modification, parcours.

Algorithme d'Euclide : Fonctionnement, implémentation récursive, lien avec la simplification de fractions.

Nombres Parfaits : Définition précise, fonction de vérification.

Optimisation : Savoir optimiser la recherche des diviseurs.
