# Révision — Théorie des graphes (cours + Python)

Guide ordonné pour l’examen : **questions de cours** + **code Python (NetworkX)**.

---

## Table des matières

**Partie A — Installation**
1. [Installer Python et les bibliothèques](#partie-a--installation)

**Partie B — Cours (définitions)**
2. [Vocabulaire de base](#partie-b1--vocabulaire-de-base)
3. [Degré et propriétés](#partie-b2--degré-et-propriétés)
4. [Matrice d’adjacence](#partie-b3--matrice-dadjacence)
5. [Chaînes, cycles, connexité](#partie-b4--chaînes-cycles-connexité)
6. [Graphe orienté](#partie-b5--graphe-orienté)
7. [Types de graphes](#partie-b6--types-de-graphes)
8. [BFS — parcours en largeur](#partie-b7--bfs--parcours-en-largeur)
9. [Vrai / Faux à connaître](#partie-b8--vrai--faux-à-connaître)

**Partie C — Code Python (résumés)**
10. [Créer et afficher un graphe](#partie-c1--créer-et-afficher-un-graphe)
11. [Sommets et arêtes](#partie-c2--sommets-et-arêtes)
12. [Analyse et algorithmes](#partie-c3--analyse-et-algorithmes)
13. [Graphes pondérés et visualisation](#partie-c4--graphes-pondérés-et-visualisation)
14. [BFS en Python](#partie-c5--bfs-en-python)

**Partie D — Exercices**
15. [Exercices cours (théorie)](#partie-d1--exercices-cours-théorie)
16. [Exercices code Python](#partie-d2--exercices-code-python)

---

# Partie A — Installation

## A.1 Python

1. Aller sur [python.org](https://www.python.org)
2. Télécharger et installer
3. **Windows :** cocher **« Add Python to PATH »**

## A.2 Bibliothèques

Dans le terminal (`cmd`) :

```bash
pip install networkx
pip install matplotlib
```

Optionnel (graphes interactifs 3D) :

```bash
pip install pyvis
```

## A.3 Test d’installation

Fichier `test_graphe.py` :

```python
import networkx as nx
import matplotlib.pyplot as plt

G = nx.Graph()
G.add_edge("Moi", "Ami 1")
G.add_edge("Moi", "Ami 2")
G.add_edge("Ami 1", "Ami 2")
G.add_edge("Ami 2", "Ami 3")

nx.draw(G, with_labels=True, node_color='skyblue', node_size=1500, edge_color='gray')
plt.show()
```

| Bibliothèque | Rôle |
|--------------|------|
| **NetworkX** | Créer, modifier, analyser des graphes |
| **Matplotlib** | Afficher les graphes (`plt.show()`) |
| **Pyvis** | Graphes interactifs (optionnel) |

---

# Partie B — Cours (définitions)

## Partie B1 — Vocabulaire de base

| Terme | Définition |
|-------|------------|
| **Graphe** G = (S, A) | Ensemble de **sommets** S et d’**arêtes** A (liens entre sommets) |
| **Sommet** (nœud, vertex) | Point du graphe (ex. A, B, 1, « Tunis ») |
| **Arête** (edge) | Lien entre 2 sommets ; notée **(A, B)** en non orienté |
| **Arc** | Lien **orienté** ; noté **(A → B)** ou **(A, B)** dans un graphe dirigé |
| **Ordre** du graphe | Nombre de sommets : **\|S\|** |
| **Taille** | Nombre d’arêtes : **m** |
| **Voisin** de s | Sommet relié à s par une arête |
| **Voisinage** N(s) | Ensemble des voisins de s |
| **Sommet isolé** | Degré = 0 (aucune arête) |
| **Graphe complet** Kₙ | Chaque sommet est relié à **tous** les autres |

---

## Partie B2 — Degré et propriétés

| Terme | Définition |
|-------|------------|
| **Degré** deg(s) | Nombre d’arêtes incidentes à s (non orienté) |
| **Somme des degrés** | **Σ deg(s) = 2m** (chaque arête compte pour 2) |
| **Conséquence** | La somme des degrés est **toujours paire** |

**Exemple** — Graphe : (A,B), (A,C), (B,C), (B,D), (C,E)

| Sommet | Degré |
|--------|-------|
| A | 2 |
| B | 3 |
| C | 3 |
| D | 1 |
| E | 1 |

- Ordre = **5**
- m = **5** arêtes → Σ deg = 10 = 2×5 ✓

---

## Partie B3 — Matrice d’adjacence

Tableau carré : ligne i, colonne j = **1** s’il existe une arête (ou arc) de i vers j, sinon **0**.

**Graphe non orienté** → matrice **symétrique** : aᵢⱼ = aⱼᵢ

**Exemple** — Sommets A, B, C, D — Arêtes : (A,B), (A,C), (B,D), (C,D)

```
     A  B  C  D
A [  0  1  1  0 ]
B [  1  0  0  1 ]
C [  1  0  0  1 ]
D [  0  1  1  0 ]
```

---

## Partie B4 — Chaînes, cycles, connexité

| Terme | Définition |
|-------|------------|
| **Chaîne** | Suite de sommets reliés par des arêtes consécutives |
| **Longueur** | Nombre d’**arêtes** dans la chaîne |
| **Chaîne fermée** | Départ = arrivée (même sommet) |
| **Cycle** | Chaîne fermée **sans répéter** les sommets (sauf départ/arrivée) |
| **Graphe connexe** | Entre **toute** paire de sommets, il existe une chaîne |
| **Composante connexe** | Sous-graphe connexe **maximal** (impossible d’ajouter un sommet) |

**Exemple** — Deux composantes : {A-B-C} et {D-E} → graphe **non connexe**, **2** composantes.

---

## Partie B5 — Graphe orienté

| Terme | Définition |
|-------|------------|
| **Successeur** de s | Sommets atteints par un arc **partant** de s |
| **Prédécesseur** de s | Sommets ayant un arc **vers** s |
| **Matrice d’adjacence** | En général **non symétrique** |

**Exemple** — Arcs : A→B, B→C, C→A, C→D

- Succ(C) = {A, D}
- Pred(A) = {C}

Matrice (ordre A, B, C, D) :

```
     A  B  C  D
A [  0  1  0  0 ]
B [  0  0  1  0 ]
C [  1  0  0  1 ]
D [  0  0  0  0 ]
```

---

## Partie B6 — Types de graphes

| Type | Symbole NetworkX | Description |
|------|------------------|-------------|
| **Non orienté** | `nx.Graph()` | Arête (A,B) = lien dans les deux sens |
| **Orienté** | `nx.DiGraph()` | Arc A→B seulement |
| **Pondéré** | `weight=` sur une arête | Valeur numérique (distance, coût) |
| **Multigraphe** | `nx.MultiGraph()` | Plusieurs arêtes entre les mêmes sommets |

---

## Partie B7 — BFS — parcours en largeur

| Idée | Détail |
|------|--------|
| **Principe** | Explorer **niveau par niveau** : voisins directs, puis voisins des voisins… |
| **Structure** | **File FIFO** (First In, First Out) |
| **Marquage** | Ensemble des sommets **déjà visités** (évite les boucles) |
| **Ordre** | Du plus proche au plus loin depuis la source |

**Pseudo-code :**

```
BFS(G, s):
    file Q ← [s]
    marquer s comme visité
    tant que Q non vide:
        u ← défiler Q
        pour chaque voisin v de u:
            si v non visité:
                marquer v
                enfiler v
```

**Exemple** — Graphe A-B-C-D-E-F → BFS depuis A : **A → B → C → D → E → F**

**Applications :** plus court chemin (nombre d’arêtes), réseau social (amis à distance k).

---

## Partie B8 — Vrai / Faux à connaître

| Affirmation | Réponse |
|-------------|---------|
| Un graphe complet est toujours connexe | **Vrai** |
| La somme des degrés est toujours paire | **Vrai** |
| Un cycle eulérien passe une seule fois par chaque sommet | **Faux** (cycle **hamiltonien**) |
| La matrice d’un graphe non orienté est symétrique | **Vrai** |

---

# Partie C — Code Python (résumés)

## Partie C1 — Créer et afficher un graphe

```python
import networkx as nx
import matplotlib.pyplot as plt

G = nx.Graph()          # non orienté
DG = nx.DiGraph()       # orienté
MG = nx.MultiGraph()    # multi-arêtes

nx.draw(G, with_labels=True, node_color='skyblue', node_size=1500)
plt.show()
```

---

## Partie C2 — Sommets et arêtes

```python
# Sommets
G.add_node("A")
G.add_nodes_from(["B", "C", "D"])
G.remove_node("D")

# Arêtes (non orienté : ordre peu importe)
G.add_edge("A", "B")
G.add_edges_from([("B", "C"), ("C", "D")])
G.remove_edge("A", "C")

# Attributs
G.add_edge("A", "B", weight=4.5)
G.nodes["A"]["label"] = "Source"

# Lister
print(G.nodes())
print(G.edges())
print(G.number_of_nodes())
print(G.number_of_edges())
```

---

## Partie C3 — Analyse et algorithmes

```python
# Voisins et degré
list(G.neighbors("A"))
G.degree("A")

# Existence
G.has_node(5)
G.has_edge(2, 4)

# Plus court chemin
chemin = nx.shortest_path(G, source="A", target="C")
chemin_pondere = nx.shortest_path(G, source="Tunis", target="Tozeur", weight="weight")
distance = nx.shortest_path_length(G, source="Tunis", target="Tozeur", weight="weight")

# Connexité
nx.is_connected(G)
nx.number_connected_components(G)
```

---

## Partie C4 — Graphes pondérés et visualisation

```python
G.add_weighted_edges_from([
    ("A", "B", 5),
    ("A", "C", 2),
    ("B", "D", 7),
    ("C", "D", 1)
])

pos = nx.spring_layout(G)
nx.draw(G, pos, with_labels=True)
labels = nx.get_edge_attributes(G, 'weight')
nx.draw_networkx_edge_labels(G, pos, edge_labels=labels)
plt.show()
```

**Deux graphes côte à côte :**

```python
plt.figure(figsize=(10, 4))
plt.subplot(121)
nx.draw(G, with_labels=True)
plt.title("Non orienté")
plt.subplot(122)
nx.draw(DG, with_labels=True)
plt.title("Orienté")
plt.show()
```

---

## Partie C5 — BFS en Python

**Avec NetworkX :**

```python
bfs_edges = list(nx.bfs_edges(G, source="A"))
bfs_tree = nx.bfs_tree(G, source="A")
```

**À la main (dictionnaire + deque) :**

```python
from collections import deque

def bfs(graphe, depart):
    visites = set()
    file = deque([depart])
    visites.add(depart)
    while file:
        u = file.popleft()
        print(u)
        for v in graphe[u]:
            if v not in visites:
                visites.add(v)
                file.append(v)
```

---

# Partie D — Exercices

Format : **Question** → **Correction**

---

# Partie D1 — Exercices cours (théorie)

---

### Ex. T1 — Ordre et degrés

**Question :** Graphe non orienté — Sommets : A, B, C, D, E — Arêtes : (A,B), (A,C), (B,C), (B,D), (C,E).

1. Ordre du graphe ?
2. Degré de chaque sommet ?
3. Voisins de B ?
4. Sommet isolé ?
5. Graphe complet ?

**Correction :**

1. **Ordre = 5** (5 sommets)
2. deg(A)=2, deg(B)=3, deg(C)=3, deg(D)=1, deg(E)=1
3. **Voisinage(B) = {A, C, D}**
4. **Non** — aucun sommet de degré 0
5. **Non** — ex. D et E ne sont pas reliés

---

### Ex. T2 — Somme des degrés

**Question :** Sommets A,B,C,D — Arêtes : (A,B), (A,C), (A,D), (B,C). Calculer les degrés, la somme, vérifier Σ deg(s) = 2m.

**Correction :**

- deg(A)=3, deg(B)=2, deg(C)=2, deg(D)=1
- **Σ = 3+2+2+1 = 8**
- m = 4 → **2m = 8** → propriété **vérifiée**

---

### Ex. T3 — Matrice d’adjacence

**Question :** Sommets A,B,C,D — Arêtes : (A,B), (A,C), (B,D), (C,D). Donner la matrice. Symétrique ?

**Correction :**

```
     A  B  C  D
A [  0  1  1  0 ]
B [  1  0  0  1 ]
C [  1  0  0  1 ]
D [  0  1  1  0 ]
```

**Oui**, symétrique (graphe non orienté).

---

### Ex. T4 — Chaîne, cycle

**Question :** Arêtes : (A,B), (B,C), (C,D), (D,A), (A,C). Donner une chaîne de longueur 3, une chaîne fermée, un cycle.

**Correction :**

1. Chaîne longueur 3 : **A — B — C — D** (3 arêtes)
2. Chaîne fermée : **A — B — C — A**
3. Cycle : **A — B — C — D — A**

---

### Ex. T5 — Connexité

**Question :** Composantes {A-B-C} et {D-E}. Connexe ? Nombre de composantes ?

**Correction :**

1. **Non connexe** — pas de chemin entre A et D par exemple
2. **2 composantes connexes**

---

### Ex. T6 — Graphe orienté

**Question :** Arcs A→B, B→C, C→A, C→D. Successeurs de C ? Prédécesseurs de A ? Matrice ?

**Correction :**

1. **Succ(C) = {A, D}**
2. **Pred(A) = {C}**
3. Matrice (A,B,C,D) — ligne i → colonne j = 1 si arc i→j :

```
     A  B  C  D
A [  0  1  0  0 ]
B [  0  0  1  0 ]
C [  1  0  0  1 ]
D [  0  0  0  0 ]
```

**Non symétrique.**

---

### Ex. T7 — Vrai ou Faux

**Question :** Répondre Vrai ou Faux :

1. Graphe complet → toujours connexe
2. Somme des degrés toujours paire
3. Cycle eulérien = passe une fois par chaque sommet
4. Matrice non orienté = symétrique

**Correction :**

| # | Réponse |
|---|---------|
| 1 | **Vrai** |
| 2 | **Vrai** |
| 3 | **Faux** |
| 4 | **Vrai** |

---

### Ex. T8 — Définitions rapides

**Question :** Définir : ordre, taille, sommet isolé, voisin, composante connexe.

**Correction :**

| Terme | Définition courte |
|-------|-------------------|
| Ordre | Nombre de sommets |
| Taille | Nombre d’arêtes m |
| Sommet isolé | deg(s) = 0 |
| Voisin | Sommet relié par une arête |
| Composante connexe | Sous-graphe connexe maximal |

---

### Ex. T9 — BFS à la main

**Question :** Graphe : A-B, A-C, B-D, B-E, C-E, E-F. Donner l’ordre BFS depuis A.

**Correction :**

**A → B → C → D → E → F**

(File : après A → [B,C] ; après B → [C,D,E] ; etc.)

---

### Ex. T10 — Propriété 2m

**Question :** Un graphe a 6 arêtes. Quelle est la somme des degrés ?

**Correction :**

**Σ deg(s) = 2m = 2 × 6 = 12**

---

# Partie D2 — Exercices code Python

---

### Ex. P1 — Imports et graphe vide

**Question :** Écris les imports et crée un graphe non orienté vide `G`.

**Correction :**

```python
import networkx as nx
import matplotlib.pyplot as plt

G = nx.Graph()
```

---

### Ex. P2 — Ajouter sommets et arêtes

**Question :** Ajoute les sommets A, B, C, D et les arêtes (A,B), (A,C), (B,C), (C,D). Affiche avec labels.

**Correction :**

```python
import networkx as nx
import matplotlib.pyplot as plt

G = nx.Graph()
G.add_nodes_from(["A", "B", "C", "D"])
G.add_edges_from([("A", "B"), ("A", "C"), ("B", "C"), ("C", "D")])

nx.draw(G, with_labels=True, node_color='skyblue', node_size=1500)
plt.show()
```

---

### Ex. P3 — Supprimer nœud et arête

**Question :** Sur un graphe avec A,B,C,D et arêtes (A,B), (A,C), (C,D) : supprime D puis supprime (A,C).

**Correction :**

```python
G.remove_node("D")
G.remove_edge("A", "C")
```

---

### Ex. P4 — Graphe orienté vs non orienté

**Question :** Crée `G = nx.Graph()` et `DG = nx.DiGraph()`. Ajoute sommets 1..5 à chacun. Supprime 1 de G. Arêtes G : {2,3},{2,5},{3,4},{4,5}. Arcs DG : (1,3),(2,3),(2,4),(2,5),(4,5),(5,1). Affiche sommets et arêtes.

**Correction :**

```python
import networkx as nx
import matplotlib.pyplot as plt

G = nx.Graph()
DG = nx.DiGraph()

G.add_nodes_from([1, 2, 3, 4, 5])
DG.add_nodes_from([1, 2, 3, 4, 5])

G.remove_node(1)

G.add_edges_from([(2, 3), (2, 5), (3, 4), (4, 5)])
DG.add_edges_from([(1, 3), (2, 3), (2, 4), (2, 5), (4, 5), (5, 1)])

print("Sommets G :", G.nodes())
print("Arêtes G :", G.edges())
print("Sommets DG :", DG.nodes())
print("Arêtes DG :", DG.edges())
```

---

### Ex. P5 — Afficher deux graphes côte à côte

**Question :** Même G et DG qu’en P4. Les tracer dans une figure avec 2 sous-graphiques.

**Correction :**

```python
plt.figure(figsize=(10, 4))

plt.subplot(121)
nx.draw(G, with_labels=True)
plt.title("Graphe non orienté")

plt.subplot(122)
nx.draw(DG, with_labels=True)
plt.title("Graphe orienté")

plt.show()
```

---

### Ex. P6 — Nombre de sommets, arêtes, voisins

**Question :** Graphe avec arêtes (1,2), (1,3), (2,4), (3,5). Afficher nombre de sommets, d’arêtes, voisins de 1.

**Correction :**

```python
import networkx as nx

G = nx.Graph()
G.add_edges_from([(1, 2), (1, 3), (2, 4), (3, 5)])

print("Nombre de sommets :", G.number_of_nodes())
print("Nombre d'arêtes :", G.number_of_edges())
print("Voisins du sommet 1 :", list(G.neighbors(1)))
```

**Résultat attendu :** 5 sommets, 4 arêtes, voisins de 1 : **[2, 3]**

---

### Ex. P7 — Plus court chemin

**Question :** Graphe avec chemins A-B-C et A-D. Afficher le plus court chemin de A à C.

**Correction :**

```python
import networkx as nx

G = nx.Graph()
G.add_edges_from([("A", "B"), ("B", "C"), ("A", "D")])

chemin = nx.shortest_path(G, source="A", target="C")
print("Chemin le plus court :", chemin)
```

**Résultat :** `['A', 'B', 'C']`

---

### Ex. P8 — Graphe pondéré

**Question :** Créer un graphe pondéré : A-B(5), A-C(2), B-D(7), C-D(1). Afficher les poids sur le dessin.

**Correction :**

```python
import networkx as nx
import matplotlib.pyplot as plt

G = nx.Graph()
G.add_weighted_edges_from([
    ("A", "B", 5),
    ("A", "C", 2),
    ("B", "D", 7),
    ("C", "D", 1)
])

pos = nx.spring_layout(G)
nx.draw(G, pos, with_labels=True)
labels = nx.get_edge_attributes(G, 'weight')
nx.draw_networkx_edge_labels(G, pos, edge_labels=labels)
plt.show()
```

---

### Ex. P9 — Plus court chemin pondéré (villes)

**Question :** Graphe Tunis-Bizerte(65), Tunis-Hammamet(63), Hammamet-Sousse(80), Sousse-Sfax(130), Sfax-Gabès(140), Gabès-Gafsa(150), Gafsa-Tozeur(95). Chemin et distance Tunis → Tozeur.

**Correction :**

```python
import networkx as nx

G = nx.Graph()
G.add_weighted_edges_from([
    ("Tunis", "Bizerte", 65),
    ("Tunis", "Hammamet", 63),
    ("Hammamet", "Sousse", 80),
    ("Sousse", "Sfax", 130),
    ("Sfax", "Gabès", 140),
    ("Gabès", "Gafsa", 150),
    ("Gafsa", "Tozeur", 95)
])

chemin = nx.shortest_path(G, source="Tunis", target="Tozeur", weight="weight")
dist = nx.shortest_path_length(G, source="Tunis", target="Tozeur", weight="weight")

print(" -> ".join(chemin))
print("Distance :", dist, "km")
```

---

### Ex. P10 — Graphe aléatoire

**Question :** Entre 2 et 10 sommets (aléatoire). Pour chaque paire possible, ajouter une arête avec probabilité 50 %. Afficher et dessiner.

**Correction :**

```python
import networkx as nx
import matplotlib.pyplot as plt
import random

G = nx.Graph()
n = random.randint(2, 10)

for i in range(n):
    G.add_node(i)

for i in range(n):
    for j in range(i + 1, n):
        if random.randint(0, 1) == 1:
            G.add_edge(i, j)

print("Sommets :", G.nodes())
print("Arêtes :", G.edges())
nx.draw(G, with_labels=True)
plt.show()
```

---

### Ex. P11 — Sommets isolés (fonction)

**Question :** Écrire une fonction qui retourne `False` s’il existe un sommet de degré 0, sinon `True`.

**Correction :**

```python
import networkx as nx

def test_non_isole(G):
    for sommet in G.nodes():
        if G.degree(sommet) == 0:
            return False
    return True

G = nx.Graph()
G.add_nodes_from([1, 2, 3])
G.add_edge(1, 2)
print(test_non_isole(G))  # True

G.add_node(4)  # isolé
print(test_non_isole(G))  # False
```

---

### Ex. P12 — BFS avec NetworkX

**Question :** Graphe A-B, A-C, B-D, B-E, C-F. BFS depuis A. Afficher l’ordre des arêtes BFS.

**Correction :**

```python
import networkx as nx

G = nx.Graph()
G.add_edges_from([('A', 'B'), ('A', 'C'), ('B', 'D'), ('B', 'E'), ('C', 'F')])

bfs_edges = list(nx.bfs_edges(G, source='A'))
print("Arêtes BFS :", bfs_edges)
```

---

### Ex. P13 — BFS à la main (deque)

**Question :** Dictionnaire `reseau` : Amin→[Leila,Omar], etc. Implémenter BFS depuis « Amin ».

**Correction :**

```python
from collections import deque

reseau = {
    'Amin': ['Leila', 'Omar'],
    'Leila': ['Amin', 'Sami'],
    'Omar': ['Amin', 'Yassine'],
    'Sami': ['Leila', 'Zineb'],
    'Yassine': ['Omar', 'Zineb'],
    'Zineb': ['Sami', 'Yassine']
}

def bfs_prenoms(graphe, depart):
    visites = set()
    file = deque([depart])
    visites.add(depart)
    while file:
        personne = file.popleft()
        print(personne)
        for ami in graphe[personne]:
            if ami not in visites:
                visites.add(ami)
                file.append(ami)

bfs_prenoms(reseau, 'Amin')
```

**Ordre :** Amin → Leila → Omar → Sami → Yassine → Zineb

---

### Ex. P14 — DiGraph arc simple

**Question :** Créer un DiGraph avec arc A→B seulement. Les voisins de A en non orienté vs successeurs en orienté ?

**Correction :**

```python
import networkx as nx

G = nx.Graph()
G.add_edge("A", "B")
print(list(G.neighbors("A")))  # ['B']

DG = nx.DiGraph()
DG.add_edge("A", "B")
print(list(DG.successors("A")))   # ['B']
print(list(DG.predecessors("B"))) # ['A']
```

---

### Ex. P15 — has_node et has_edge

**Question :** Vérifier si le sommet 5 et l’arête (2,4) existent dans G.

**Correction :**

```python
print(G.has_node(5))
print(G.has_edge(2, 4))
```

---

### Ex. P16 — Connexité

**Question :** Vérifier si G est connexe et donner le nombre de composantes.

**Correction :**

```python
print(nx.is_connected(G))
print(nx.number_connected_components(G))
```

---

### Ex. P17 — Atelier complet (énoncé type examen)

**Question :** En un seul script : créer G et DG, sommets 1..5, afficher, supprimer 1 de G, ajouter les arêtes de l’atelier, afficher, tracer les deux graphes.

**Correction :**

```python
import networkx as nx
import matplotlib.pyplot as plt

G = nx.Graph()
DG = nx.DiGraph()

G.add_nodes_from([1, 2, 3, 4, 5])
DG.add_nodes_from([1, 2, 3, 4, 5])

print("Avant suppression G :", list(G.nodes()))
G.remove_node(1)

G.add_edges_from([(2, 3), (2, 5), (3, 4), (4, 5)])
DG.add_edges_from([(1, 3), (2, 3), (2, 4), (2, 5), (4, 5), (5, 1)])

print("G sommets :", list(G.nodes()))
print("G arêtes :", list(G.edges()))
print("DG sommets :", list(DG.nodes()))
print("DG arêtes :", list(DG.edges()))

plt.figure(figsize=(10, 4))
plt.subplot(121)
nx.draw(G, with_labels=True)
plt.title("G")
plt.subplot(122)
nx.draw(DG, with_labels=True)
plt.title("DG")
plt.show()
```

---

## Checklist examen

### Questions de cours

| Sujet | Exercices |
|-------|-----------|
| Ordre, degré, voisins, isolé, complet | T1, T8 |
| Σ deg = 2m | T2, T10 |
| Matrice adjacence, symétrie | T3, T6 |
| Chaîne, cycle, connexité | T4, T5 |
| Orienté succ/préd | T6 |
| Vrai/Faux | T7 |
| BFS ordre | T9 |

### Code Python

| Sujet | Exercices |
|-------|-----------|
| Création Graph / DiGraph | P1–P5, P17 |
| add/remove nodes & edges | P2–P4 |
| number_of_*, neighbors | P6 |
| shortest_path, weight | P7–P9 |
| draw, labels, subplot | P5, P8 |
| Graphe aléatoire | P10 |
| Fonction degré 0 | P11 |
| bfs_edges, deque BFS | P12–P13 |
| has_node, is_connected | P15–P16 |

---

## Ordre d’apprentissage recommandé

1. **Jour 1** — Partie B1 à B4 + exercices T1–T4  
2. **Jour 2** — Partie B5 à B8 + T5–T10  
3. **Jour 3** — Partie C (tout le code) + P1–P9  
4. **Jour 4** — BFS (B7, C5) + P10–P17  
5. **Jour 5** — Refaire T7, P17 et l’atelier complet sans regarder

---

Bonne préparation pour l’examen.
