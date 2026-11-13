# ADR-0002 — Paginer GET /notes par numéro de page

**Statut** : Proposé  
**Date** : 2026-11-13

## Contexte

Le front appelle `GET /notes` sans paramètre et filtre ensuite les titres reçus. L’API découpe déjà la liste par groupes de dix, mais elle saute les dix premières notes : la page par défaut vaut 1 et le découpage démarre à `page * 10`. Passer `page=0` ne contourne pas le problème puisque le serveur remplace aussi zéro par 1.

## Options envisagées

- **Renvoyer toute la liste** : la recherche locale du front porterait sur toutes les notes. En contrepartie, chaque chargement transférerait tout le fichier, même pour afficher dix titres.
- **Numéro de page** : une URL comme `/notes?page=2` se partage et se teste facilement. Si une note est supprimée entre deux requêtes, les suivantes peuvent changer de page.
- **Curseur** : demander les notes après le dernier identifiant reçu éviterait le décalage lié à une suppression précédente. Cela demande un ordre stable et le front devrait conserver le curseur pour avancer.

## Décision

On propose des pages de dix notes dans l’ordre du fichier, numérotées à partir de 1. Sans paramètre, l’API servirait la page 1. Le premier indice serait `(page - 1) * 10` : avec douze notes, on en attend dix sur la première page et deux sur la deuxième. Une page au-delà de la fin renverrait `[]` ; zéro, un nombre négatif ou une valeur non entière donneraient une erreur 400. Ce contrat reste à implémenter.

## Conséquences

Le front devra mémoriser la page affichée et transmettre son numéro lors d’un changement de page. Une page de moins de dix notes indique la fin. Si elle en contient exactement dix, il faudra essayer la suivante pour savoir s’il en reste.

Le champ de recherche actuel filtre uniquement la page chargée. Pour rechercher un titre dans toutes les notes, le front pourra appeler la route existante `/search?q=...`. Enfin, limiter la réponse à dix notes réduit le transfert mais pas la lecture disque : avec le stockage actuel, le serveur charge tout le JSON avant de découper la liste.
