# Qui fait quoi

Le wiki est désactivé sur le dépôt. Cette page rassemble les rôles et les liens utiles pour le TP.

## Qui prépare et qui valide ?

**R** réalise le travail, **A** répond du résultat, **C** donne un avis avant la livraison et **I** est tenu au courant. Pour une PR, l’approbation vient toujours d’un autre membre que son auteur.

| Livrable | Nohan | Shakil | Mathéo | Dimitri |
| --- | --- | --- | --- | --- |
| Création et suppression des notes côté API | I | A | C | R |
| Affichage du contenu des notes côté React | R | A | C | I |
| Chargement de la liste côté front | A | I | R | C |
| Modèles d’issues et de PR | A | R | I | C |
| README et installation depuis un clone neuf | A | R | C | I |
| ADR sur le stockage JSON | R | A | I | C |
| ADR sur la pagination | R | C | A | I |

## Où trouver quoi ?

| Je cherche… | Où regarder |
| --- | --- |
| Les commandes pour lancer les deux serveurs | [Installation](../README.md#installation) |
| Les routes et le stockage des notes | [Serveur Express](../api/server.js) |
| Le formulaire, la recherche et la liste | [Composant React](../web/src/App.jsx) |
| La raison d’un choix technique | [Index des ADR](adr/) |
| Les règles pour proposer une modification | [Guide de contribution](../CONTRIBUTING.md) |
| Les relecteurs pour un dossier | [CODEOWNERS](../.github/CODEOWNERS) |
| Les bugs et le travail en cours | [Issues](https://github.com/Shakil60/notes-app-React/issues) et [PR](https://github.com/Shakil60/notes-app-React/pulls) |
