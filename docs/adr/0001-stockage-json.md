# ADR-0001 — Garder les notes dans un fichier JSON

**Statut** : Proposé  
**Date** : 2026-11-13

## Contexte

Pour essayer notes-app, on démarre déjà deux programmes : le front et l’API. On veut pouvoir créer quelques notes, redémarrer le serveur et retrouver les mêmes données, sans configurer un service de plus. Quand on lance l’API depuis le dossier `api/`, elle écrit dans `api/notes.json`. Le fichier est créé au premier ajout et ignoré par Git.

## Options envisagées

- **Fichier JSON** : Node sait le lire directement et on peut ouvrir le fichier pour vérifier le résultat d’un test. En revanche, supprimer une seule note oblige à réécrire toute la liste.
- **SQLite** : les données resteraient sur la machine, dans un seul fichier. Une transaction permettrait de modifier une note sans réécrire les autres. Il faudrait choisir un pilote compatible avec nos versions de Node et prévoir la reprise des notes existantes.

## Décision

On propose de garder le fichier JSON pour le TP. Pour vérifier le bug des identifiants, par exemple, il suffit d’ouvrir le fichier après une suppression et de regarder quels identifiants restent. Pour cet usage, passer à SQLite apporte peu.

## Conséquences

Chacun a ses propres notes en local. Copier le fichier suffit pour conserver un jeu de données de test. Il faut toutefois lancer le serveur depuis le bon dossier : le chemin est relatif au répertoire de lancement.

Les lectures et écritures synchrones bloquent l’API pendant les accès disque. Une écriture interrompue peut aussi laisser un fichier illisible. Si on doit lancer deux instances de l’API sur les mêmes données, il faudra revoir ce choix : chacune pourrait écraser les modifications de l’autre.
