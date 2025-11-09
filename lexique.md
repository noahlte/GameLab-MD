# Lexique Lua - Français

Ce lexique regroupe tous les mots-clés, termes techniques et concepts importants en Lua avec leur traduction et définition.

---

## Mots-clés de base

### **local**
- **Traduction :** Local
- **Définition :** Déclare une variable qui n'existe que dans une partie limitée du code (bonne pratique)
- **Exemple :** `local nom = "Alice"`

### **print**
- **Traduction :** Imprimer / Afficher
- **Définition :** Fonction qui affiche du texte dans le terminal
- **Exemple :** `print("Hello World")`

---

## Types de données

### **string**
- **Traduction :** Chaîne de caractères
- **Définition :** Type de donnée représentant du texte entre guillemets
- **Exemple :** `local message = "Bonjour"`

### **number**
- **Traduction :** Nombre
- **Définition :** Type de donnée représentant un nombre (entier ou décimal)
- **Exemple :** `local age = 15` ou `local poids = 52.5`

### **boolean**
- **Traduction :** Booléen
- **Définition :** Type de donnée qui peut être soit `true` (vrai) soit `false` (faux)
- **Exemple :** `local vivant = true`

### **nil**
- **Traduction :** Néant / Vide / Rien
- **Définition :** Représente l'absence de valeur
- **Exemple :** `local inventaire = nil`

### **table**
- **Traduction :** Tableau
- **Définition :** Structure de données qui permet de stocker plusieurs valeurs dans une seule variable
- **Exemple :** `local scores = {100, 200, 150}`

---

## Opérateurs mathématiques

### **+** (addition)
- **Traduction :** Plus
- **Définition :** Additionne deux nombres
- **Exemple :** `10 + 5` → 15

### **-** (subtraction)
- **Traduction :** Moins
- **Définition :** Soustrait deux nombres
- **Exemple :** `10 - 5` → 5

### **\*** (multiplication)
- **Traduction :** Multiplié par
- **Définition :** Multiplie deux nombres
- **Exemple :** `10 * 5` → 50

### **/** (division)
- **Traduction :** Divisé par
- **Définition :** Divise deux nombres
- **Exemple :** `10 / 5` → 2

### **%** (modulo)
- **Traduction :** Modulo / Reste
- **Définition :** Donne le reste d'une division
- **Exemple :** `10 % 3` → 1 (car 10 ÷ 3 = 3 reste 1)

### **^** (power)
- **Traduction :** Puissance
- **Définition :** Élève un nombre à une puissance
- **Exemple :** `2 ^ 3` → 8 (2 × 2 × 2)

---

## Opérateurs de comparaison

### **==** (equal)
- **Traduction :** Égal à
- **Définition :** Vérifie si deux valeurs sont identiques
- **Exemple :** `age == 15` (vrai si age vaut 15)

### **~=** (not equal)
- **Traduction :** Différent de / Pas égal à
- **Définition :** Vérifie si deux valeurs sont différentes
- **Exemple :** `age ~= 18` (vrai si age n'est pas 18)

### **>** (greater than)
- **Traduction :** Plus grand que / Supérieur à
- **Définition :** Vérifie si une valeur est supérieure à une autre
- **Exemple :** `age > 12` (vrai si age est plus grand que 12)

### **<** (less than)
- **Traduction :** Plus petit que / Inférieur à
- **Définition :** Vérifie si une valeur est inférieure à une autre
- **Exemple :** `age < 18` (vrai si age est moins de 18)

### **>=** (greater or equal)
- **Traduction :** Plus grand ou égal à
- **Définition :** Vérifie si une valeur est supérieure ou égale à une autre
- **Exemple :** `age >= 18` (vrai si age est 18 ou plus)

### **<=** (less or equal)
- **Traduction :** Plus petit ou égal à
- **Définition :** Vérifie si une valeur est inférieure ou égale à une autre
- **Exemple :** `age <= 12` (vrai si age est 12 ou moins)

---

## Structures conditionnelles

### **if**
- **Traduction :** Si
- **Définition :** Exécute du code seulement si une condition est vraie
- **Exemple :**
```lua
if age >= 18 then
    print("Majeur")
end
```

### **then**
- **Traduction :** Alors
- **Définition :** Suit toujours un `if` ou `elseif` pour indiquer le début du code à exécuter
- **Exemple :** `if age >= 18 then`

### **else**
- **Traduction :** Sinon
- **Définition :** Exécute du code si la condition du `if` est fausse
- **Exemple :**
```lua
if age >= 18 then
    print("Majeur")
else
    print("Mineur")
end
```

### **elseif**
- **Traduction :** Sinon si
- **Définition :** Permet de tester une autre condition si la première est fausse
- **Exemple :**
```lua
if age < 12 then
    print("Enfant")
elseif age < 18 then
    print("Adolescent")
else
    print("Adulte")
end
```

### **end**
- **Traduction :** Fin
- **Définition :** Marque la fin d'une structure (if, function, loop, etc.)
- **Exemple :** `end`

---

## Opérateurs logiques

### **and**
- **Traduction :** Et
- **Définition :** Les deux conditions doivent être vraies
- **Exemple :** `if age >= 12 and age < 18 then` (vrai si age entre 12 et 17)

### **or**
- **Traduction :** Ou
- **Définition :** Au moins une des conditions doit être vraie
- **Exemple :** `if weekend or vacances then` (vrai si c'est le weekend OU les vacances)

### **not**
- **Traduction :** Non / Pas
- **Définition :** Inverse une condition (vrai devient faux, faux devient vrai)
- **Exemple :** `if not vivant then` (vrai si vivant est false)

---

## Boucles

### **while**
- **Traduction :** Tant que
- **Définition :** Répète du code tant qu'une condition est vraie
- **Exemple :**
```lua
while compteur < 10 do
    print(compteur)
    compteur = compteur + 1
end
```

### **for**
- **Traduction :** Pour
- **Définition :** Répète du code un nombre précis de fois
- **Exemple :**
```lua
for i = 1, 10 do
    print(i)
end
```

### **do**
- **Traduction :** Faire
- **Définition :** Marque le début du code à répéter dans une boucle
- **Exemple :** `while condition do`

### **repeat**
- **Traduction :** Répéter
- **Définition :** Répète du code au moins une fois, puis continue tant que la condition est fausse
- **Exemple :**
```lua
repeat
    print("Essayez encore")
    reponse = io.read()
until reponse == "oui"
```

### **until**
- **Traduction :** Jusqu'à
- **Définition :** Utilisé avec `repeat`, arrête la boucle quand la condition devient vraie
- **Exemple :** `until condition`

### **break**
- **Traduction :** Casser / Sortir
- **Définition :** Sort immédiatement d'une boucle
- **Exemple :**
```lua
while true do
    if condition then
        break
    end
end
```

---

## Fonctions

### **function**
- **Traduction :** Fonction
- **Définition :** Déclare un bloc de code réutilisable
- **Exemple :**
```lua
function direBonjour()
    print("Bonjour !")
end
```

### **return**
- **Traduction :** Retourner / Renvoyer
- **Définition :** Renvoie une valeur depuis une fonction et arrête son exécution
- **Exemple :**
```lua
function addition(a, b)
    return a + b
end
```

---

## Fonctions utiles

### **type()**
- **Traduction :** Type
- **Définition :** Retourne le type d'une variable (string, number, boolean, etc.)
- **Exemple :** `print(type(age))` → "number"

### **tonumber()**
- **Traduction :** Vers nombre
- **Définition :** Convertit une valeur en nombre
- **Exemple :** `local age = tonumber("15")` → 15

### **tostring()**
- **Traduction :** Vers chaîne
- **Définition :** Convertit une valeur en texte
- **Exemple :** `tostring(15)` → "15"

### **io.read()**
- **Traduction :** Lire l'entrée
- **Définition :** Lit ce que l'utilisateur tape dans le terminal
- **Exemple :** `local nom = io.read()`

### **string.lower()**
- **Traduction :** En minuscules
- **Définition :** Convertit un texte en minuscules
- **Exemple :** `string.lower("BONJOUR")` → "bonjour"

### **string.upper()**
- **Traduction :** En majuscules
- **Définition :** Convertit un texte en majuscules
- **Exemple :** `string.upper("bonjour")` → "BONJOUR"

### **math.random()**
- **Traduction :** Aléatoire
- **Définition :** Génère un nombre aléatoire
- **Exemple :** `math.random(1, 10)` → nombre entre 1 et 10

---

## Symboles spéciaux

### **..** (concatenation)
- **Traduction :** Concaténation
- **Définition :** Colle deux chaînes de caractères ensemble
- **Exemple :** `"Bonjour " .. "Alice"` → "Bonjour Alice"

### **#** (length)
- **Traduction :** Longueur / Taille
- **Définition :** Donne la taille d'un tableau ou d'une chaîne
- **Exemple :** `#inventaire` → nombre d'éléments dans le tableau

### **--** (comment)
- **Traduction :** Commentaire
- **Définition :** Ligne ignorée par Lua, sert à expliquer le code
- **Exemple :** `-- Ceci est un commentaire`

### **--[[  ]]** (multi-line comment)
- **Traduction :** Commentaire multiligne
- **Définition :** Bloc de texte ignoré par Lua
- **Exemple :**
```lua
--[[
Ceci est un commentaire
sur plusieurs lignes
]]
```

### **{ }** (table constructor)
- **Traduction :** Accolades / Constructeur de tableau
- **Définition :** Crée un tableau
- **Exemple :** `local scores = {100, 200, 150}`

### **[ ]** (index)
- **Traduction :** Crochets / Index
- **Définition :** Accède à un élément d'un tableau
- **Exemple :** `inventaire[1]` → premier élément

### **( )** (parentheses)
- **Traduction :** Parenthèses
- **Définition :** Groupe des opérations ou passe des paramètres à une fonction
- **Exemple :** `(2 + 3) * 4` ou `print("texte")`

---

## Termes de programmation

### **Variable**
- **Définition :** Boîte qui stocke une valeur (nombre, texte, etc.)
- **Exemple :** `local age = 15`

### **Condition**
- **Définition :** Test qui vérifie si quelque chose est vrai ou faux
- **Exemple :** `if age >= 18 then`

### **Boucle** (Loop)
- **Définition :** Structure qui répète du code plusieurs fois
- **Exemple :** `for i = 1, 10 do`

### **Fonction** (Function)
- **Définition :** Bloc de code réutilisable qu'on peut appeler
- **Exemple :** `function direBonjour()`

### **Paramètre** (Parameter)
- **Définition :** Valeur qu'on donne à une fonction
- **Exemple :** Dans `print("texte")`, "texte" est le paramètre

### **Tableau** (Table/Array)
- **Définition :** Liste qui contient plusieurs valeurs
- **Exemple :** `local noms = {"Alice", "Bob", "Charlie"}`

### **Index**
- **Définition :** Position d'un élément dans un tableau (commence à 1 en Lua)
- **Exemple :** `noms[1]` → "Alice"

### **Concaténation**
- **Définition :** Action de coller/assembler plusieurs textes
- **Exemple :** `"Bon" .. "jour"` → "Bonjour"

### **Itération**
- **Définition :** Une répétition dans une boucle
- **Exemple :** Dans `for i = 1, 5`, il y a 5 itérations

### **Syntaxe**
- **Définition :** Règles d'écriture du code (comme la grammaire)
- **Exemple :** Oublier `then` après `if` est une erreur de syntaxe

### **Bug / Erreur**
- **Définition :** Problème dans le code qui empêche le programme de fonctionner
- **Exemple :** `print("texte"` → manque la parenthèse fermante

### **Débugger** (Debug)
- **Définition :** Chercher et corriger les erreurs dans le code
- **Exemple :** Lire les messages d'erreur et corriger le code

---

## Valeurs spéciales

### **true**
- **Traduction :** Vrai
- **Définition :** Valeur booléenne représentant "vrai"
- **Exemple :** `local vivant = true`

### **false**
- **Traduction :** Faux
- **Définition :** Valeur booléenne représentant "faux"
- **Exemple :** `local estMort = false`

---

## Conventions de nommage

### **Camel Case**
- **Définition :** Style d'écriture où chaque nouveau mot commence par une majuscule (sauf le premier)
- **Exemple :** `nomDuJoueur`, `pointsDeVie`, `scoreTotal`

### **Snake Case**
- **Définition :** Style d'écriture où les mots sont séparés par des underscores
- **Exemple :** `nom_du_joueur`, `points_de_vie`, `score_total`

---

## Astuces

💡 **Bonne pratique :** Toujours utiliser `local` pour déclarer des variables

💡 **Attention :** En Lua, les tableaux commencent à l'index 1 (pas 0 comme dans d'autres langages)

💡 **Rappel :** `=` assigne une valeur, `==` compare deux valeurs

💡 **Conseil :** Utiliser des noms de variables descriptifs : `pointsDeVie` plutôt que `pdv` ou `x`
