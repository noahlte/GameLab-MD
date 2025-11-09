# 03. Les Conditions en Lua

## Introduction : Lire une entrée utilisateur

Avant de parler des conditions, apprenons à **lire** ce que l'utilisateur tape dans le terminal.

### La fonction `io.read()`

```lua
print("Entrez votre nom : ")
local nom = io.read()
```

- `io.read()` lit ce que l'utilisateur tape dans le terminal
- Le résultat est toujours du **texte** (string)

### Convertir en nombre avec `tonumber()`

```lua
print("Entrez votre âge : ")
local age = tonumber(io.read())
```

- `tonumber()` transforme le texte en nombre
- Utile pour faire des calculs ou des comparaisons

---

## Les Conditions - C'est quoi ?

Une **condition** permet de vérifier si quelque chose est **vrai** ou **faux**.

Si la condition est validée, on réalise quelque chose.

### Syntaxe de base

```lua
if condition then
    -- code à exécuter
end
```

**En français :**
```
Si ... alors
    Ce qui se passe...
Fin
```

### Exemple simple

```lua
local age = 18

if age >= 18 then
    print("Tu es majeur !")
end
```

Si `age` est supérieur ou égal à 18, alors on affiche le message.

---

## Les opérateurs de comparaison

Pour créer des conditions, on utilise des **opérateurs de comparaison** :

| Opérateur | Signification | Exemple |
|-----------|---------------|---------|
| `==` | égal à | `age == 10` |
| `~=` | différent de | `age ~= 10` |
| `>` | plus grand que | `age > 18` |
| `<` | plus petit que | `age < 13` |
| `>=` | plus grand ou égal à | `age >= 18` |
| `<=` | plus petit ou égal à | `age <= 12` |

### Exemples

```lua
local age = 10

if age == 10 then
    print("Tu as exactement 10 ans !")
end

if age < 13 then
    print("Tu es encore un enfant")
end

if age > 12 then
    print("Tu es un adolescent ou un adulte")
end
```

---

## IF ... ELSE (Si ... Sinon)

Maintenant, on aimerait afficher quelque chose quand la condition est **fausse**.

Pour ça, on utilise `else` qui veut dire **SINON**.

### Syntaxe

```lua
if condition then
    -- code si la condition est vraie
else
    -- code si la condition est fausse
end
```

### Exemple

```lua
local age = 15

if age >= 18 then
    print("Tu es majeur !")
else
    print("Tu es mineur !")
end
```

**Résultat :** `Tu es mineur !`

---

## IF ... ELSEIF ... ELSE

`elseif` permet de tester **plusieurs conditions** différentes.

On peut en mettre **autant qu'on veut** !

### Syntaxe

```lua
if condition1 then
    -- code si condition1 est vraie
elseif condition2 then
    -- code si condition2 est vraie
elseif condition3 then
    -- code si condition3 est vraie
else
    -- code si aucune condition n'est vraie
end
```

### Exemple : Catégories d'âge

```lua
local age = 15

if age < 6 then
    print("Tu es un bébé !")
elseif age < 12 then
    print("Tu es un enfant !")
elseif age < 18 then
    print("Tu es un adolescent !")
else
    print("Tu es un adulte !")
end
```

**Résultat :** `Tu es un adolescent !`

---

## Vérifier l'égalité avec ==

Pour vérifier si deux valeurs sont **identiques**, on utilise `==`.

### Exemple : Mot de passe

```lua
local motDePasse = "secret123"

print("Entrez le mot de passe : ")
local tentative = io.read()

if tentative == motDePasse then
    print("Accès autorisé !")
else
    print("Mot de passe incorrect !")
end
```

---

## Vérifier vrai ou faux (Boolean)

On peut vérifier si une variable est `true` (vrai) ou `false` (faux).

### Avec `not`

```lua
local vivant = false

if not vivant then
    print("Le personnage est mort !")
end
```

`not` inverse la valeur booléenne :
- `not true` devient `false`
- `not false` devient `true`

### Vérifier directement

```lua
local aFaim = true

if aFaim then
    print("Il est temps de manger !")
end
```

Pas besoin d'écrire `if aFaim == true`, on peut juste écrire `if aFaim`.

---

## Combiner des conditions

On peut combiner plusieurs conditions avec des **opérateurs logiques** :

### AND (et)

Les **deux** conditions doivent être vraies.

```lua
if condition1 and condition2 then
    -- code
end
```

**Exemple :**

```lua
local age = 15
local argent = 25
local prixJeu = 20

if age >= 12 and argent >= prixJeu then
    print("Tu peux acheter le jeu !")
else
    print("Tu ne peux pas acheter le jeu...")
end
```

### OR (ou)

**Au moins une** condition doit être vraie.

```lua
if condition1 or condition2 then
    -- code
end
```

**Exemple :**

```lua
local weekEnd = true
local vacances = false

if weekEnd or vacances then
    print("Tu peux jouer toute la journée !")
else
    print("Il faut aller à l'école...")
end
```

### Combiner plusieurs conditions

```lua
local niveau = 5
local score = 1200
local boss = true

if niveau >= 5 and score > 1000 and boss then
    print("FÉLICITATIONS ! Tu as battu le boss !")
elseif niveau >= 5 and score > 1000 then
    print("Tu peux affronter le boss !")
else
    print("Continue à jouer pour débloquer le boss...")
end
```

---

## Tableau récapitulatif

| Opérateur | Signification | Exemple |
|-----------|---------------|---------|
| `and` | ET (les deux doivent être vrais) | `age >= 18 and permis == true` |
| `or` | OU (au moins un doit être vrai) | `weekEnd or vacances` |
| `not` | NON (inverse la valeur) | `not vivant` |

---

## Exercice : Le contrôle d'accès au parc d'attractions

Crée un programme qui vérifie si on peut entrer dans une attraction.

### Règles :

- Il faut avoir **au moins 120 cm** de taille
- **ET** avoir **au moins 8 ans**
- **OU** être accompagné d'un adulte

### Consignes :

Demande à l'utilisateur :
1. Sa taille (en cm)
2. Son âge
3. S'il est accompagné d'un adulte (oui/non)

Ensuite, affiche s'il peut monter dans l'attraction ou non.

### Aide

```lua
print("Quelle est ta taille en cm ? ")
local taille = tonumber(io.read())

-- À toi de continuer !
```

**Astuce :** Utilise `string.lower()` pour convertir "OuI" en "oui"

<details>
<summary> Voir la correction</summary>

```lua
print("Entrez votre taille (en cm) : ")
local taille = tonumber(io.read())

print("Entrez votre âge : ")
local age = tonumber(io.read())

print("Êtes-vous accompagné d'un adulte ? (oui/non) : ")
local accompagneAdulte = string.lower(io.read())

if taille >= 120 and (age >= 8 or accompagneAdulte == "oui") then
    print("Vous pouvez rentrer dans l'attraction.")
else
    print("Vous ne pouvez pas rentrer dans l'attraction !")
end
```

**Explication :**
- `taille >= 120` : doit avoir au moins 120 cm
- `and` : ET
- `(age >= 8 or accompagneAdulte == "oui")` : avoir 8 ans OU être accompagné
- Les parenthèses sont importantes pour grouper les conditions !

</details>

---

## Points clés à retenir

- `if ... then ... end` permet de tester une condition
- `else` exécute du code si la condition est fausse
- `elseif` permet de tester plusieurs conditions
- Opérateurs de comparaison : `==`, `~=`, `>`, `<`, `>=`, `<=`
- Opérateurs logiques : `and`, `or`, `not`
- `io.read()` lit l'entrée utilisateur (retourne du texte)
- `tonumber()` convertit du texte en nombre
- `string.lower()` convertit du texte en minuscules

---

## Prochaine étape

Maintenant que tu sais prendre des décisions dans ton code, passons aux **boucles** pour répéter des actions !

**Rendez-vous dans le chapitre suivant : [Les Boucles](04_boucles.md)**
