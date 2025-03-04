## Fiche de révision pour le TP Cryptographie

### 1. **Fonction `dessinsModulo(n, a)`**
```python
def dessinsModulo(n, a):
    cercle = circle((0, 0), 1, color='black')
    graphique = cercle
    points = []
    
    # Placer n points sur le cercle
    for i in range(n):
        angle = 2 * pi * i / n
        x = sin(angle)
        y = cos(angle)
        points.append((x, y))
        graphique += point((x, y), color='red', size=20)
    
    # Tracer les lignes selon la multiplication modulaire
    for i in range(n):
        resultat = (i * a) % n
        graphique += line([points[i], points[resultat]], color='blue')
    
    show(graphique, xmin=-1.2, xmax=1.2, ymin=-1.2, ymax=1.2, aspect_ratio=1)
```

### 2. **Fonction `rot(m, i, alpha)`**
```python
def rot(m, i, alpha):
    message_transforme = ""
    for char in m:
        if char in alpha:
            # Trouver l'index du caractère
            index = alpha.find(char)
            # Calculer le nouvel index après décalage
            nouvel_index = (index + i) % len(alpha)
            # Ajouter le caractère transformé
            message_transforme += alpha[nouvel_index]
        else:
            # Conserver les caractères hors alphabet
            message_transforme += char
    return message_transforme
```

### 3. **Fonction de signature RSA**
```python
def signature_rsa(p, q, message):
    # Calcul de n
    n = p * q
    
    # Calcul de phi(n)
    phi = (p - 1) * (q - 1)
    
    # Choix de e (clé publique)
    e = 11  # Un choix simple qui respecte les contraintes
    
    # Vérification que e est premier avec phi
    assert gcd(e, phi) == 1, "e doit être premier avec phi(n)"
    
    # Calcul de la clé privée d
    d = pow(e, -1, phi)
    
    # Signature
    signature = pow(message, d, n)
    
    # Vérification
    verification = pow(signature, e, n)
    
    return n, e, signature, verification == message
```

### 4. **Exemples d'utilisation**

#### ROT13
```python
alpha13 = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
message = "TEST"
crypte = rot(message, 13, alpha13)
print(crypte)  # Résultat : 'GRFG'
```

#### Signature RSA
```python
p = 22091
q = 95647806479275528135733781266203904794419563064407
M = 19070

n, e, signature, est_valide = signature_rsa(p, q, M)
print("Message original:", M)
print("Signature:", signature)
print("Signature valide:", est_valide)
```

### 5. **Points clés à retenir**
- Modulo : reste de la division
- Décalage cyclique dans ROT
- Conditions sur les clés RSA
- Utiliser `pow()` pour les calculs modulaires
- Vérifier le PGCD
