# Les Tableaux en Lua

## Les Tableaux - C'est quoi ?

Un **tableau** (table en anglais) est comme une **GRANDE BOÎTE** qui contient plusieurs valeurs.

Au lieu de créer plein de variables différentes, on peut tout ranger dans un seul tableau !

### Exemple concret

❌ **Sans tableau :**
```lua
local joueur1 = "Alice"
local joueur2 = "Bob"
local joueur3 = "Charlie"
local joueur4 = "David"
```
4 variables différentes... imagine avec 100 joueurs !

✅ **Avec tableau :**
```lua
local joueurs = {"Alice", "Bob", "Charlie", "David"}
```
Une seule variable qui contient tout !

### Pourquoi utiliser des tableaux ?

Les tableaux sont **INDISPENSABLES** pour :
- Stocker une liste de scores
- Gérer un inventaire de jeu
- Enregistrer les noms de joueurs
- Créer des grilles de jeu (tetris, morpion, etc.)

---

## Créer un tableau

On utilise des **accolades** `{ }` pour créer un tableau.

On sépare les éléments par des **virgules**.

### Exemples

```lua
-- Tableau de noms
local prenoms = {"Alice", "Bob", "Charlie", "David"}

-- Tableau de nombres
local scores = {1200, 850, 2300, 950}

-- Tableau de booléens
local vies = {true, true, false, true}

-- Tableau vide
local inventaire = {}

-- Tableau avec différents types (possible mais pas recommandé)
local melange = {"texte", 42, true, 3.14}
```

---

## Accéder aux éléments

Chaque élément d'un tableau a un **INDEX** (position).

⚠️ **IMPORTANT :** En Lua, les tableaux commencent à **1** (pas 0 comme dans d'autres langages) !

### Syntaxe

```lua
nomTableau[index]
```

### Exemple

```lua
local fruits = {"Pomme", "Banane", "Orange", "Fraise"}

print(fruits[1])  -- Pomme (premier élément)
print(fruits[2])  -- Banane (deuxième élément)
print(fruits[3])  -- Orange
print(fruits[4])  -- Fraise (dernier élément)
```

**Visualisation :**
```
Index :    1         2         3         4
Valeur : "Pomme" "Banane" "Orange" "Fraise"
```

### Utiliser les éléments dans des calculs

```lua
local points = {100, 200, 150, 300}

local total = points[1] + points[2] + points[3] + points[4]
print("Total des points : " .. total)  -- 750

local moyenne = total / 4
print("Moyenne : " .. moyenne)  -- 187.5
```

---

## Modifier un élément

On peut changer la valeur d'un élément en utilisant son index.

```lua
local temperatures = {15, 18, 20, 17}

print("Température du jour 2 : " .. temperatures[2])  -- 18

temperatures[2] = 25  -- Change la température du jour 2
print("Nouvelle température du jour 2 : " .. temperatures[2])  -- 25
```

### Exemple : Inventaire de jeu

```lua
local inventaire = {"Épée", "Potion", "Bouclier"}

print("Objet 2 : " .. inventaire[2])  -- Potion

inventaire[2] = "Super Potion"  -- Améliore la potion
print("Nouvel objet 2 : " .. inventaire[2])  -- Super Potion
```

---

## Taille d'un tableau (#)

Le symbole `#` devant un tableau donne sa **TAILLE** (nombre d'éléments).

C'est **TRÈS utile** pour savoir combien d'éléments il y a !

```lua
local couleurs = {"Rouge", "Vert", "Bleu", "Jaune"}

print("Nombre de couleurs : " .. #couleurs)  -- 4
```

### Accéder au dernier élément

```lua
local nombres = {10, 20, 30, 40, 50}

print("Premier élément : " .. nombres[1])       -- 10
print("Dernier élément : " .. nombres[#nombres])  -- 50
```

---

## Ajouter des éléments

Pour ajouter un élément à la **fin** d'un tableau, on utilise `table.insert()`.

### Syntaxe

```lua
table.insert(tableau, valeur)
```

### Exemple

```lua
local animaux = {"Chat", "Chien"}
print("Animaux : " .. #animaux)  -- 2

table.insert(animaux, "Lapin")  -- Ajoute "Lapin" à la fin
print("Animaux : " .. #animaux)  -- 3
print("Nouvel animal : " .. animaux[3])  -- Lapin
```

### Ajouter à une position précise

```lua
table.insert(tableau, position, valeur)
```

**Exemple :**

```lua
local podium = {"Alice", "Bob", "Charlie"}

table.insert(podium, 2, "David")  -- Insère David à la position 2
-- Résultat : {"Alice", "David", "Bob", "Charlie"}

for i = 1, #podium do
    print(i .. ". " .. podium[i])
end
```

**Résultat :**
```
1. Alice
2. David
3. Bob
4. Charlie
```

---

## Supprimer des éléments

Pour supprimer un élément, on utilise `table.remove()`.

### Supprimer le dernier élément

```lua
local stack = {"A", "B", "C", "D"}
print("Taille avant : " .. #stack)  -- 4

local dernier = table.remove(stack)  -- Enlève et retourne "D"
print("Élément supprimé : " .. dernier)
print("Taille après : " .. #stack)  -- 3
```

### Supprimer à une position précise

```lua
local joueurs = {"Alice", "Bob", "Charlie", "David"}

table.remove(joueurs, 2)  -- Supprime "Bob" (position 2)
-- Résultat : {"Alice", "Charlie", "David"}

for i = 1, #joueurs do
    print(joueurs[i])
end
```

---

## Parcourir un tableau avec FOR

C'est **ICI** que les boucles deviennent **SUPER PUISSANTES** !

On peut parcourir automatiquement tous les éléments d'un tableau.

### Exemple : Afficher tous les éléments

```lua
local jeux = {"Minecraft", "Roblox", "Fortnite", "Among Us"}

for i = 1, #jeux do
    print(i .. ". " .. jeux[i])
end
```

**Résultat :**
```
1. Minecraft
2. Roblox
3. Fortnite
4. Among Us
```

### Exemple : Calculer la somme

```lua
local notes = {15, 18, 12, 20, 16}
local somme = 0

for i = 1, #notes do
    somme = somme + notes[i]
end

local moyenne = somme / #notes
print("Moyenne des notes : " .. moyenne)  -- 16.2
```

### Exemple : Trouver le maximum

```lua
local scores = {850, 1200, 950, 2100, 1500}
local maximum = scores[1]  -- On commence avec le premier

for i = 2, #scores do
    if scores[i] > maximum then
        maximum = scores[i]
    end
end

print("Meilleur score : " .. maximum)  -- 2100
```

---

## IPAIRS - Parcourir simplement

`ipairs()` est une façon plus élégante de parcourir un tableau.

On obtient automatiquement **l'index ET la valeur**.

### Syntaxe

```lua
for index, valeur in ipairs(tableau) do
    -- code
end
```

### Exemple

```lua
local legumes = {"Carotte", "Tomate", "Salade", "Poivron"}

for index, legume in ipairs(legumes) do
    print(index .. ". " .. legume)
end
```

**Résultat :**
```
1. Carotte
2. Tomate
3. Salade
4. Poivron
```

### Exemple : Afficher l'inventaire

```lua
local inventaire = {"Épée de feu", "Potion de vie", "Armure légère", "Flèches x20"}

print("=== INVENTAIRE ===")
for i, objet in ipairs(inventaire) do
    print("[" .. i .. "] " .. objet)
end
```

**Résultat :**
```
=== INVENTAIRE ===
[1] Épée de feu
[2] Potion de vie
[3] Armure légère
[4] Flèches x20
```

---

## Tableaux associatifs (Dictionnaires)

En Lua, les tableaux peuvent aussi utiliser des **CLÉS** (comme un dictionnaire).

Au lieu d'utiliser des nombres (1, 2, 3...), on utilise des **mots** !

### Créer un tableau associatif

```lua
local joueur = {
    nom = "Alice",
    age = 14,
    niveau = 25,
    classe = "Mage",
    pointsDeVie = 150
}

print("Nom : " .. joueur.nom)        -- Alice
print("Âge : " .. joueur.age)        -- 14
print("Niveau : " .. joueur.niveau)  -- 25
```

### Modifier un tableau associatif

```lua
local hero = {
    nom = "Arthur",
    vie = 100,
    mana = 50
}

print("Vie avant combat : " .. hero.vie)  -- 100
hero.vie = hero.vie - 20  -- Perd 20 points de vie
print("Vie après combat : " .. hero.vie)  -- 80

hero.mana = hero.mana + 10  -- Gagne 10 points de mana
print("Mana : " .. hero.mana)  -- 60
```

### Ajouter de nouvelles propriétés

```lua
local personnage = {
    nom = "Bob"
}

personnage.age = 15  -- Ajoute une nouvelle propriété
personnage.classe = "Guerrier"

print(personnage.nom .. " est un " .. personnage.classe .. " de " .. personnage.age .. " ans")
```

---

## Parcourir un tableau associatif

Pour parcourir un tableau associatif, on utilise **pairs()** (pas ipairs).

```lua
local stats = {
    force = 10,
    intelligence = 15,
    agilite = 12,
    chance = 8
}

print("=== STATISTIQUES ===")
for cle, valeur in pairs(stats) do
    print(cle .. " : " .. valeur)
end
```

**Résultat :**
```
=== STATISTIQUES ===
force : 10
intelligence : 15
agilite : 12
chance : 8
```

---

## Tableaux 2D (Grilles)

Un tableau peut contenir **d'autres tableaux** !

C'est utile pour créer des grilles (morpion, tetris, cartes, etc.).

### Créer une grille 3x3

```lua
local grille = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
}

-- Pour accéder : grille[ligne][colonne]
print(grille[1][1])  -- 1 (ligne 1, colonne 1)
print(grille[2][2])  -- 5 (ligne 2, colonne 2)
print(grille[3][3])  -- 9 (ligne 3, colonne 3)
```

### Afficher une grille

```lua
local plateau = {
    {"X", "O", "X"},
    {"O", "X", "O"},
    {"X", "O", "X"}
}

for ligne = 1, #plateau do
    local texte = ""
    for colonne = 1, #plateau[ligne] do
        texte = texte .. plateau[ligne][colonne] .. " "
    end
    print(texte)
end
```

**Résultat :**
```
X O X
O X O
X O X
```

### Tableau de joueurs avec statistiques

```lua
local equipe = {
    {nom = "Alice", score = 1200, niveau = 15},
    {nom = "Bob", score = 950, niveau = 12},
    {nom = "Charlie", score = 1500, niveau = 18}
}

print("=== ÉQUIPE ===")
for i, joueur in ipairs(equipe) do
    print(i .. ". " .. joueur.nom .. " - Niveau " .. joueur.niveau .. " - Score : " .. joueur.score)
end
```

---

## Fonctions utiles pour tableaux

| Fonction | Description |
|----------|-------------|
| `table.insert(tableau, valeur)` | Ajoute à la fin |
| `table.insert(tableau, position, valeur)` | Ajoute à une position |
| `table.remove(tableau)` | Supprime le dernier |
| `table.remove(tableau, position)` | Supprime à une position |
| `#tableau` | Taille du tableau |
| `table.concat(tableau, séparateur)` | Transforme en texte |

### Exemple : table.concat

```lua
local mots = {"Bonjour", "tout", "le", "monde"}
local phrase = table.concat(mots, " ")
print(phrase)  -- "Bonjour tout le monde"
```

---

## Erreurs courantes

### 1. Oublier que Lua commence à 1

❌ **Mauvais :**
```lua
local tab = {"A", "B", "C"}
print(tab[0])  -- nil (pas d'élément à l'index 0)
```

✅ **Bon :**
```lua
print(tab[1])  -- "A" (premier élément)
```

### 2. Oublier # pour la taille

❌ **Mauvais :**
```lua
local fruits = {"Pomme", "Banane"}
for i = 1, fruits do  -- ERREUR ! Il faut #fruits
    print(fruits[i])
end
```

✅ **Bon :**
```lua
for i = 1, #fruits do
    print(fruits[i])
end
```

---

## Exercice : Gestionnaire de scores

Crée un programme qui gère les scores d'un jeu.

### Fonctionnalités :

1. Crée un tableau vide `scores`
2. Demande à l'utilisateur de saisir **5 scores** (un par un)
3. Stocke chaque score dans le tableau avec `table.insert()`
4. Affiche tous les scores avec leur position
5. Calcule et affiche :
   - Le **score total** (somme)
   - Le **score moyen**
   - Le **meilleur score**
   - Le **pire score**

**Aide :**
- Utilise une boucle `for` pour demander les 5 scores
- Utilise `tonumber(io.read())` pour lire un nombre
- Pour trouver le max : commence avec `scores[1]` puis compare

<details>
<summary>💡 Voir la correction</summary>

```lua
local scores = {}

-- Demander 5 scores
for i = 1, 5 do
    print("Entrez le score " .. i .. " : ")
    local score = tonumber(io.read())
    table.insert(scores, score)
end

-- Afficher les scores
print("\n=== SCORES ===")
for i, score in ipairs(scores) do
    print(i .. ". " .. score)
end

-- Calculs
local total = 0
local meilleur = scores[1]
local pire = scores[1]

for i = 1, #scores do
    total = total + scores[i]

    if scores[i] > meilleur then
        meilleur = scores[i]
    end

    if scores[i] < pire then
        pire = scores[i]
    end
end

local moyenne = total / #scores

print("\nScore total : " .. total)
print("Score moyen : " .. moyenne)
print("Meilleur score : " .. meilleur)
print("Pire score : " .. pire)
```

</details>

---

## Points clés à retenir

- Les tableaux stockent **plusieurs valeurs** dans une seule variable
- On crée un tableau avec des accolades `{ }`
- Les index commencent à **1** en Lua
- `#tableau` donne la taille
- `table.insert()` pour ajouter
- `table.remove()` pour supprimer
- `ipairs()` pour parcourir un tableau numéroté
- `pairs()` pour parcourir un tableau associatif
- Les tableaux 2D permettent de créer des grilles

---

## Prochaine étape

Maintenant que tu sais manipuler des tableaux, passons aux **fonctions** pour créer du code réutilisable !

**Rendez-vous dans le chapitre suivant : [Les Fonctions](06_fonctions.md)**
