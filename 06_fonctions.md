# 06. Les Fonctions en Lua

## Les Fonctions - C'est quoi ?

Une **fonction** est un **BLOC DE CODE RÉUTILISABLE** qu'on peut appeler plusieurs fois.

Au lieu de copier-coller le même code partout, on crée une fonction !

### Pourquoi utiliser des fonctions ?

Imagine que tu veux dire "Bonjour" 100 fois dans ton programme.

**Sans fonction :**
```lua
print("Bonjour")
print("Bonjour")
print("Bonjour")
-- ... répété 100 fois
```

**Avec fonction :**
```lua
function direBonjour()
    print("Bonjour")
end

-- Appeler 100 fois
for i = 1, 100 do
    direBonjour()
end
```

### Les avantages des fonctions

- **RÉUTILISER** du code sans le réécrire
- **ORGANISER** le code en petits morceaux
- **SIMPLIFIER** la lecture du code
- **ÉVITER** les erreurs (on modifie à un seul endroit)

### Tu as déjà utilisé des fonctions !

- `print()` → affiche du texte
- `tonumber()` → convertit en nombre
- `table.insert()` → ajoute dans un tableau
- `math.random()` → génère un nombre aléatoire

Maintenant, tu vas créer **TES PROPRES fonctions** !

---

## Créer une fonction simple

### Syntaxe

```lua
local function nomDeLaFonction()
    -- code à exécuter
end
```

Pour utiliser la fonction, on l'**APPELLE** :

```lua
nomDeLaFonction()
```

### Exemple

```lua
local function direBonjour()
    print("Bonjour !")
    print("Comment ça va ?")
end

-- Appeler la fonction
direBonjour()
direBonjour()
direBonjour()
```

**Résultat :**
```
Bonjour !
Comment ça va ?
Bonjour !
Comment ça va ?
Bonjour !
Comment ça va ?
```

### Exemple : Séparateur

```lua
local function afficherSeparateur()
    print("====================")
end

afficherSeparateur()
print("Menu principal")
afficherSeparateur()
```

**Résultat :**
```
====================
Menu principal
====================
```

---

## Fonctions avec paramètres

Les **paramètres** sont des **VALEURS** qu'on donne à la fonction.

C'est comme une variable qui change à chaque appel !

### Syntaxe

```lua
local function nomFonction(parametre1, parametre2)
    -- code qui utilise les paramètres
end
```

### Exemple : Un paramètre

```lua
local function saluer(nom)
    print("Bonjour " .. nom .. " !")
end

saluer("Alice")   -- Bonjour Alice !
saluer("Bob")     -- Bonjour Bob !
saluer("Charlie") -- Bonjour Charlie !
```

### Exemple : Deux paramètres

```lua
local function presenter(nom, age)
    print("Je m'appelle " .. nom .. " et j'ai " .. age .. " ans.")
end

presenter("Alice", 14)  -- Je m'appelle Alice et j'ai 14 ans.
presenter("Bob", 15)    -- Je m'appelle Bob et j'ai 15 ans.
```

### Exemple : Fonction mathématique

```lua
local function addition(a, b)
    local resultat = a + b
    print(a .. " + " .. b .. " = " .. resultat)
end

addition(5, 3)    -- 5 + 3 = 8
addition(10, 25)  -- 10 + 25 = 35
```

### Exemple : Créer un personnage

```lua
local function creerPersonnage(nom, classe, niveau, vie)
    print("=== NOUVEAU PERSONNAGE ===")
    print("Nom : " .. nom)
    print("Classe : " .. classe)
    print("Niveau : " .. niveau)
    print("Points de vie : " .. vie)
    print("==========================")
end

creerPersonnage("Arthur", "Guerrier", 10, 150)
creerPersonnage("Merlin", "Mage", 8, 80)
```

---

## RETURN - Renvoyer une valeur

`return` permet à une fonction de **RENVOYER** un résultat.

Au lieu de juste afficher, la fonction calcule et **RETOURNE** le résultat.

On peut ensuite utiliser ce résultat dans une variable ou un calcul.

### Exemple : Addition

```lua
local function additionner(a, b)
    return a + b
end

local somme = additionner(5, 3)
print("Résultat : " .. somme)  -- 8

local total = additionner(10, 20) + additionner(5, 15)
print("Total : " .. total)  -- 50
```

### Exemple : Fonctions mathématiques

```lua
local function multiplier(a, b)
    return a * b
end

local function diviser(a, b)
    if b == 0 then
        print("Erreur : division par zéro !")
        return nil
    end
    return a / b
end

print(multiplier(5, 3))  -- 15
print(diviser(10, 2))    -- 5
print(diviser(10, 0))    -- nil (erreur)
```

### Exemple : Vérifier si un nombre est pair

```lua
local function estPair(nombre)
    if nombre % 2 == 0 then
        return true
    else
        return false
    end
end

-- Version plus courte
local function estPair2(nombre)
    return nombre % 2 == 0
end

print(estPair(4))   -- true
print(estPair(7))   -- false
print(estPair2(10)) -- true
```

---

## Return multiple

En Lua, une fonction peut renvoyer **PLUSIEURS valeurs** à la fois !

### Exemple

```lua
local function calculerStats(nombre)
    local double = nombre * 2
    local triple = nombre * 3
    local carre = nombre ^ 2
    return double, triple, carre
end

local d, t, c = calculerStats(5)
print("Double : " .. d)   -- 10
print("Triple : " .. t)   -- 15
print("Carré : " .. c)    -- 25
```

### Exemple : Diviser avec reste

```lua
local function divisionComplete(a, b)
    local quotient = math.floor(a / b)
    local reste = a % b
    return quotient, reste
end

local q, r = divisionComplete(17, 5)
print("17 ÷ 5 = " .. q .. " reste " .. r)  -- 17 ÷ 5 = 3 reste 2
```

---

## Portée des variables (Scope)

Les variables déclarées **DANS** une fonction n'existent **QUE** dans cette fonction.

On appelle ça la **PORTÉE LOCALE**.

### Exemple

```lua
local function tester()
    local message = "Je suis dans la fonction"
    print(message)
end

tester()
-- print(message)  -- ERREUR ! message n'existe pas ici
```

### Variable globale vs locale

```lua
local compteur = 0  -- Variable en dehors de la fonction

local function incrementer()
    compteur = compteur + 1  -- On peut utiliser la variable extérieure
    print("Compteur : " .. compteur)
end

incrementer()  -- 1
incrementer()  -- 2
incrementer()  -- 3
```

---

## Fonctions qui appellent d'autres fonctions

Une fonction peut en appeler une autre !

C'est très utile pour organiser le code.

### Exemple

```lua
local function calculerCarre(n)
    return n * n
end

local function calculerSommesCarres(a, b)
    local carreA = calculerCarre(a)
    local carreB = calculerCarre(b)
    return carreA + carreB
end

local resultat = calculerSommesCarres(3, 4)
print("3² + 4² = " .. resultat)  -- 9 + 16 = 25
```

### Exemple : Système de combat

```lua
local function calculerDegats(attaque, defense)
    local degats = attaque - defense
    if degats < 0 then
        degats = 0
    end
    return degats
end

local function attaquer(nomAttaquant, attaque, nomDefenseur, defense, vie)
    print(nomAttaquant .. " attaque " .. nomDefenseur .. " !")

    local degats = calculerDegats(attaque, defense)
    print("Dégâts infligés : " .. degats)

    vie = vie - degats
    if vie < 0 then
        vie = 0
    end

    print(nomDefenseur .. " a maintenant " .. vie .. " PV")
    return vie
end

local vieEnnemi = 100
vieEnnemi = attaquer("Arthur", 35, "Gobelin", 10, vieEnnemi)
```

---

## Paramètres par défaut

On peut donner des **valeurs par défaut** aux paramètres.

Si on ne donne pas de valeur, la valeur par défaut est utilisée.

### Exemple

```lua
local function salutation(nom, titre)
    titre = titre or "Aventurier"  -- Si titre est nil, utilise "Aventurier"
    print("Bonjour " .. titre .. " " .. nom .. " !")
end

salutation("Alice", "Magicienne")  -- Bonjour Magicienne Alice !
salutation("Bob")                   -- Bonjour Aventurier Bob !
```

### Exemple : Créer un ennemi

```lua
local function creerEnnemi(nom, vie, attaque)
    vie = vie or 50        -- Par défaut : 50 PV
    attaque = attaque or 10 -- Par défaut : 10 d'attaque

    print("Ennemi créé : " .. nom)
    print("Vie : " .. vie)
    print("Attaque : " .. attaque)
end

creerEnnemi("Gobelin", 30, 15)
creerEnnemi("Slime")  -- Utilise les valeurs par défaut
```

---

## Fonctions avec tableaux

Les fonctions peuvent recevoir et retourner des tableaux.

### Afficher un inventaire

```lua
local function afficherInventaire(inventaire)
    print("=== INVENTAIRE ===")
    for i, objet in ipairs(inventaire) do
        print(i .. ". " .. objet)
    end
    print("Total : " .. #inventaire .. " objets")
end

local sac = {"Épée", "Potion", "Bouclier"}
afficherInventaire(sac)
```

### Calculer la moyenne

```lua
local function calculerMoyenne(nombres)
    local somme = 0
    for i = 1, #nombres do
        somme = somme + nombres[i]
    end
    return somme / #nombres
end

local notes = {15, 18, 12, 20, 16}
local moyenne = calculerMoyenne(notes)
print("Moyenne : " .. moyenne)  -- 16.2
```

### Retourner un tableau

```lua
local function creerEquipe(nbJoueurs)
    local equipe = {}
    for i = 1, nbJoueurs do
        table.insert(equipe, "Joueur " .. i)
    end
    return equipe
end

local team = creerEquipe(5)
for i, joueur in ipairs(team) do
    print(i .. ". " .. joueur)
end
```

---

## Fonctions utilitaires

Créer des petites fonctions utiles qu'on peut réutiliser partout.

### Barre de vie

```lua
local function afficherBarreVie(vie, vieMax)
    local pourcentage = (vie / vieMax) * 100
    local barres = math.floor(pourcentage / 10)

    local barre = "["
    for i = 1, 10 do
        if i <= barres then
            barre = barre .. "="
        else
            barre = barre .. " "
        end
    end
    barre = barre .. "] " .. vie .. "/" .. vieMax .. " PV"

    print(barre)
end

afficherBarreVie(75, 100)   -- [=======   ] 75/100 PV
afficherBarreVie(30, 100)   -- [===       ] 30/100 PV
afficherBarreVie(100, 100)  -- [==========] 100/100 PV
```

---

## Récursivité (Avancé)

Une fonction peut s'appeler **ELLE-MÊME** !

**ATTENTION :** Il faut toujours une condition d'arrêt, sinon boucle infinie !

### Exemple : Factorielle

```lua
local function factorielle(n)
    if n <= 1 then
        return 1  -- Condition d'arrêt
    else
        return n * factorielle(n - 1)  -- Appel récursif
    end
end

print("5! = " .. factorielle(5))  -- 120
```

**Explication :**
- `factorielle(5)` = 5 × `factorielle(4)`
- `factorielle(4)` = 4 × `factorielle(3)`
- `factorielle(3)` = 3 × `factorielle(2)`
- `factorielle(2)` = 2 × `factorielle(1)`
- `factorielle(1)` = 1
- Résultat : 5 × 4 × 3 × 2 × 1 = 120

---

## Erreurs courantes

### 1. Oublier les parenthèses

**Mauvais :**
```lua
function test()
    print("Test")
end

test  -- N'APPELLE PAS la fonction
```

**Bon :**
```lua
test()  -- APPELLE la fonction
```

### 2. Oublier return

**Mauvais :**
```lua
function multiplier(a, b)
    a * b  -- Ne fait rien !
end

local resultat = multiplier(5, 3)
print(resultat)  -- nil
```

**Bon :**
```lua
function multiplier(a, b)
    return a * b
end
```

---

## Bonnes pratiques

Donner des **NOMS CLAIRS** aux fonctions (verbes d'action)
- `calculerScore()`, `afficherMenu()`, `verifierVictoire()`

Une fonction = **UNE TÂCHE**
- Pas de fonction qui fait 10 choses différentes

Utiliser `return` pour renvoyer des résultats
- Au lieu de `print()` dans la fonction

Toujours déclarer les variables locales avec `local`

Commenter les fonctions complexes
- Expliquer ce qu'elles font, les paramètres, ce qu'elles retournent

---

## Exercice : Calculatrice avec fonctions

Crée une calculatrice complète en utilisant des fonctions.

### Consignes :

1. Crée 4 fonctions mathématiques :
   - `addition(a, b)` → retourne `a + b`
   - `soustraction(a, b)` → retourne `a - b`
   - `multiplication(a, b)` → retourne `a * b`
   - `division(a, b)` → retourne `a / b` (attention à la division par zéro !)

2. Crée une fonction `afficherMenu()` qui affiche :
   ```
   === CALCULATRICE ===
   [1] Addition
   [2] Soustraction
   [3] Multiplication
   [4] Division
   [5] Quitter
   ```

3. Crée une fonction `demanderNombre(message)` qui :
   - Affiche le message
   - Lit un nombre avec `io.read()`
   - Retourne le nombre

4. Programme principal :
   - Affiche le menu
   - Demande le choix de l'utilisateur
   - Demande deux nombres
   - Appelle la bonne fonction
   - Affiche le résultat
   - Répète jusqu'à "Quitter"

**BONUS :**
- Ajoute `puissance(a, b)` qui calcule `a^b`
- Gère les erreurs (division par zéro, nombres invalides)

<details>
<summary>Voir la correction</summary>

```lua
local function addition(a, b)
    return a + b
end

local function soustraction(a, b)
    return a - b
end

local function multiplication(a, b)
    return a * b
end

local function division(a, b)
    if b == 0 then
        return nil, "Erreur : division par zéro"
    end
    return a / b
end

local function afficherMenu()
    print("\n=== CALCULATRICE ===")
    print("[1] Addition")
    print("[2] Soustraction")
    print("[3] Multiplication")
    print("[4] Division")
    print("[5] Quitter")
end

local function demanderNombre(message)
    print(message)
    return tonumber(io.read())
end

-- Programme principal
local choix

repeat
    afficherMenu()
    print("Votre choix : ")
    choix = tonumber(io.read())

    if choix >= 1 and choix <= 4 then
        local a = demanderNombre("Entrez le premier nombre : ")
        local b = demanderNombre("Entrez le deuxième nombre : ")

        local resultat, erreur

        if choix == 1 then
            resultat = addition(a, b)
        elseif choix == 2 then
            resultat = soustraction(a, b)
        elseif choix == 3 then
            resultat = multiplication(a, b)
        elseif choix == 4 then
            resultat, erreur = division(a, b)
        end

        if erreur then
            print(erreur)
        elseif resultat then
            print("Résultat : " .. resultat)
        end
    elseif choix ~= 5 then
        print("Choix invalide !")
    end
until choix == 5

print("Au revoir !")
```

</details>

---

## Points clés à retenir

- Les fonctions permettent de **réutiliser du code**
- Syntaxe : `local function nom(parametres) ... end`
- `return` renvoie un résultat
- Les fonctions peuvent retourner **plusieurs valeurs**
- Les paramètres peuvent avoir des **valeurs par défaut**
- Les variables locales n'existent que dans la fonction
- Les fonctions peuvent appeler d'autres fonctions
- Toujours donner des **noms clairs** aux fonctions

---

## Prochaine étape

Félicitations ! Tu maîtrises maintenant les bases de Lua. Il est temps de mettre tout ça en pratique avec un **projet final** !

**Rendez-vous dans le chapitre suivant : [Projet Final](07_projet_final.md)**
