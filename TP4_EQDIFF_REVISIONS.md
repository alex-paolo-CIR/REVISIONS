### **Fiche de Révision : SageMath Équations Différentielles**

---

#### **1. Commandes essentielles de SageMath**

1. **Déclarer une variable :**  
   ```python
   var('x')  # Déclare x comme une variable
   ```

2. **Déclarer une fonction inconnue :**  
   ```python
   y = function('y')(x)  # Déclare y comme fonction de x
   ```

3. **Parties réelle et imaginaire d’un nombre complexe :**  
   ```python
   real(z)  # Partie réelle de z
   imag(z)  # Partie imaginaire de z
   ```

4. **Module d’un nombre complexe :**  
   ```python
   abs(z)  # Calcule le module de z
   ```

5. **Distance entre deux points :**  
   Si \( A(x_1, y_1) \) et \( B(x_2, y_2) \) :  
   ```python
   sqrt((x2 - x1)^2 + (y2 - y1)^2)
   ```

---

#### **2. Résolution d'Équations Différentielles**

1. **Résolution symbolique :**  
   Pour résoudre \( y'(x) + y(x) = e^{-x} \) :  
   ```python
   desolve(diff(y, x) + y == exp(-x), y)
   ```

2. **Ajouter une condition initiale :**  
   Pour résoudre avec \( y(0) = 1 \) :  
   ```python
   desolve(diff(y, x) + y == exp(-x), y, ics=[0, 1])
   ```

3. **Vérifier une solution :**  
   Pour vérifier que \( y(x) = Ce^{2x} + \frac{x^2}{2} \) satisfait \( y'(x) - 2y(x) = x \) :  
   ```python
   eq = diff(y, x) - 2 * y - x
   simplify(eq)  # Doit donner 0 si correct
   ```

---

#### **3. Tracer une solution**

1. **Résolution numérique et tracé :**  
   Pour résoudre \( y'(x) + 2y(x) = \cos(x) \) avec \( y(0) = 1 \) :  
   ```python
   sol = desolve(diff(y, x) + 2 * y == cos(x), y, ics=[0, 1])
   plot(sol, (x, 0, 5))  # Tracer sur [0, 5]
   ```

---

#### **4. Concepts clés**

1. **Solution générale :**  
   Contient une constante \( C \), correspondant à toutes les solutions possibles.

2. **Solution particulière :**  
   Obtenue en ajoutant une condition initiale (ex. \( y(0) = 1 \)).

3. **Structure d'une équation différentielle :**  
   Exemple : \( y'(x) + py(x) = q(x) \), où :  
   - \( p(x) \) et \( q(x) \) sont des fonctions données.  
   - \( y(x) \) est la fonction à trouver.  
