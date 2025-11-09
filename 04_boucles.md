# 04. Les Boucles en Lua

## Les Boucles - C'est quoi ?

Une **boucle** permet de **RÉPÉTER** du code plusieurs fois automatiquement.

Au lieu d'écrire 100 fois `print("Bonjour")`, on peut utiliser une boucle !

### Pourquoi utiliser des boucles ?

Imagine que tu veux compter de 1 à 100 :

**Sans boucle :**
```lua
print(1)
print(2)
print(3)
-- ... (fastidieux !)
print(100)
```

**Avec boucle :**
```lua
for i = 1, 100 do
    print(i)
end
```

Quelques lignes de code suffisent !

### Les 3 types de boucles en Lua

1. **while** (tant que)
2. **for** (pour)
3. **repeat until** (répéter jusqu'à)

---

## La boucle WHILE (Tant que)

La boucle `while` continue **TANT QUE** la condition est vraie.

### Syntaxe

```lua
while condition do
    -- code à répéter
end
```

**En français :**
```
Tant que ... faire
    Ce qui se répète...
Fin
```

**Attention :** Si la condition reste toujours vraie, la boucle ne s'arrête JAMAIS !

### Exemple : Compter de 1 à 5

```lua
local compteur = 1

while compteur <= 5 do
    print(compteur)
    compteur = compteur + 1  -- TRÈS IMPORTANT : faire évoluer la variable !
end
```

**Résultat :**
```
1
2
3
4
5
```

**Que se passe-t-il ?**
1. `compteur = 1`, condition vraie (1 ≤ 5), affiche 1, `compteur` devient 2
2. `compteur = 2`, condition vraie (2 ≤ 5), affiche 2, `compteur` devient 3
3. `compteur = 3`, condition vraie (3 ≤ 5), affiche 3, `compteur` devient 4
4. `compteur = 4`, condition vraie (4 ≤ 5), affiche 4, `compteur` devient 5
5. `compteur = 5`, condition vraie (5 ≤ 5), affiche 5, `compteur` devient 6
6. `compteur = 6`, condition **fausse** (6 ≤ 5), la boucle s'arrête

### Exemple : Demander un mot de passe

```lua
local motDePasse = "secret"
local tentative = ""

while tentative ~= motDePasse do
    print("Entrez le mot de passe : ")
    tentative = io.read()

    if tentative ~= motDePasse then
        print("Mot de passe incorrect ! Réessayez.")
    end
end

print("Accès autorisé ! Bienvenue.")
```

La boucle continue jusqu'à ce que l'utilisateur entre le bon mot de passe.

---

## La boucle FOR numérique

La boucle `for` est parfaite quand on sait **COMBIEN DE FOIS** on veut répéter.

### Syntaxe

```lua
for variable = début, fin do
    -- code à répéter
end
```

**Avec un pas (step) :**

```lua
for variable = début, fin, pas do
    -- code à répéter
end
```

### Exemple : Compter de 1 à 10

```lua
for i = 1, 10 do
    print(i)
end
```

La variable `i` prend automatiquement les valeurs de 1 à 10.

### Exemple : Compter de 10 à 1 (à l'envers)

```lua
for i = 10, 1, -1 do
    print(i)
end

print("Décollage !")
```

**Résultat :**
```
10
9
8
7
6
5
4
3
2
1
Décollage !
```

Le `-1` est le **PAS** (step). Cela signifie qu'on **ENLÈVE 1** à chaque fois.

### Exemple : Compter de 2 en 2

```lua
for i = 0, 20, 2 do
    print(i)
end
```

**Résultat :**
```
0
2
4
6
8
10
12
14
16
18
20
```

### Exemple : Table de multiplication

```lua
local nombre = 7

print("Table de multiplication de " .. nombre .. " :")
for i = 1, 10 do
    local resultat = nombre * i
    print(nombre .. " x " .. i .. " = " .. resultat)
end
```

**Résultat :**
```
Table de multiplication de 7 :
7 x 1 = 7
7 x 2 = 14
7 x 3 = 21
...
7 x 10 = 70
```

---

## WHILE vs FOR : Quand utiliser quoi ?

### Utilise FOR quand :
- Tu sais **COMBIEN DE FOIS** répéter
- Compter de 1 à 10
- Afficher 5 messages
- Table de multiplication

### Utilise WHILE quand :
- Tu ne sais **PAS combien de fois** répéter
- Demander un mot de passe jusqu'à ce qu'il soit bon
- Jouer jusqu'à ce que le joueur perde
- Continuer tant qu'une condition est vraie

---

## La boucle REPEAT UNTIL

`repeat until` est comme `while`, mais :

1. Le code s'exécute **AU MOINS UNE FOIS**
2. On continue **JUSQU'À** ce que la condition soit vraie (inverse de `while`)

### Syntaxe

```lua
repeat
    -- code à répéter
until condition
```

### Différence avec WHILE

- **while** : vérifie **AVANT** d'exécuter
- **repeat until** : exécute **PUIS** vérifie

### Exemple : Demander l'âge

```lua
local age

repeat
    print("Quel est votre âge ? ")
    age = tonumber(io.read())

    if age == nil or age < 0 then
        print("Veuillez entrer un âge valide !")
    end
until age ~= nil and age >= 0

print("Vous avez " .. age .. " ans.")
```

### Exemple : Menu de jeu

```lua
local choix

repeat
    print("\n=== MENU ===")
    print("1. Jouer")
    print("2. Options")
    print("3. Quitter")
    print("Votre choix : ")
    choix = tonumber(io.read())

    if choix == 1 then
        print("Lancement du jeu...")
    elseif choix == 2 then
        print("Options du jeu...")
    elseif choix == 3 then
        print("Au revoir !")
    else
        print("Choix invalide !")
    end
until choix == 3
```

---

## BREAK - Sortir d'une boucle

`break` permet de **SORTIR immédiatement** d'une boucle, même si la condition est encore vraie.

### Exemple : Arrêter à 10

```lua
for i = 1, 100 do
    print(i)

    if i == 10 then
        print("On s'arrête à 10 !")
        break  -- Sort de la boucle
    end
end

print("Fin de la boucle")
```

**Résultat :**
```
1
2
...
10
On s'arrête à 10 !
Fin de la boucle
```

### Exemple : Chercher un nombre

```lua
local nombres = {5, 12, 8, 23, 15, 7}
local cherche = 23
local trouve = false

for i = 1, #nombres do
    if nombres[i] == cherche then
        print("Nombre trouvé à la position " .. i)
        trouve = true
        break  -- Pas besoin de continuer !
    end
end

if not trouve then
    print("Nombre non trouvé")
end
```

---

## Boucles imbriquées

On peut mettre une boucle **DANS** une autre boucle !

C'est utile pour créer des grilles, des tableaux 2D, etc.

### Exemple : Dessiner un rectangle

```lua
local largeur = 10
local hauteur = 5

for ligne = 1, hauteur do
    local texte = ""
    for colonne = 1, largeur do
        texte = texte .. "*"
    end
    print(texte)
end
```

**Résultat :**
```
**********
**********
**********
**********
**********
```

### Exemple : Pyramide

```lua
for ligne = 1, 5 do
    local texte = ""
    for etoile = 1, ligne do
        texte = texte .. "*"
    end
    print(texte)
end
```

**Résultat :**
```
*
**
***
****
*****
```

---

## Erreurs courantes

### 1. Boucle infinie (ne s'arrête jamais)

**Mauvais exemple :**
```lua
local i = 1
while i <= 10 do
    print(i)
    -- OUPS ! On a oublié : i = i + 1
end
```

La boucle ne s'arrête **JAMAIS** car `i` reste toujours 1.

### 2. Mauvais sens (for avec pas négatif)

**Mauvais exemple :**
```lua
for i = 1, 10, -1 do  -- Ne fait RIEN car on va à l'envers
    print(i)
end
```

### 3. Oublier tonumber() avec io.read()

**Mauvais exemple :**
```lua
local age = io.read()  -- age est un STRING, pas un nombre !
```

**Bon exemple :**
```lua
local age = tonumber(io.read())
```

---

## Exercice 1 : FizzBuzz

Crée un programme qui affiche les nombres de 1 à 30, **MAIS** :

- Si le nombre est divisible par 3, affiche **"Fizz"** au lieu du nombre
- Si le nombre est divisible par 5, affiche **"Buzz"** au lieu du nombre
- Si le nombre est divisible par 3 **ET** 5, affiche **"FizzBuzz"**
- Sinon, affiche juste le nombre

**Exemple de résultat :**
```
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
Buzz
11
Fizz
13
14
FizzBuzz
16
...
```

**Aide :**
- Utilise l'opérateur modulo `%` pour vérifier la divisibilité
- `nombre % 3 == 0` signifie "divisible par 3"
- Commence par vérifier **3 ET 5**, puis **3**, puis **5**, puis le reste

<details>
<summary>Voir la correction</summary>

```lua
for i = 1, 30 do
    if i % 3 == 0 and i % 5 == 0 then
        print("FizzBuzz")
    elseif i % 3 == 0 then
        print("Fizz")
    elseif i % 5 == 0 then
        print("Buzz")
    else
        print(i)
    end
end
```

</details>

---

## Exercice 2 : Jeu du Plus ou Moins

Crée un jeu où l'ordinateur choisit un nombre aléatoire entre 1 et 100.
Le joueur doit le deviner !

### Fonctionnalités :

1. L'ordinateur choisit un nombre : `math.random(1, 100)`
2. Le joueur a **7 tentatives maximum**
3. À chaque tentative :
   - Si le nombre est trop petit, affiche "C'est plus !"
   - Si le nombre est trop grand, affiche "C'est moins !"
   - Si c'est le bon nombre, affiche "Bravo !" et arrête le jeu
4. Affiche le nombre de tentatives restantes
5. Si le joueur n'a pas trouvé après 7 tentatives, affiche "Perdu ! C'était [nombre]"

**BONUS :**
Affiche un message différent selon le nombre de tentatives :
- 1-2 tentatives : "Incroyable !"
- 3-4 tentatives : "Très bien !"
- 5-6 tentatives : "Pas mal !"
- 7 tentatives : "De justesse !"

<details>
<summary>Voir la correction</summary>

```lua
math.randomseed(os.time())

local nombreSecret = math.random(1, 100)
local tentativesMax = 7
local trouve = false

print("=== JEU DU PLUS OU MOINS ===")
print("Devinez le nombre entre 1 et 100 !")
print("Vous avez " .. tentativesMax .. " tentatives.\n")

for tentative = 1, tentativesMax do
    print("Tentative " .. tentative .. "/" .. tentativesMax)
    print("Votre nombre : ")
    local devine = tonumber(io.read())

    if devine == nombreSecret then
        print("\nBravo ! Vous avez trouvé !")
        trouve = true

        -- Bonus : message selon le nombre de tentatives
        if tentative <= 2 then
            print("Incroyable !")
        elseif tentative <= 4 then
            print("Très bien !")
        elseif tentative <= 6 then
            print("Pas mal !")
        else
            print("De justesse !")
        end

        break
    elseif devine < nombreSecret then
        print("C'est plus !\n")
    else
        print("C'est moins !\n")
    end
end

if not trouve then
    print("Perdu ! C'était " .. nombreSecret)
end
```

</details>

---

## Points clés à retenir

- Les boucles permettent de **répéter du code**
- **while** : répète **tant que** la condition est vraie
- **for** : répète un **nombre précis** de fois
- **repeat until** : répète **jusqu'à** ce que la condition soit vraie
- **break** : sort immédiatement de la boucle
- Attention aux **boucles infinies** !
- On peut **imbriquer** des boucles (boucle dans une boucle)

---

## Prochaine étape

Maintenant que tu sais répéter des actions, passons aux **tableaux** pour stocker plusieurs valeurs !

**Rendez-vous dans le chapitre suivant : [Les Tableaux](05_tableaux.md)**
