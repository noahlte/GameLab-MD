# Les Variables en Lua

## Les Variables - C'est quoi ?

Une **variable**, c'est comme une **boîte** dans laquelle nous allons mettre des éléments avec une **étiquette** qui définit notre élément.

On pourra **ajouter** ou **enlever** des objets dans cette boîte au fur et à mesure de notre code.

### Exemples concrets

Imagine que tu as plusieurs boîtes :
- Une boîte **"nom"** qui contient `"Noah"`
- Une boîte **"age"** qui contient `10`
- Une boîte **"score"** qui contient `1500`

Les variables permettent de **stocker des informations** pour les réutiliser plus tard dans ton programme.

---

## Comment déclarer une variable

En Lua, déclarer une variable est très simple :

```lua
local nom = "Noah"
```

**Décomposition :**
- `local` : indique qu'on crée une variable locale (on verra ça plus tard)
- `nom` : c'est le **nom** de notre variable (l'étiquette sur la boîte)
- `=` : le signe égal permet d'**assigner** une valeur
- `"Noah"` : la **valeur** qu'on met dans la variable

### Afficher une variable

Pour afficher le contenu d'une variable, on utilise `print()` :

```lua
local nom = "Noah"
print(nom)
```

**Résultat :**
```
Noah
```

---

## Règles de nommage

En programmation, il y a des règles pour nommer les variables :

❌ **Interdit :**
- Pas d'accent : `prénom`, `numéro`
- Pas de caractères spéciaux : `$score`, `prix€`
- Pas d'espace : `mon nom`

✅ **Autorisé :**
- Lettres (a-z, A-Z)
- Chiffres (0-9) **MAIS** ne peut pas commencer par un chiffre
- Underscore `_` : `mon_nom`

### La nomenclature Camel Case

Dans ce cours, nous utilisons la **Camel Case** :

```lua
local nomDeLaVariable = "valeur"
local scoreJoueur = 100
local nombreDeVies = 3
```

**Principe :** La première lettre est en minuscule, puis chaque nouveau mot commence par une majuscule.

**Exemples :**
- `prenomJoueur`
- `pointsExperience`
- `estEnVie`

---

## Les types de variables

Il existe plusieurs **types** de données en Lua :

### 1. String (Chaîne de caractères)

Du texte entre guillemets :

```lua
local prenom = "Noah"
local message = "Bonjour le monde"
```

### 2. Number (Nombre)

Des nombres entiers ou à virgule :

```lua
local age = 19
local poids = 52.5
local score = 1500
```

### 3. Boolean (Booléen)

Vrai ou faux :

```lua
local vivant = true
local estMajeur = false
```

### 4. Nil (Vide)

Représente l'absence de valeur :

```lua
local inventaire = nil
```

### Vérifier le type d'une variable

On utilise la fonction `type()` :

```lua
local prenom = "Noah"
local age = 19
local vivant = true

print(type(prenom))   -- affiche : string
print(type(age))      -- affiche : number
print(type(vivant))   -- affiche : boolean
```

---

## La concaténation

La **concaténation** permet d'assembler du texte avec des variables.

On utilise **deux points** `..` pour coller les morceaux ensemble.

### Exemple simple

```lua
local nom = "Noah"
print("Bonjour, je suis " .. nom)
```

**Résultat :**
```
Bonjour, je suis Noah
```

### Concaténation multiple

```lua
local nom = "Noah"
local age = 19

print("Bonjour je m'appelle " .. nom .. ", j'ai " .. age .. " ans.")
```

**Résultat :**
```
Bonjour je m'appelle Noah, j'ai 19 ans.
```

### Convertir en texte avec tostring()

Pour concaténer des booléens, il faut les convertir en texte :

```lua
local vivant = true
print("Vivant : " .. tostring(vivant))
```

**Résultat :**
```
Vivant : true
```

---

## Modifier une variable

Une variable peut **changer de valeur** pendant le programme. C'est ça qui est pratique !

```lua
local score = 0
print("Score de départ : " .. score)

score = 10  -- On change la valeur (sans réécrire "local")
print("Nouveau score : " .. score)

score = score + 5  -- On ajoute 5 au score actuel
print("Score après bonus : " .. score)
```

**Résultat :**
```
Score de départ : 0
Nouveau score : 10
Score après bonus : 15
```

**Important :** Quand on modifie une variable existante, on n'écrit PAS `local` à nouveau !

---

## Les opérations mathématiques

Lua permet de faire des calculs directement dans le code :

### Opérateurs mathématiques

```lua
local a = 10
local b = 3

print("Addition : " .. (a + b))        -- 13
print("Soustraction : " .. (a - b))    -- 7
print("Multiplication : " .. (a * b))  -- 30
print("Division : " .. (a / b))        -- 3.333...
print("Modulo : " .. (a % b))          -- 1
print("Puissance : " .. (a ^ 2))       -- 100
```

### Le modulo (%)

Le **modulo** donne le **reste** d'une division :

```lua
print(10 % 3)  -- 1 (car 10 ÷ 3 = 3 reste 1)
print(15 % 4)  -- 3 (car 15 ÷ 4 = 3 reste 3)
print(8 % 2)   -- 0 (car 8 ÷ 2 = 4 reste 0)
```

**Utilité :** Savoir si un nombre est pair ou impair !
- Si `nombre % 2 == 0`, le nombre est **pair**
- Sinon, le nombre est **impair**

### Stocker un résultat

```lua
local resultat = 10 + 5
print("Résultat : " .. resultat)  -- 15

local moyenne = (10 + 15 + 20) / 3
print("Moyenne : " .. moyenne)  -- 15
```

---

## Ordre des opérations

Comme en mathématiques, il y a un **ordre de priorité** :

1. **Parenthèses** `()`
2. **Puissance** `^`
3. **Multiplication**, **Division**, **Modulo** : `*`, `/`, `%`
4. **Addition**, **Soustraction** : `+`, `-`

### Exemples

```lua
print(2 + 3 * 4)      -- 14 (pas 20 !) car * avant +
print((2 + 3) * 4)    -- 20 (parenthèses en premier)
```

### Application dans un jeu

```lua
local degatsBase = 10
local forceJoueur = 5
local critique = 2

-- Calcul des dégâts avec critique
local degatsTotal = (degatsBase + forceJoueur) * critique
print("Dégâts infligés : " .. degatsTotal)  -- 30
```

---

## Variables locales vs globales

En Lua, on utilise le mot-clé `local` devant une variable :

- **local** : la variable existe seulement dans une partie du code ✅
- **sans local** : la variable existe partout (GLOBAL) ❌ **À ÉVITER !**

### Bonne pratique

**Toujours utiliser `local` !**

```lua
local monNom = "Noah"     -- BIEN ✓
monAutreNom = "Alice"     -- MAL ✗ (ne faites pas ça)
```

---

## Exercices

### Exercice 1 : Créer une fiche de personnage

Crée les variables suivantes pour un personnage de jeu :

1. `nomHeros` (une chaîne de caractères)
2. `niveau` (un nombre)
3. `pointsDeVie` (un nombre)
4. `pointsDeMana` (un nombre)
5. `classe` (guerrier, mage, archer...)

Ensuite, affiche un résumé avec `print()` :

**Format attendu :**
```
[Nom] est un [classe] de niveau [niveau]. Il possède [PV] PV et [mana] mana.
```

**Exemple de résultat :**
```
Arthur est un guerrier de niveau 5. Il possède 150 PV et 30 mana.
```

<details>
<summary>💡 Voir la correction</summary>

```lua
local nomHeros = "Arthur"
local niveau = 5
local pointsDeVie = 150
local pointsDeMana = 30
local classe = "Guerrier"

print(nomHeros .. " est un " .. classe .. " de niveau " .. niveau .. ". Il possède " .. pointsDeVie .. " PV et " .. pointsDeMana .. " de mana.")
```

</details>

---

### Exercice 2 : Calculatrice de statistiques de jeu

Tu as vaincu des monstres et tu dois calculer ton score final !

**Données :**
- `gobelinsVaincus = 12` (chaque gobelin donne **10 points**)
- `trollsVaincus = 3` (chaque troll donne **50 points**)
- `dragonsVaincus = 1` (chaque dragon donne **500 points**)

**À faire :**
1. Calcule le score des gobelins
2. Calcule le score des trolls
3. Calcule le score des dragons
4. Calcule le score total
5. Affiche : `"Score : [score]"`

**BONUS :** Calcule aussi le score moyen par monstre vaincu !
(score total ÷ nombre total de monstres)

<details>
<summary>💡 Voir la correction</summary>

```lua
local gobelinsVaincus = 12
local trollsVaincus = 3
local dragonsVaincus = 1

local score = (gobelinsVaincus * 10) + (trollsVaincus * 50) + (dragonsVaincus * 500)
print("Score : " .. score)

-- Bonus
local nombreTotalMonstres = gobelinsVaincus + trollsVaincus + dragonsVaincus
local moyenne = score / nombreTotalMonstres
print("Score moyen par monstre : " .. moyenne)
```

**Résultat :**
```
Score : 770
Score moyen par monstre : 48.125
```

</details>

---

## Points clés à retenir

- Une variable stocke une valeur avec un nom
- On utilise `local` pour déclarer une variable
- Les types principaux : **string**, **number**, **boolean**, **nil**
- La concaténation se fait avec `..`
- On peut faire des calculs mathématiques : `+`, `-`, `*`, `/`, `%`, `^`
- L'ordre des opérations suit les règles mathématiques
- Toujours utiliser `local` devant les variables

---

## Prochaine étape

Maintenant que tu sais utiliser des variables, passons aux **conditions** pour prendre des décisions dans ton programme !

**Rendez-vous dans le chapitre suivant : [Les Conditions](03_conditions.md)**
