# Test — HTML & JavaScript

Petits exercices avec **question** puis **correction en code**. Couvre tout le programme (sans CSS).

---

## Partie 1 — Structure HTML

---

### Ex. 1.1 — Squelette minimal HTML5

**Question :** Écris le squelette d’une page HTML5 en français avec charset UTF-8 et le titre « Mon examen ».

**Correction :**

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Mon examen</title>
</head>
<body>

</body>
</html>
```

---

### Ex. 1.2 — Viewport mobile

**Question :** Ajoute la balise meta pour que la page s’adapte aux écrans mobiles.

**Correction :**

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

*(à placer dans `<head>`)*

---

### Ex. 1.3 — Où va le contenu visible ?

**Question :** Dans quelle balise place-t-on tout ce que l’utilisateur voit à l’écran ?

**Correction :**

```html
<body>
    <h1>Bonjour</h1>
    <p>Contenu visible ici.</p>
</body>
```

---

## Partie 2 — Texte et titres

---

### Ex. 2.1 — Titres et paragraphe

**Question :** Crée un titre principal « ESIP », un sous-titre « Gafsa », puis un paragraphe sur deux lignes avec un saut de ligne.

**Correction :**

```html
<h1>ESIP</h1>
<h3>Gafsa</h3>
<p>Première ligne<br>Deuxième ligne</p>
```

---

### Ex. 2.2 — Ligne horizontale

**Question :** Insère une ligne de séparation à 60% de la largeur entre deux sections.

**Correction :**

```html
<h3>Section 1</h3>
<p>Texte...</p>
<hr width="60%">
<h3>Section 2</h3>
```

---

### Ex. 2.3 — Formule avec indice

**Question :** Affiche centré : **X₂** = X₁ cos(a) (X₂ et X₁ en indice, X₂ en gras).

**Correction :**

```html
<center>
    <b>X<sub>2</sub></b> = X<sub>1</sub> cos(a)
</center>
```

---

### Ex. 2.4 — Alignement

**Question :** Trois titres `<h4>` : un à droite, un au centre, un à gauche.

**Correction :**

```html
<h4 align="right">À droite</h4>
<h4 align="center">Au centre</h4>
<h4 align="left">À gauche</h4>
```

---

## Partie 3 — Listes

---

### Ex. 3.1 — Liste à puces

**Question :** Liste à puces avec : Adresse ESIP, Tél, E-mail.

**Correction :**

```html
<ul>
    <li>Adresse : ESIP Gafsa</li>
    <li>Tel : 76 221 111</li>
    <li>E-mail : esip@esip.tn</li>
</ul>
```

---

### Ex. 3.2 — Liste numérotée

**Question :** Menu numéroté : Accueil, Contact, À propos.

**Correction :**

```html
<ol>
    <li>Accueil</li>
    <li>Contact</li>
    <li>À propos</li>
</ol>
```

---

### Ex. 3.3 — Liste imbriquée

**Question :** Liste numérotée « École » avec sous-liste à puces : 1ère année Tozeur, 2e année Gafsa.

**Correction :**

```html
<ol>
    <li>École
        <ul>
            <li>1ère : Tozeur</li>
            <li>2e : Gafsa</li>
        </ul>
    </li>
</ol>
```

---

### Ex. 3.4 — Type de puces

**Question :** Même liste avec puces `disc`, puis `circle`, puis `square` (3 listes séparées).

**Correction :**

```html
<ul type="disc"><li>Item A</li></ul>
<ul type="circle"><li>Item B</li></ul>
<ul type="square"><li>Item C</li></ul>
```

---

### Ex. 3.5 — Liens dans une liste imbriquée

**Question :** Liste numérotée « Constructeurs » contenant une liste à puces avec liens vers Apple et IBM.

**Correction :**

```html
<ol>
    <li>Constructeurs
        <ul>
            <li><a href="https://www.apple.com">Apple</a></li>
            <li><a href="https://www.ibm.com">IBM</a></li>
        </ul>
    </li>
</ol>
```

---

## Partie 4 — Liens et ancres

---

### Ex. 4.1 — Lien externe

**Question :** Lien cliquable « Google » vers https://www.google.com.

**Correction :**

```html
<a href="https://www.google.com">Google</a>
```

---

### Ex. 4.2 — Ancre interne (aller vers une section)

**Question :** Menu avec 2 liens vers les sections `#contact` et `#cv`. Chaque section a un `<h3>` avec le bon `id`.

**Correction :**

```html
<ol>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#cv">CV</a></li>
</ol>
<hr>
<h3 id="contact">Contact</h3>
<p>Mon adresse...</p>
<hr>
<h3 id="cv">Mon CV</h3>
<p>Mon parcours...</p>
```

---

### Ex. 4.3 — Retour au plan

**Question :** Dans le sommaire, le chapitre a `id="plan1"`. Dans le contenu, un lien « Retour au plan » pointe vers ce sommaire.

**Correction :**

```html
<!-- Sommaire -->
<li id="plan1"><a href="#intro">Introduction</a></li>

<!-- Contenu -->
<li id="intro"><a href="#plan1">Introduction</a></li>
<p>Texte du chapitre...</p>
```

---

### Ex. 4.4 — Lien e-mail

**Question :** Lien qui ouvre un mail à `etudiant@esip.tn` avec le texte « Me contacter ».

**Correction :**

```html
<a href="mailto:etudiant@esip.tn">Me contacter</a>
```

---

## Partie 5 — Images

---

### Ex. 5.1 — Image simple

**Question :** Affiche `logo.png` avec texte alternatif « Logo ESIP » et largeur 30%.

**Correction :**

```html
<img src="logo.png" alt="Logo ESIP" width="30%">
```

---

### Ex. 5.2 — Image + lien dans une liste

**Question :** Dans un `<li>`, affiche une petite image puis un lien « Lycos ».

**Correction :**

```html
<li>
    <img src="lycos.png" alt="logo Lycos" width="20%">
    <a href="https://www.lycos.com">Lycos</a>
</li>
```

---

## Partie 6 — Formulaires HTML

---

### Ex. 6.1 — Formulaire texte + bouton

**Question :** Formulaire nommé `monForm` avec un champ texte `zoneTexte` et un bouton type `button` (pas submit).

**Correction :**

```html
<form name="monForm">
    <input type="text" name="zoneTexte"><br><br>
    <button type="button">Cliquer</button>
</form>
```

---

### Ex. 6.2 — Boutons radio

**Question :** 3 options radio (même groupe `choix`) : A, B, C avec les values « Option A », etc.

**Correction :**

```html
<input type="radio" name="choix" value="Option A"> A<br>
<input type="radio" name="choix" value="Option B"> B<br>
<input type="radio" name="choix" value="Option C"> C<br>
```

---

### Ex. 6.3 — Cases à cocher

**Question :** 4 checkboxes avec les id `c1`, `c2`, `c3`, `c4`.

**Correction :**

```html
<input type="checkbox" id="c1"> 1<br>
<input type="checkbox" id="c2"> 2<br>
<input type="checkbox" id="c3"> 3<br>
<input type="checkbox" id="c4"> 4<br>
```

---

### Ex. 6.4 — Liste déroulante

**Question :** Select `id="musique"` avec option vide par défaut et Jazz, Rock.

**Correction :**

```html
<select id="musique">
    <option value="">-- Choisir --</option>
    <option value="Jazz">Jazz</option>
    <option value="Rock">Rock</option>
</select>
```

---

### Ex. 6.5 — Champ obligatoire et pattern

**Question :** Champ texte obligatoire ; un autre qui n’accepte que des lettres (et espaces) via `pattern`.

**Correction :**

```html
<input type="text" required><br>
<input type="text" pattern="[ a-zA-Z]*" value="lettres">
```

---

### Ex. 6.6 — Autres types d’input

**Question :** Un champ `number`, un `password`, un `time` obligatoire, un champ `readonly` pour le résultat.

**Correction :**

```html
<input type="number" id="nombre"><br>
<input type="password" id="mdp"><br>
<input type="time" value="08:00" required><br>
<input type="text" id="resultat" readonly>
```

---

### Ex. 6.7 — Label

**Question :** Associe le label « Entier : » au champ nombre `id="nombre"`.

**Correction :**

```html
<label for="nombre">Entier :</label><br>
<input type="number" id="nombre">
```

---

## Partie 7 — Tableaux

---

### Ex. 7.1 — Tableau login

**Question :** Tableau bordure 1 : en-têtes Login / Password, une ligne avec 2 inputs, une ligne avec un bouton Login centré sur 2 colonnes.

**Correction :**

```html
<table border="1">
    <tr>
        <th>Login</th>
        <th>Password</th>
    </tr>
    <tr>
        <td><input type="text" id="login"></td>
        <td><input type="password" id="password"></td>
    </tr>
    <tr>
        <td colspan="2" align="center">
            <button type="submit">Login</button>
        </td>
    </tr>
</table>
```

---

## Partie 8 — HTML5 sémantique

---

### Ex. 8.1 — Structure de page

**Question :** Page avec `header`, `nav`, `main`, `footer`. Dans `main`, un `article` avec titre et paragraphe.

**Correction :**

```html
<header>
    <h1>Mon site</h1>
    <nav>
        <a href="#">Accueil</a>
    </nav>
</header>
<main>
    <article>
        <h2>Article</h2>
        <p>Contenu...</p>
    </article>
</main>
<footer>
    <p>&copy; 2026 ESIP</p>
</footer>
```

---

### Ex. 8.2 — Layout avec aside

**Question :** `main` contient un `aside` (menu) et un `article` (contenu).

**Correction :**

```html
<main>
    <aside>
        <ul>
            <li>Menu 1</li>
            <li>Menu 2</li>
        </ul>
    </aside>
    <article>
        <h2>Titre</h2>
        <p>Texte principal...</p>
    </article>
</main>
```

---

### Ex. 8.3 — Figure et section

**Question :** Une `section` avec 2 `article`. Le premier contient un `figure` avec image.

**Correction :**

```html
<section>
    <article>
        <h2>Photo</h2>
        <figure>
            <img src="photo.png" alt="Description">
        </figure>
    </article>
    <article>
        <h2>Texte</h2>
        <p>Paragraphe...</p>
    </article>
</section>
```

---

## Partie 9 — JavaScript : alert & prompt

---

### Ex. 9.1 — Alert au chargement

**Question :** Au chargement de la page, affiche « Bonjour ».

**Correction :**

```html
<script>
    alert("Bonjour");
</script>
```

---

### Ex. 9.2 — Prompt année

**Question :** Demande l’année. Si l’utilisateur annule, alerte « Annulé ». Sinon affiche l’année saisie.

**Correction :**

```html
<script>
    let annee = prompt("Entrez l'année :");
    if (annee !== null) {
        alert("Année : " + annee);
    } else {
        alert("Annulé");
    }
</script>
```

---

## Partie 10 — JavaScript : DOM & formulaires

---

### Ex. 10.1 — Écrire dans un champ (form name)

**Question :** Fonction `afficher()` qui met « ESIP » dans `document.monForm.zoneTexte.value`. Bouton `onclick`.

**Correction :**

```html
<form name="monForm">
    <input type="text" name="zoneTexte">
    <button type="button" onclick="afficher()">Afficher</button>
</form>
<script>
    function afficher() {
        document.monForm.zoneTexte.value = "ESIP";
    }
</script>
```

---

### Ex. 10.2 — Carré d’un nombre

**Question :** Bouton « Carré » : lit `#nombre`, si vide → alerte ; sinon met le carré dans `#resultat` (readonly).

**Correction :**

```html
<input type="number" id="nombre">
<button onclick="calculerCarre()">Carré</button>
<input type="text" id="resultat" readonly>

<script>
    function calculerCarre() {
        let n = document.getElementById("nombre").value;
        if (n === "") {
            alert("Saisissez un nombre !");
            return;
        }
        document.getElementById("resultat").value = n * n;
    }
</script>
```

---

### Ex. 10.3 — Lire un radio (boucle)

**Question :** Fonction qui parcourt les radios `name="choix"` et affiche la value cochée, sinon « Aucun choix ».

**Correction :**

```html
<button onclick="afficherChoix()">Valider</button>
<script>
    function afficherChoix() {
        let choix = document.getElementsByName("choix");
        let selection = null;
        for (let i = 0; i < choix.length; i++) {
            if (choix[i].checked) {
                selection = choix[i].value;
                break;
            }
        }
        if (selection) {
            alert("Choix : " + selection);
        } else {
            alert("Aucun choix");
        }
    }
</script>
```

---

### Ex. 10.4 — Select onchange

**Question :** Quand on change le select `#musique`, si une valeur est choisie, alerte « Vous avez choisi : … ».

**Correction :**

```html
<select id="musique" onchange="afficherChoix()">
    <option value="">--</option>
    <option value="Jazz">Jazz</option>
</select>
<script>
    function afficherChoix() {
        let v = document.getElementById("musique").value;
        if (v !== "") {
            alert("Vous avez choisi : " + v);
        }
    }
</script>
```

---

### Ex. 10.5 — Changer image avec select

**Question :** Select `#listeImages` : au `change`, met à jour `src` de `#imageAffichee`.

**Correction :**

```html
<select id="listeImages">
    <option value="chat.jpg">Chat</option>
    <option value="chien.png">Chien</option>
</select>
<img id="imageAffichee" src="chat.jpg" alt="image">

<script>
    const select = document.getElementById("listeImages");
    const img = document.getElementById("imageAffichee");
    select.addEventListener("change", function () {
        img.src = select.value;
    });
</script>
```

---

### Ex. 10.6 — Formulaire submit + validation

**Question :** Form `#formLogin` : au submit, `preventDefault`. Vérifie login et password vides (messages différents) ou succès.

**Correction :**

```html
<form id="formLogin">
    <input type="text" id="login">
    <input type="password" id="password">
    <button type="submit">Login</button>
</form>
<script>
    const form = document.getElementById("formLogin");
    const login = document.getElementById("login");
    const password = document.getElementById("password");

    form.addEventListener("submit", function (event) {
        event.preventDefault();
        if (login.value === "" && password.value === "") {
            alert("Saisir login et mot de passe !");
        } else if (login.value === "") {
            alert("Saisir le login !");
        } else if (password.value === "") {
            alert("Saisir le mot de passe !");
        } else {
            alert("Connexion réussie !");
        }
    });
</script>
```

---

## Partie 11 — JavaScript : événements

---

### Ex. 11.1 — Clic → autre page

**Question :** Bouton `#btn` : au clic, va vers `page.html` avec `addEventListener`.

**Correction :**

```html
<button id="btn">Aller</button>
<script>
    document.getElementById("btn").addEventListener("click", function () {
        document.location.href = "page.html";
    });
</script>
```

---

### Ex. 11.2 — Date actuelle

**Question :** Affiche la date/heure actuelle dans `<h2 id="date">` avec `new Date()` et `toLocaleString()`.

**Correction :**

```html
<h2 id="date"></h2>
<script>
    const el = document.getElementById("date");
    el.textContent = new Date().toLocaleString();
</script>
```

---

### Ex. 11.3 — Événement load

**Question :** Quand la page est entièrement chargée, alerte « Bienvenue ».

**Correction :**

```html
<script>
    window.addEventListener("load", function () {
        alert("Bienvenue");
    });
</script>
```

---

### Ex. 11.4 — mouseover

**Question :** Lien `#lien` : au survol, alerte « Bonjour prof ».

**Correction :**

```html
<a href="#" id="lien">Survolez-moi</a>
<script>
    document.getElementById("lien").addEventListener("mouseover", function () {
        alert("Bonjour prof");
    });
</script>
```

---

### Ex. 11.5 — QCM checkboxes

**Question :** Bonne réponse si c1, c2 et c4 cochés ET c3 non coché. Bouton `#corriger` au clic.

**Correction :**

```html
<input type="checkbox" id="c1"> 1<br>
<input type="checkbox" id="c2"> 2<br>
<input type="checkbox" id="c3"> 3<br>
<input type="checkbox" id="c4"> 4<br>
<button id="corriger">Corriger</button>

<script>
    const c1 = document.getElementById("c1");
    const c2 = document.getElementById("c2");
    const c3 = document.getElementById("c3");
    const c4 = document.getElementById("c4");

    document.getElementById("corriger").addEventListener("click", function () {
        if (c1.checked && c2.checked && c4.checked && !c3.checked) {
            alert("Bonne réponse !");
        } else {
            alert("Mauvaise réponse !");
        }
    });
</script>
```

---

## Partie 12 — Exercices combinés (type examen)

---

### Ex. 12.1 — Mini page perso (HTML seul)

**Question :** Page avec titre centré, menu numéroté (3 ancres), 3 sections avec `id`, liens externes dans une liste à puces, lien mailto, `hr` entre sections.

**Correction :**

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Ma page</title>
</head>
<body>
    <h2 align="center">Nom Prénom</h2>
    <ol>
        <li><a href="#coordonnees">Coordonnées</a></li>
        <li><a href="#cv">CV</a></li>
        <li><a href="#loisirs">Loisirs</a></li>
    </ol>
    <hr>
    <h3 id="coordonnees">Coordonnées</h3>
    <p>Ville<br>Tél</p>
    <hr width="60%">
    <h3 id="cv">CV</h3>
    <p>Parcours...</p>
    <hr width="60%">
    <h3 id="loisirs">Loisirs</h3>
    <p>Sport...</p>
    <ul>
        <li><a href="https://www.esip.tn">ESIP</a></li>
    </ul>
    <p><a href="mailto:moi@mail.com">Contact</a></p>
</body>
</html>
```

---

### Ex. 12.2 — Page complète HTML + JS

**Question :** Champ nombre + bouton Carré + résultat readonly + validation vide (tout en une page).

**Correction :**

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Carré</title>
</head>
<body>
    <label>Entier :</label><br>
    <input type="number" id="nombre"><br>
    <button onclick="calculerCarre()">Carré</button><br>
    <label>Résultat :</label><br>
    <input type="text" id="resultat" readonly>

    <script>
        function calculerCarre() {
            let n = document.getElementById("nombre").value;
            if (n === "") {
                alert("Veuillez saisir un nombre !");
                return;
            }
            document.getElementById("resultat").value = n * n;
        }
    </script>
</body>
</html>
```

---

### Ex. 12.3 — Album images (HTML + JS events)

**Question :** Select 3 images + img affichée ; changement via `addEventListener("change")`.

**Correction :**

```html
<select id="listeImages">
    <option value="a.jpg">A</option>
    <option value="b.jpg" selected>B</option>
    <option value="c.jpg">C</option>
</select>
<img id="imageAffichee" src="b.jpg" alt="image">
<script>
    const s = document.getElementById("listeImages");
    const i = document.getElementById("imageAffichee");
    s.addEventListener("change", function () {
        i.src = s.value;
    });
</script>
```

---

## Checklist — Tout est couvert ?

| Thème | Exercices |
|-------|-----------|
| Structure HTML5, meta, viewport | 1.1 – 1.3 |
| Texte h, p, br, hr, b, sub, center, align | 2.1 – 2.4 |
| ul, ol, imbriqué, type | 3.1 – 3.5 |
| Liens externes, ancres, mailto, retour plan | 4.1 – 4.4 |
| img src alt width | 5.1 – 5.2 |
| form, input types, radio, checkbox, select, required, pattern, readonly, label | 6.1 – 6.7 |
| table, th, td, colspan, align | 7.1 |
| header, nav, main, article, aside, section, figure, footer | 8.1 – 8.3 |
| alert, prompt, null | 9.1 – 9.2 |
| getElementById, getElementsByName, .value, .checked, form name | 10.1 – 10.6 |
| onclick, addEventListener, change, submit, load, mouseover, click | 10.5 – 11.5 |
| document.location, Date, textContent, preventDefault, && ! | 11.1 – 11.5 |
| Pages combinées examen | 12.1 – 12.3 |

---

**Conseil :** Cache la correction, fais l’exercice sur papier ou dans un fichier `.html`, puis compare.
