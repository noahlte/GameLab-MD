# 07. Projet Final - Jeu Textuel en Lua

## Introduction

Félicitations ! 🎉 Tu as appris tout ce qu'il faut savoir pour connaître les **bases du Lua**.

Maintenant, il est l'heure de mettre en pratique ce qu'on a appris dans un dernier projet.

---

## But de l'exercice

Réalise un **jeu textuel** (un jeu qui se joue dans le terminal).

### Contraintes :

Le jeu doit utiliser **TOUTES** les notions apprises :
- Variables
- Conditions
- Boucles
- Tableaux
- Fonctions

Le jeu doit être **assez long** et **un minimum complexe**

Tu es **totalement libre** sur l'idée du jeu et son concept !

---

## Exemples de jeux textuels

Voici quelques idées pour t'inspirer :

### 1. Jeu à choix multiples
Une aventure interactive où le joueur fait des choix qui influencent l'histoire.

**Exemple :**
```
Vous êtes dans une forêt sombre.
[1] Aller à gauche
[2] Aller à droite
[3] Monter à l'arbre
Votre choix : _
```

### 2. Pierre, Papier, Ciseaux (évolué)
Un Pierre-Papier-Ciseaux contre l'IA avec :
- Score sur plusieurs manches
- Statistiques
- Niveaux de difficulté

### 3. Morpion (OXO)
Un jeu de morpion 3x3 :
- Joueur vs Joueur
- Ou Joueur vs IA

### 4. Quizz
Un jeu de questions-réponses :
- Plusieurs catégories
- Score
- Timer (optionnel)

### 5. RPG de combat
Un système de combat au tour par tour :
- Personnage avec stats (vie, mana, attaque)
- Plusieurs ennemis
- Inventaire
- Sorts et attaques

### 6. Jeu de devinettes
Devine le nombre, le mot, etc. :
- Nombre de tentatives limitées
- Indices
- Score

### 7. Pendu
Le jeu du pendu classique :
- Choisir un mot aléatoire
- Afficher les lettres trouvées
- Nombre d'erreurs limité

### 8. Labyrinthe textuel
Se déplacer dans un labyrinthe en utilisant les directions.

---

## Exemple complet : Pierre, Papier, Ciseaux

Voici un exemple de projet complet pour t'inspirer.

### Code commenté

```lua
-- Initialisation du générateur aléatoire
math.randomseed(os.time())

-- Variables globales
local scoreJoueur = 0
local scoreIA = 0
local scoreVictoire = 3
local menu = 0

-- Fonction pour demander le choix du joueur
local function choixJoueur()
    while true do
        print("Pierre, papier ou ciseau ? (r, p, c) : ")
        local choice = string.lower(io.read())

        if choice == "r" or choice == "c" or choice == "p" then
            return choice
        else
            print("Choix incorrect\n")
        end
    end
end

-- Fonction pour générer le choix de l'IA
local function choixIA()
    local possibleChoice = {'r', 'p', 'c'}
    return possibleChoice[math.random(3)]
end

-- Fonction pour vérifier qui a gagné
local function checkGagnant(choixJoueur, choixIA)
    local regles = {
        r = {r = "=", p = "IA", c = "Joueur"},
        p = {r = "Joueur", p = "=", c = "IA"},
        c = {r = "IA", p = "Joueur", c = "="}
    }

    return regles[choixJoueur][choixIA]
end

-- Fonction principale du jeu
local function lancerLeJeu()
    repeat
        local choixDuJoueur = choixJoueur()
        local choixDeIA = choixIA()
        local gagnant = checkGagnant(choixDuJoueur, choixDeIA)

        print("Joueur : " .. choixDuJoueur .. " / IA : " .. choixDeIA .. "\n")

        if gagnant == "=" then
            print("C'est une égalité !\n")
        elseif gagnant == "Joueur" then
            print("Le joueur gagne un point !\n")
            scoreJoueur = scoreJoueur + 1
        else
            print("L'IA gagne un point !\n")
            scoreIA = scoreIA + 1
        end

        print("Score : Joueur " .. scoreJoueur .. " - " .. scoreIA .. " IA\n")
    until scoreJoueur == scoreVictoire or scoreIA == scoreVictoire

    if scoreIA == scoreVictoire then
        print("L'IA a gagné la partie !\n")
    else
        print("Le joueur a gagné la partie !\n")
    end
end

-- Menu principal
repeat
    print("Choisissez parmi les 2 choix suivants :")
    print("1. Jouer")
    print("2. Quitter le jeu\n")
    menu = tonumber(io.read())

    if menu == nil or menu > 2 or menu < 1 then
        print("Choix incorrect\n")
    end

    if menu == 1 then
        scoreIA = 0
        scoreJoueur = 0
        lancerLeJeu()
    end
until menu == 2

print("Merci d'avoir joué ! Au revoir.")
```

---

## Conseils pour ton projet

### 1. Planification

Avant de coder, **réfléchis** à ton projet :
- Quel est le but du jeu ?
- Quelles sont les règles ?
- Comment le joueur gagne-t-il ?
- De quelles variables ai-je besoin ?
- Quelles fonctions créer ?

### 2. Structure du code

Organise ton code avec des fonctions :
- Une fonction pour le menu
- Une fonction pour le jeu principal
- Des fonctions pour chaque action

### 3. Commence simple

1. Crée d'abord une **version simple** qui fonctionne
2. Ajoute des **fonctionnalités** progressivement
3. **Teste** régulièrement ton code

### 4. Gestion des erreurs

Vérifie que l'utilisateur entre des valeurs correctes :
```lua
local choix = tonumber(io.read())
if choix == nil then
    print("Erreur : entrez un nombre !")
end
```

### 5. Améliore l'interface

Rends ton jeu agréable à jouer :
- Ajoute des séparateurs
- Affiche des messages clairs
- Utilise des espaces et des retours à la ligne

**Exemple :**
```lua
print("\n================================")
print("       BIENVENUE AU JEU")
print("================================\n")
```

---

## Idées d'améliorations

Une fois ton jeu de base fonctionnel, tu peux ajouter :

### Système de difficulté
```lua
print("Choisissez la difficulté :")
print("[1] Facile")
print("[2] Normal")
print("[3] Difficile")
```

### Sauvegarde de score
Garde le meilleur score dans un tableau.

### Système de niveaux
Le jeu devient plus difficile au fur et à mesure.

### Statistiques
Affiche des stats à la fin :
- Nombre de parties jouées
- Taux de victoire
- Meilleur score

### Sons (avec Love2D)
Si tu utilises Love2D plus tard, tu pourras ajouter des sons et de la musique !

---

## Checklist avant de rendre ton projet

Le code fonctionne sans erreur

J'ai utilisé :
- [ ] Des variables
- [ ] Des conditions (if/elseif/else)
- [ ] Des boucles (for, while ou repeat)
- [ ] Des tableaux
- [ ] Des fonctions

Le code est **commenté** (explications avec `--`)

Le code est **indenté** proprement

Les noms de variables sont **clairs**

Le jeu est **jouable** et **amusant**

---

## Exemples de projets à réaliser

### Projet facile
- Jeu de devinette de nombre
- Pierre-Papier-Ciseaux
- Quizz simple

### Projet moyen
- Morpion (OXO)
- Pendu
- Calculatrice avancée avec historique

### Projet difficile
- RPG de combat au tour par tour
- Jeu d'aventure textuel à choix multiples
- Labyrinthe avec inventaire

---

## À toi de jouer !

C'est le moment de **créer ton propre jeu** !

### Étapes recommandées :

1. **Choisis** ton type de jeu
2. **Planifie** sur papier (règles, fonctions, variables)
3. **Code** une version simple
4. **Teste** et corrige les bugs
5. **Améliore** en ajoutant des fonctionnalités
6. **Peaufine** l'interface et les messages

**Bon courage et amuse-toi bien !** 🚀

---

## Ressources supplémentaires

### Documentation Lua
- [Manuel de référence Lua](https://www.lua.org/manual/5.4/)
- [Tutoriels Lua](https://www.lua.org/pil/)

### Prochaines étapes
Une fois que tu maîtrises Lua, tu peux :
- Créer des jeux avec **Love2D**
- Modder des jeux comme **Roblox** ou **Garry's Mod**
- Apprendre d'autres langages comme **Python** ou **JavaScript**

---

## Partage ton projet !

N'hésite pas à partager ton jeu avec tes amis ou ton professeur !

Tu peux aussi :
- Demander des retours pour l'améliorer
- Ajouter de nouvelles fonctionnalités
- Créer une version 2.0 encore meilleure

**Félicitations d'avoir terminé ce cours de Lua !**

Tu as maintenant toutes les bases pour créer tes propres programmes et jeux. Continue à pratiquer et à créer !
