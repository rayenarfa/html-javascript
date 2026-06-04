# Révision examen — HTML & JavaScript

Résumé de tout ce que tu as pratiqué dans ce dossier. **L’examen ne couvre pas le CSS** — les fichiers `html+css/` servent surtout pour la structure HTML5 (balises sémantiques).

---

## Table des matières

1. [Structure d’une page HTML](#1-structure-dune-page-html)
2. [Texte et titres](#2-texte-et-titres)
3. [Listes](#3-listes)
4. [Liens et ancres](#4-liens-et-ancres)
5. [Images](#5-images)
6. [Formulaires HTML](#6-formulaires-html)
7. [Tableaux](#7-tableaux)
8. [HTML5 sémantique](#8-html5-sémantique)
9. [JavaScript — bases](#9-javascript--bases)
10. [JavaScript — entrée / sortie](#10-javascript--entrée--sortie)
11. [JavaScript — manipulation des formulaires](#11-javascript--manipulation-des-formulaires)
12. [JavaScript — gestionnaires d’événements](#12-javascript--gestionnaires-dévénements)
13. [Aide-mémoire rapide](#13-aide-mémoire-rapide)

---

## 1. Structure d’une page HTML

### À retenir

| Élément | Rôle |
|--------|------|
| `<!DOCTYPE html>` | Déclare une page HTML5 |
| `<html lang="fr">` | Racine ; `lang` = langue de la page |
| `<head>` | Métadonnées (non visibles) |
| `<body>` | Contenu visible |

Dans `<head>` :

```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Titre de l'onglet</title>
```

- **`charset`** : accents et caractères spéciaux (français).
- **`viewport`** : adaptation mobile.
- **`title`** : texte de l’onglet du navigateur.

### Exercices

| Fichier | Contenu |
|---------|---------|
| `tp1.html` | Page simple sans DOCTYPE |
| `tp2ex1.html`, `tp2ex2.html` | DOCTYPE + `lang="fr"` + charset |
| `tp2ex3.html`, `tp2ex4.html` | + `viewport` |

---

## 2. Texte et titres

### Balises

| Balise | Usage |
|--------|--------|
| `<h1>` … `<h6>` | Titres (1 = plus grand) |
| `<p>` | Paragraphe |
| `<br>` | Saut de ligne |
| `<hr>` | Ligne horizontale ; attribut `width="60%"` possible |
| `<b>` | Texte en gras |
| `<sub>` | Indice (ex. X<sub>2</sub>) |
| `<center>` | Centrage (ancien, mais vu dans tes TP) |

Attributs de présentation (HTML ancien, présents dans tes fichiers) :

- `align="center"` / `"left"` / `"right"` sur `<h2>`, `<h4>`, `<hr>`, `<td>`.

### Exercices

| Fichier | Contenu |
|---------|---------|
| `ex3.html` | Formules math avec `<b>`, `<sub>`, `<center>` |
| `ex5.html` | `<h4 align="right/center/left">` |
| `tp1.html` | `<h2>`, `<h3>`, `<p>`, `<br>`, `<hr>` |

---

## 3. Listes

### Types

| Balise | Type | Numérotation |
|--------|------|----------------|
| `<ul>` | Liste à puces | Non |
| `<ol>` | Liste numérotée | Oui |
| `<li>` | Élément de liste | — |

### Listes imbriquées

Une `<ol>` peut contenir une `<ul>` (et l’inverse) :

```html
<ol>
  <li>Catégorie
    <ul>
      <li>Sous-élément</li>
    </ul>
  </li>
</ol>
```

### Attribut `type` sur `<ul>` (vu dans `ex2.html`)

| Valeur | Puce |
|--------|------|
| `disc` | Plein (défaut) |
| `circle` | Cercle vide |
| `square` | Carré |

### Exercices

| Fichier | Contenu |
|---------|---------|
| `ex2.html` | `ul`, `ol` imbriqué, `type="disc/circle/square"` |
| `tp1.html` | `ol` (menu) + `ul` (sites) |
| `tp2ex1.html` | `ol` > `ul` + liens |

---

## 4. Liens et ancres

### Lien externe

```html
<a href="https://www.google.com">Texte du lien</a>
```

**Important :** `href` doit souvent commencer par `http://` ou `https://`. Sinon le navigateur cherche une page locale.

### Lien interne (ancre sur la même page)

1. Définir un **id** sur la cible : `<h3 id="coordonnees">`
2. Lier avec **#** + id : `<a href="#coordonnees">Mes coordonnées</a>`

### Lien e-mail

```html
<a href="mailto:test@gmail.com">Nom Prénom</a>
```

Ouvre le client mail avec l’adresse préremplie.

### Navigation aller-retour (plan ↔ chapitre)

- Plan → contenu : `<a href="#intro">`
- Contenu → plan : `<a href="#plan1">` avec `<li id="plan1">` dans le sommaire.

### Exercices

| Fichier | Contenu |
|---------|---------|
| `tp1.html` | Ancres `#coordonnes`, `#cv`, `#loisirs` ; `mailto:` ; liens externes |
| `tp2ex3.html` | Ancres `#intro`, `#chap1`, `#chap2` |
| `tp2ex4.html` | Liens bidirectionnels plan ↔ sections |

---

## 5. Images

```html
<img src="chemin/image.jpg" alt="description" width="20%">
```

| Attribut | Rôle |
|----------|------|
| `src` | Chemin ou URL de l’image |
| `alt` | Texte si l’image ne charge pas (accessibilité) |
| `width` | Largeur (`%` ou pixels) |

### Exercices

| Fichier | Contenu |
|---------|---------|
| `tp2ex5.html` | `<img>` + lien dans un `<li>` |
| `html+css/photo.html` | `<figure>` + `<img>` (structure sémantique) |

---

## 6. Formulaires HTML

### Structure de base

```html
<form name="monForm" id="formLogin">
  <label>Entier :</label>
  <input type="text" name="zoneTexte" id="login">
  <button type="button">Cliquer</button>
  <button type="submit">Envoyer</button>
</form>
```

### Types d’`<input>` vus dans tes TP

| `type` | Usage |
|--------|--------|
| `text` | Texte libre |
| `password` | Mot de passe masqué |
| `number` | Nombre |
| `radio` | Un seul choix parmi plusieurs (même `name`) |
| `checkbox` | Cases à cocher multiples |
| `time` | Heure |

### Boutons radio

```html
<input type="radio" name="choix" value="Option 1"> Option 1
<input type="radio" name="choix" value="Option 2"> Option 2
```

Même **`name`** = un seul choix possible.

### Liste déroulante `<select>`

```html
<select id="musique">
  <option value="">-- Sélectionnez --</option>
  <option value="Jazz">Jazz</option>
</select>
```

- **`value`** : valeur lue en JavaScript.
- **`selected`** : option par défaut.

### Validation HTML5 (`022426.HTML`)

| Attribut | Effet |
|----------|--------|
| `required` | Champ obligatoire |
| `pattern="[ a-zA-Z]*"` | Expression régulière (ici : lettres et espaces) |
| `readonly` | Lecture seule (pas modifiable par l’utilisateur) |

États CSS liés (concept utile même sans CSS à l’examen) : `:required`, `:optional`, `:invalid`.

### Exercices

| Fichier | Contenu |
|---------|---------|
| `022426.HTML` | `required`, `pattern`, `type="time"` |
| `tp4 js/.../ex1` (formulaires) | Radio |
| `tp4 js/.../ex2` | Select + `onchange` |
| `tp4 js/.../ex4` | Login + `submit` |

---

## 7. Tableaux

```html
<table border="1">
  <tr>
    <th>Login</th>
    <th>Password</th>
  </tr>
  <tr>
    <td><input type="text"></td>
    <td><input type="password"></td>
  </tr>
  <tr>
    <td colspan="2" align="center">...</td>
  </tr>
</table>
```

| Balise | Rôle |
|--------|------|
| `<table>` | Tableau |
| `<tr>` | Ligne |
| `<th>` | En-tête de colonne |
| `<td>` | Cellule |
| `colspan="2"` | Fusionne 2 colonnes |
| `border="1"` | Bordure visible |

### Exercice

| Fichier | Contenu |
|---------|---------|
| `tp4 js/MANIPULATION DES FORMULAIRES/ex4.html` | Formulaire login dans un tableau |

---

## 8. HTML5 sémantique

Balises pour structurer le sens (pas seulement l’apparence) :

| Balise | Rôle |
|--------|------|
| `<header>` | En-tête de page ou de section |
| `<nav>` | Menu de navigation |
| `<main>` | Contenu principal |
| `<article>` | Bloc autonome (article, produit…) |
| `<section>` | Section thématique |
| `<aside>` | Contenu latéral |
| `<footer>` | Pied de page |
| `<figure>` | Image + légende possible |

Autres éléments utiles :

- `<button>` : bouton (ex. « Add to cart »)
- `&copy;` : symbole ©

### Exercices (structure HTML uniquement)

| Fichier | Contenu |
|---------|---------|
| `html+css/2.html` | `header`, `main`, `aside`, `article`, `footer` |
| `html+css/photo.html` | `header`, `nav`, `main`, `article`, `figure`, `footer` |
| `html+css/tp6/ex2.html` | `header`, `main`, `article`, `button`, `img` |
| `html+css/tp6/ex3.html` | `header`, `nav`, `section`, `footer` |

---

# JavaScript

Le JavaScript s’écrit dans `<script>` … `</script>`, en bas du `<body>` ou dans le `<head>`.

---

## 9. JavaScript — bases

### Syntaxe

```javascript
let variable = "valeur";        // variable modifiable
const element = document.getElementById("id");  // constante

function nomFonction() {
  // code
}
```

### Accéder au DOM (Document Object Model)

| Méthode | Retourne |
|---------|----------|
| `document.getElementById("id")` | Un élément par son `id` |
| `document.getElementsByName("nom")` | Liste d’éléments (ex. radios) |
| `document.monForm.zoneTexte` | Champ par `name` du formulaire |

### Propriétés courantes

| Propriété | Sur | Usage |
|-----------|-----|--------|
| `.value` | input, select | Lire / écrire la valeur |
| `.checked` | radio, checkbox | `true` si coché |
| `.src` | `<img>` | Changer l’image |
| `.textContent` | tout élément | Texte affiché |
| `document.location.href` | page | Changer d’URL (navigation) |

### Boucle `for`

```javascript
for (let i = 0; i < choix.length; i++) {
  if (choix[i].checked) { ... }
}
```

### Conditions

```javascript
if (condition) {
} else if (autre) {
} else {
}

// Comparaisons : ===  !==  &&  ||
if (c1.checked && c2.checked && !c3.checked) { ... }
```

---

## 10. JavaScript — entrée / sortie

**Dossier :** `tp4 js/ENTREE SORTIE/`

### `alert(message)`

Affiche une boîte de dialogue avec un message.

```javascript
alert("Bonjour");
alert("L'année saisie est : " + annee);
```

### `prompt(message)`

Demande une saisie à l’utilisateur.

- Retourne la **chaîne saisie**.
- Retourne **`null`** si l’utilisateur clique sur Annuler.

```javascript
let annee = prompt("Veuillez introduire l'année :");
if (annee !== null) {
  alert("L'année saisie est : " + annee);
} else {
  alert("Vous avez annulé la saisie.");
}
```

### Modifier un champ de formulaire

```javascript
function afficher() {
  document.monForm.zoneTexte.value = "ESIP";
}
```

Déclenchement : `onclick="afficher()"` sur un bouton.

### Lire un champ + calcul

```javascript
let nombre = document.getElementById("nombre").value;
if (nombre === "") {
  alert("Veuillez saisir un nombre !");
  return;
}
let carre = nombre * nombre;
document.getElementById("resultat").value = carre;
```

**Note :** `.value` d’un input est une **chaîne** ; `*` la convertit souvent en nombre. Pour un contrôle strict : `Number(nombre)` ou `parseInt(nombre)`.

### Résumé exercices

| Ex. | Fichier | Concepts |
|-----|---------|----------|
| 1 | `ex1.html` | `alert()` |
| 2 | `ex2.html` | `form`, `onclick`, modifier `.value` |
| 3 | `ex3.html` | `prompt()`, `null`, `let` |
| 4 | `ex4.html` | `getElementById`, calcul, `readonly`, validation vide |

---

## 11. JavaScript — manipulation des formulaires

**Dossier :** `tp4 js/MANIPULATION DES FORMULAIRES/`

### Boutons radio — lire le choix

```javascript
let choix = document.getElementsByName("choix");
let selection = null;
for (let i = 0; i < choix.length; i++) {
  if (choix[i].checked) {
    selection = choix[i].value;
    break;
  }
}
if (selection) {
  alert("Votre choix est : " + selection);
} else {
  alert("Veuillez sélectionner une option !");
}
```

### `<select>` — `onchange` ou `addEventListener`

```javascript
// Méthode 1 : attribut HTML
<select id="musique" onchange="afficherChoix()">

// Méthode 2 : JavaScript
select.addEventListener("change", function () {
  image.src = select.value;
});
```

```javascript
let choix = document.getElementById("musique").value;
if (choix !== "") {
  alert("Vous avez choisi : " + choix);
}
```

### Changer l’image selon la liste

```javascript
const select = document.getElementById("listeImages");
const image = document.getElementById("imageAffichee");
select.addEventListener("change", function () {
  image.src = select.value;  // value = nom du fichier image
});
```

### Formulaire — empêcher l’envoi + validation

```javascript
form.addEventListener("submit", function(event) {
  event.preventDefault();  // empêche le rechargement de la page

  if (login.value === "" && password.value === "") {
    alert("Veuillez saisir le login et le mot de passe !");
  } else if (login.value === "") {
    alert("Veuillez saisir le login !");
  } else if (password.value === "") {
    alert("Veuillez saisir le mot de passe !");
  } else {
    alert("Connexion réussie !");
  }
});
```

### Résumé exercices

| Ex. | Fichier | Concepts |
|-----|---------|----------|
| 1 | `ex1.html` | `getElementsByName`, `.checked`, `.value`, boucle `for` |
| 2 | `ex2.html` | `<select>`, `.value`, `onchange` |
| 3 | `ex3.html` | `addEventListener("change")`, modifier `img.src` |
| 4 | `ex4.html` | `submit`, `preventDefault()`, validation champs vides |

---

## 12. JavaScript — gestionnaires d’événements

**Dossier :** `tp4 js/GESTIONNAIRES EVENTS/`

### Deux façons d’attacher un événement

```html
<!-- Inline (dans le HTML) -->
<button onclick="calculerCarre()">Carré</button>

<!-- Recommandé : en JavaScript -->
btn.addEventListener("click", function() {
  document.location.href = "fichier.htm";
});
```

### Événements vus dans tes TP

| Événement | Quand | Exemple |
|-----------|--------|---------|
| `click` | Clic souris | Bouton, lien, « Corriger » |
| `change` | Valeur d’un select change | Liste musique / images |
| `submit` | Envoi du formulaire | Login |
| `load` | Page entièrement chargée | `window.addEventListener("load", ...)` |
| `mouseover` | Souris sur l’élément | Lien « Survolez-moi » |

### Navigation vers une autre page

```javascript
document.location.href = "fichier.htm";
```

### Date et heure

```javascript
const maintenant = new Date();
dateElement.textContent = maintenant.toLocaleString();
```

- **`new Date()`** : date/heure actuelles.
- **`.toLocaleString()`** : format lisible selon la locale.
- **`.textContent`** : insérer du texte dans un élément HTML.

### Message au chargement de la page

```javascript
window.addEventListener("load", function() {
  alert("Bienvenue à cette page");
});
```

### Checkboxes (QCM)

```javascript
if (c1.checked && c2.checked && c4.checked && !c3.checked) {
  alert("Bonne réponse !");
} else {
  alert("Mauvaise réponse !");
}
```

- **`.checked`** : `true` si la case est cochée.
- **`&&`** : ET logique — toutes les conditions doivent être vraies.
- **`!c3.checked`** : case 3 ne doit **pas** être cochée.

### Résumé exercices

| Ex. | Fichier | Concepts |
|-----|---------|----------|
| 1 | `ex1.html` | `addEventListener("click")`, `document.location.href` |
| 2 | `ex2.html` | `new Date()`, `toLocaleString()`, `textContent` |
| 3 | `ex3.html` | `window`, événement `load` |
| 4 | `ex4.html` | `mouseover` sur un lien `<a>` |
| 5 | `ex5.html` | checkboxes, `.checked`, logique `&&` / `!` |

---

## 13. Aide-mémoire rapide

### HTML — pièges fréquents à l’examen

1. Ancre interne : **`href="#id"`** + **`id="id"`** sur la cible.
2. Liens externes : préférer **`https://...`**.
3. Radio : même **`name`**, valeurs différentes dans **`value`**.
4. **`required`** et **`pattern`** valident côté navigateur avant JavaScript.
5. **`colspan`** fusionne des colonnes ; **`rowspan`** fusionne des lignes (pas vu mais utile).

### JavaScript — pièges fréquents

1. **`getElementById`** → un seul élément ; **`getElementsByName`** → tableau.
2. **`prompt()`** annulé → **`null`**, pas une chaîne vide.
3. Formulaire : **`event.preventDefault()`** pour ne pas recharger la page.
4. Vérifier **`""`** avant un calcul (`ex4 entrée/sortie`).
5. Radio non sélectionné : boucler et tester **`.checked`**.

### Carte des dossiers

```
Racine/
├── tp1.html              → Page perso, ancres, listes, mailto
├── tp2ex*.html           → Listes imbriquées, ancres, images
├── ex2.html, ex3.html    → Listes, formules math
├── ex5.html              → align sur titres
├── 022426.HTML           → Validation formulaire (required, pattern)
├── html+css/             → HTML5 sémantique (pas CSS à l'examen)
└── tp4 js/
    ├── ENTREE SORTIE/    → alert, prompt, getElementById, calcul
    ├── MANIPULATION DES FORMULAIRES/ → radio, select, submit, images
    └── GESTIONNAIRES EVENTS/ → addEventListener, Date, load, QCM
```

---

Bonne chance pour l’examen.
