# Hello World - Ton premier programme en Lua

## Introduction

Bienvenue dans ton premier programme en Lua ! Dans cette leçon, nous allons réaliser l'exercice le plus commun à tout langage de programmation : le **Hello World**.

### Pourquoi "Hello World" ?

Pour un peu de contexte, "Hello World" veut dire "Bonjour le monde" en français. D'une manière symbolique, c'est un peu la façon pour l'ordinateur de dire :

> "Bonjour ! Je viens de créer mon premier programme, je parle au monde."

C'est une tradition dans le monde de la programmation. Chaque fois qu'on apprend un nouveau langage, on commence par afficher "Hello World" pour vérifier que tout fonctionne correctement.

---

## Comment faire ?

Voici le code le plus simple pour afficher un message en Lua :

```lua
print("Hello World !")
```

C'est tout ! Une seule ligne de code suffit.

---

## Décomposition du code

Analysons ensemble ce que fait cette ligne de code :

### La fonction `print()`

```lua
print()
```

C'est une **fonction** qui permet d'**imprimer** ou **afficher** un texte dans notre terminal (la console où s'exécute le programme).

Cette fonction prend un **paramètre** : c'est la valeur qu'on lui donne entre les parenthèses.

### La chaîne de caractères

```lua
"Hello World !"
```

C'est un **string** (chaîne de caractères en français). Elle représente le texte qu'on veut afficher.

Les guillemets `" "` permettent d'indiquer à Lua que ce qui se trouve à l'intérieur est du texte, et non du code.

**Résumé :** Le paramètre qu'on donne à `print()` est notre texte à afficher.

---

## Lançons notre programme !

Maintenant que tu comprends le code, il est temps de l'exécuter !

### Étapes pour lancer le programme :

1. **Crée un fichier** nommé `helloworld.lua`
2. **Écris le code** dedans :
   ```lua
   print("Hello World !")
   ```
3. **Ouvre ton terminal** dans le dossier où se trouve ton fichier
4. **Lance le programme** avec la commande :
   ```bash
   lua helloworld.lua
   ```

Tu devrais voir s'afficher :
```
Hello World !
```

**Félicitations !** Tu viens d'exécuter ton premier programme en Lua !

---

## Pour aller plus loin

Maintenant que tu sais afficher du texte, essaie de modifier le message :

```lua
print("Bonjour tout le monde !")
print("Je m'appelle [Ton prénom]")
print("Bienvenue dans mon premier programme Lua")
```

Tu peux utiliser plusieurs `print()` à la suite pour afficher plusieurs lignes !

**Résultat :**
```
Bonjour tout le monde !
Je m'appelle Noah
Bienvenue dans mon premier programme Lua
```

---

## Points clés à retenir

- `print()` permet d'afficher du texte dans le terminal
- Les **chaînes de caractères** (texte) se mettent entre guillemets `" "`
- Chaque instruction en Lua se termine naturellement (pas besoin de point-virgule)
- On peut utiliser `print()` autant de fois qu'on veut dans un programme

---

## Prochaine étape

Maintenant que tu sais afficher du texte, passons à la création de **variables** pour stocker des informations !

**Rendez-vous dans le chapitre suivant : [Les Variables](02_variables.md)**
