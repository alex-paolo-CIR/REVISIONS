# Fiche de Révision : Dynamique du Point Matériel

## 1. Introduction à la Dynamique
- **Définition** : La dynamique étudie la relation entre les forces appliquées à un corps et les changements de mouvement qui en résultent.
- **Objectif** : Prédire le mouvement d'un corps dans un milieu donné en analysant les forces qui agissent sur lui.

---

## 2. Les Lois de Newton

### 2.1. Première Loi de Newton (Principe d’Inertie)
- **Énoncé** : Un système soumis à des forces extérieures dont la somme vectorielle est nulle est appelé **système pseudo-isolé** (ou isolé si aucune force n’agit sur lui).
  - Si `\sum \vec{F}_{ext} = \vec{0}`, alors le centre d’inertie du système est soit au repos, soit en mouvement rectiligne uniforme dans un référentiel galiléen.
- **Référentiel Galiléen** : Un référentiel dans lequel le principe d’inertie est vérifié. Tout référentiel en translation rectiligne uniforme par rapport à un référentiel galiléen est également galiléen.
  - **Exemple** : Si un objet est en équilibre (`\sum \vec{F}_{ext} = \vec{0}`), alors `\vec{T} + \vec{F}_g = \vec{0}` (tension égale au poids).

### 2.2. Deuxième Loi de Newton (Principe Fondamental de la Dynamique - PFD)
- **Énoncé** : La somme des forces extérieures appliquées à un point matériel est égale au produit de sa masse et de son accélération.
  ```math
  \sum \vec{F}_{ext} = m \vec{a}
  ```
- **Forces** :
  - **Forces à distance** : Interaction gravitationnelle, force électrostatique, force magnétique.
  - **Forces de contact** : Frottement, tension, réaction normale.

### 2.3. Troisième Loi de Newton (Principe de l’Action et de la Réaction)
- **Énoncé** : Si un objet A exerce une force `\vec{F}_{A \rightarrow B}` sur un objet B, alors B exerce une force `\vec{F}_{B \rightarrow A}` de même intensité mais de sens opposé sur A.
  ```math
  \vec{F}_{A \rightarrow B} = -\vec{F}_{B \rightarrow A}
  ```

---

## 3. Les Forces

### 3.1. Forces à Distance
- **Gravitation** : Deux corps de masses `m_A` et `m_B` s'attirent mutuellement avec une force proportionnelle à leurs masses et inversement proportionnelle au carré de la distance `d` qui les sépare.
  ```math
  F_{A/B} = F_{B/A} = G \frac{m_A m_B}{d^2}
  ```
  où `G = 6,67 \times 10^{-11} \, \text{Nm}^2/\text{kg}^2` est la constante de gravitation universelle.
- **Force Électrostatique (Coulomb)** : Deux charges `q_1` et `q_2` exercent une force attractive ou répulsive selon le signe des charges.
  ```math
  F = k \frac{q_1 q_2}{d^2}
  ```
  où `k = 9 \times 10^9 \, \text{Nm}^2/\text{C}^2`.
- **Force Magnétique (Lorentz)** : Une charge `q` en mouvement dans un champ magnétique `\vec{B}` subit une force :
  ```math
  \vec{f}_m = q \vec{v} \wedge \vec{B}
  ```

### 3.2. Forces de Contact
- **Réaction Normale (`\vec{N}`)** : Force perpendiculaire à la surface de contact.
- **Tension (`\vec{T}`)** : Force exercée par un fil ou une corde.
- **Frottement** :
  - **Frottement Statique** : Force qui s'oppose au mouvement d'un objet immobile.
    ```math
    f_{s \text{max}} = \mu_s N
    ```
  - **Frottement Cinétique** : Force qui s'oppose au mouvement d'un objet en déplacement.
    ```math
    f_c = \mu_c N
    ```
    où `\mu_s` et `\mu_c` sont les coefficients de frottement statique et cinétique.

### 3.3. Forces de Frottement dans un Fluide
- **Frottements Linéaires** : Proportionnels à la vitesse (`f = -k v`).
- **Frottements Quadratiques** : Proportionnels au carré de la vitesse (`f = -k' v^2`).

---

## 4. Application de la Relation Fondamentale de la Dynamique (RFD)

### 4.1. Chute Libre
- **Définition** : Mouvement d'un objet soumis uniquement à son poids (pas de frottement).
- **Équations** :
  - Accélération : `a = g`.
  - Vitesse : `v = g t`.
  - Position : `z = \frac{1}{2} g t^2`.

### 4.2. Mouvement Parabolique
- **Équations** :
  - Horizontal : `x = v_0 \cos(\theta) t`.
  - Vertical : `z = v_0 \sin(\theta) t - \frac{1}{2} g t^2`.

---

## 5. Quantité de Mouvement

### 5.1. Définition
- La quantité de mouvement `\vec{p}` d'un point matériel de masse `m` et de vitesse `\vec{v}` est :
  ```math
  \vec{p} = m \vec{v}
  ```
- Pour un système de `N` points matériels :
  ```math
  \vec{p} = \sum_i m_i \vec{v}_i
  ```

### 5.2. Conservation de la Quantité de Mouvement
- Dans un système isolé (aucune force extérieure), la quantité de mouvement totale est conservée :
  ```math
  \frac{d\vec{p}}{dt} = 0
  ```

---

## 6. Collisions

### 6.1. Types de Collisions
- **Collision Élastique** : Conservation de la quantité de mouvement et de l'énergie cinétique.
- **Collision Inélastique** : Conservation de la quantité de mouvement, mais perte d'énergie cinétique.
- **Collision Parfaitement Inélastique** : Les deux corps restent liés après la collision.

### 6.2. Exemple de Collision Inélastique
- **Avant la collision** : `\vec{p} = m_1 \vec{v}_1`.
- **Après la collision** : `\vec{p}' = (m_1 + m_2) \vec{v}'`.
- **Vitesse après collision** :
  ```math
  v' = \frac{m_1 v_1}{m_1 + m_2}
  ```

---

## 7. Pendule Simple
- **Équations du mouvement** :
  ```math
  \ddot{\theta} + \frac{g}{l} \sin(\theta) = 0
  ```
- **Tension dans le fil** :
  ```math
  T = mg (3 \cos(\theta) - 2 \cos(\theta_0))
  ```

---

## 8. Exercices d'Application

### 8.1. Chute Libre
- Un objet est lâché sans vitesse initiale. Calculer sa vitesse après une chute de hauteur `h`.
  ```math
  v = \sqrt{2 g h}
  ```

### 8.2. Collision Inélastique
- Un chariot de 5 kg à 2 m/s entre en collision avec un chariot de 7 kg au repos. Calculer la vitesse après collision.
  ```math
  v' = \frac{5 \times 2}{5 + 7} = 0,83 \, \text{m/s}
  ```

---

## 9. Résumé des Formules Clés
- **PFD** : `\sum \vec{F}_{ext} = m \vec{a}`.
- **Quantité de mouvement** : `\vec{p} = m \vec{v}`.
- **Frottement statique** : `f_{s \text{max}} = \mu_s N`.
- **Frottement cinétique** : `f_c = \mu_c N`.
- **Chute libre** : `v = g t`, `z = \frac{1}{2} g t^2`.
