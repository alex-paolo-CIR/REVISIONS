### **Fiche de Révision : TP 4 - Équations Différentielles avec SageMath**

---

#### **1. Commandes essentielles de SageMath**

1. **Déclarer une variable et une fonction :**  
   - Déclaration de variables :  
     ```python
     var('x')  # Déclare x comme variable
     ```
   - Déclaration d'une fonction inconnue :  
     ```python
     y = function('y')(x)  # Déclare y comme fonction de x
     ```

2. **Résolution symbolique d'une équation différentielle :**  
   - Exemple pour résoudre \( y'(x) + y(x) = e^{-x} \) :  
     ```python
     desolve(diff(y, x) + y == exp(-x), y)
     ```

3. **Ajouter des conditions initiales :**  
   - Pour résoudre avec \( y(0) = 1 \) :  
     ```python
     desolve(diff(y, x) + y == exp(-x), y, ics=[0, 1])
     ```

4. **Tracé des solutions :**  
   - Pour tracer la solution \( y(x) \) sur un intervalle donné :  
     ```python
     plot(solution, (x, a, b))  # Intervalle [a, b]
     ```

5. **Champ de pentes :**  
   - Exemple pour l'équation \( y' = f(x, y) \) :  
     ```python
     plot_slope_field(f(x, y), (x, x_min, x_max), (y, y_min, y_max))
     ```

6. **Vérification d'une solution :**  
   - Pour vérifier que \( y(x) \) satisfait l'équation différentielle :  
     ```python
     eq = diff(y, x) + y - exp(-x)  # Équation différentielle
     eq.substitute_function(y, solution).simplify()  # Doit donner 0
     ```

---

#### **2. Analyse des équations différentielles**

1. **Ordre et type :**  
   Identifier l'ordre et le type de l'équation (exemple : linéaire, homogène, etc.).

2. **Interprétation des solutions :**  
   - Solution générale : contient une constante \( C \).  
   - Solution particulière : obtenue en appliquant des conditions initiales.  

---

#### **3. Applications et Résolutions**

1. **Exemple 1 : Résolution d'ordre 1**  
   Équation : \( y'(x) + y(x) = e^{-x} \).  
   - Solution générale :  
     ```python
     desolve(diff(y, x) + y == exp(-x), y)
     ```
   - Avec \( y(0) = 1 \) :  
     ```python
     desolve(diff(y, x) + y == exp(-x), y, ics=[0, 1])
     ```

2. **Exemple 2 : Résolution d'ordre 2**  
   Équation : \( y''(x) + 2y'(x) + y(x) = x + 1 \) avec \( y(0) = 1, y'(0) = 2 \).  
   - Résolution :  
     ```python
     desolve(diff(y, x, 2) + 2 * diff(y, x) + y == x + 1, y, ics=[0, 1, 2])
     ```

3. **Exemple 3 : Mouvement amorti**  
   Équation : \( x''(t) + fx'(t) + x(t) = 0 \) avec \( f = 0, 1, 2 \), \( x(0) = 1 \), \( x'(0) = 0 \).  
   - Pour \( f = 0 \) :  
     ```python
     solution = cos(t)
     plot(solution, (t, -1, 10))
     ```

4. **Champ de pentes et courbes intégrales**  
   - Tracer le champ de pentes pour \( y' = y + 3x + 4 \) :  
     ```python
     plot_slope_field(y + 3*x + 4, (x, -1, 1), (y, -3, 5))
     ```
   - Ajouter la courbe intégrale :  
     ```python
     plot(sol, (x, -1, 1)) + plot_slope_field(...)
     ```

---

#### **4. Questions fréquentes**

1. **Comment déclarer plusieurs variables simultanément ?**  
   ```python
   var('x y z')  # Déclare x, y, z comme variables
   ```

2. **Comment intégrer numériquement une équation différentielle ?**  
   Utiliser la commande `numerical_integral`.  

3. **Quelle commande pour différencier plusieurs fois ?**  
   ```python
   diff(y, x, n)  # Différencie y n fois par rapport à x
   ```

4. **Comment représenter plusieurs solutions sur un même graphe ?**  
   ```python
   p1 = plot(sol1, (x, -1, 1))
   p2 = plot(sol2, (x, -1, 1))
   p1 + p2
   ```

---

Cette fiche couvre toutes les commandes clés et méthodes liées aux équations différentielles abordées dans le TP. Souhaites-tu ajouter des cas spécifiques ou des exemples plus détaillés ? 😊
