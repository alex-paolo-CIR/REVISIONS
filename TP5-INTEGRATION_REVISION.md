## Fiche de révision pour le TP 5 - Intégration

### 1. **Concepts clés** 
- **Primitives** :
  - Calcul avec SageMath : `integrate(f, x)` renvoie une primitive de \( f(x) \).
  - L'ensemble des primitives inclut une constante \( C \).
  - Les primitives impliquent parfois le logarithme népérien \( \log(x) \) (noté \( \ln(x) \) en mathématiques).
- **Intégrale définie** :
  - Syntaxe : `integral(f, x, a, b)` pour calculer \( \int_a^b f(x) \, \mathrm{d}x \).
  - Approximation numérique : `N(integral(f, x, a, b))`.

---

### 2. **Exercices**
#### **Exercice 1 : Primitives**
- Utiliser `integrate` pour vérifier des primitives, ex. : 
  - \( \int \tan(t) \, \mathrm{d}t = -\ln(\cos(t)) \).
  - Vérification : `bool`.

#### **Exercice 2 : Calcul et graphes**
- Calcul exact de \( \int_0^1 \sqrt{1-x^2} \, \mathrm{d}x \) : \( \frac{\pi}{4} \).
- Graphe de l'intégrande avec `plot(aspect_ratio=1)`.

---

### 3. **Rappels Python**
- **Boucles** :
  - `for` et `while` pour itérer.
  - Création de listes : `[0 for j in range(n)]`.
- **Définir une fonction** :
  - Exemple : \( f(x) = x^2 \) si \( x \geq 0 \), sinon \( f(x) = 0 \).
  ```python
  def f(x):
      return x^2 if x >= 0 else 0
  ```

---

### 4. **Intégration numérique**
- **Méthodes simples** :
  - Rectangle : \( \tilde{I} = (b-a)f(a) \) ou \( (b-a)f\big(\frac{a+b}{2}\big) \).
  - Trapèze : \( \tilde{I} = (b-a)\frac{f(a)+f(b)}{2} \).
  - Simpson : \( \tilde{I} = \frac{b-a}{6}\big[f(a)+4f\big(\frac{a+b}{2}\big)+f(b)\big] \).
- **Méthodes composites** :
  - Découper \( [a, b] \) en \( n \) intervalles.
  - Exemples :
    - **Trapèzes** : \(\tilde{I} = \frac{b-a}{n}\big(\frac{f(a)+f(b)}{2} + \sum_{i=1}^{n-1} f(x_i)\big)\).

---

### 5. **Applications et exercices**
- Calculer \(\int_0^{5/2} f(x) \, \mathrm{d}x \) avec :
  - Rectangles : `h * sum(f[:-1])`.
  - Trapèzes : \((h/2) \times (f[0] + 2 \cdot \text{sum}(f[1:-1]) + f[-1])\).
- Représentation graphique des rectangles/trapèzes avec `Graphics` et `line`.

---

### 6. **Programmation avec Sage**
- Fonction `trapezes(f, a, b, n)` :
  - Calcul numérique par trapèzes.
  - Visualisation si \( n < 15 \).
  
--- 
