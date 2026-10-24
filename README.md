# TP 4 : Projet de synthèse React – To-Do List interactive ou Blog simple

Application React réalisée dans le cadre du quatrième TP. Elle reprend les notions vues dans les TP précédents : composants fonctionnels, état local, événements, formulaires contrôlés et passage de données par les props. Le projet choisi est l'option A, la To-Do List.

## Ce que le projet démontre

- le découpage d'une interface en composants réutilisables (`TodoForm`, `TodoList`, `TodoItem`)
- le stockage des tâches dans l'état du composant racine avec `useState`
- la remontée des actions vers le parent grâce aux fonctions passées en props
- les formulaires contrôlés, où la valeur du champ est gérée par l'état
- l'affichage d'une liste avec `map()` et l'attribut `key`
- le rendu conditionnel (message quand la liste est vide, tâche barrée quand elle est terminée)
- la sauvegarde des données dans `localStorage` avec `useEffect`

## Fonctionnalités

- ajouter une tâche avec un formulaire (un champ vide est refusé)
- afficher la liste des tâches en temps réel
- cocher ou décocher une tâche pour la marquer comme terminée
- supprimer une tâche
- filtrer l'affichage : toutes, en cours ou terminées
- afficher le nombre de tâches restantes
- conserver les tâches après un rechargement de la page

## Prérequis

- Node.js (version 18 ou plus)
- npm
- un éditeur de code, par exemple Visual Studio Code

Pour vérifier l'installation :

```bash
node -v
npm -v
```

## Installation et lancement

Le projet a été créé avec :

```bash
npx create-react-app mon-projet-react
```

Depuis le dossier du projet :

```bash
npm install
npm start
```

L'application s'ouvre sur `http://localhost:3000`. Si ce n'est pas le cas, il suffit de taper l'adresse dans le navigateur. Pour arrêter le serveur, utiliser `Ctrl + C` dans le terminal.

## Structure du projet

![Structure du dossier src](screenshots/1.png)

```
src/
├── components/
│   ├── TodoForm.js
│   ├── TodoItem.js
│   └── TodoList.js
├── App.css
├── App.js
├── index.css
└── index.js
```

## Les composants

| Composant | Rôle | Données utilisées |
|---|---|---|
| `App` | Garde la liste des tâches et le filtre, définit les fonctions d'ajout, de changement d'état et de suppression | état : `taches`, `filtre` |
| `TodoForm` | Formulaire contrôlé qui envoie le texte saisi au parent | état : `texte` / prop : `ajouterTache` |
| `TodoList` | Parcourt le tableau et affiche un `TodoItem` par tâche, ou un message si la liste est vide | props : `taches`, `changerEtat`, `supprimerTache` |
| `TodoItem` | Affiche une ligne avec la case à cocher et le bouton Supprimer | props : `tache`, `changerEtat`, `supprimerTache` |

La balise `<p>` du message de `TodoList` n'était pas fermée dans l'énoncé, ce qui provoquait une erreur de syntaxe. Elle a été corrigée. Le style est placé dans `App.css` plutôt qu'en ligne.

## Exécution

### Liste avec des tâches

Trois tâches ajoutées, dont une cochée. Elle est barrée et le compteur indique qu'il en reste deux.

![Toutes les tâches](screenshots/2.png)

### Filtre "En cours"

Seules les tâches non terminées restent visibles.

![Filtre en cours](screenshots/3.png)


## Tests effectués

- ajout avec un champ vide : refusé
- ajout de plusieurs tâches
- changement d'état d'une tâche puis retour en arrière
- suppression d'une tâche
- les trois filtres
- rechargement de la page : les tâches sont conservées
- aucune erreur dans la console du navigateur
