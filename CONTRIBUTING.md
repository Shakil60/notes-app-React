# Contribuer à notes-app

## Du ticket à la branche

Ouvrir une issue pour décrire le besoin. Pour un bug, donner les étapes de reproduction et le résultat attendu. S’assigner le ticket pour que les autres sachent qui le prend.

Partir de `main` à jour. Nommer la branche d’après le ticket : `fix/3-identifiants-notes` pour un correctif, `docs/8-readme` pour la documentation. Garder un seul sujet par PR. Pour les commits, on utilise par exemple `fix(api): éviter les identifiants en double` ou `docs: expliquer le stockage JSON`.

## Ouvrir et relire la PR

Dans la description, préciser le contexte, les changements, leur impact et la façon de les tester. Ajouter `Closes #3`, par exemple, si la fusion doit fermer le ticket. Pour une correction API, donner la requête et le résultat attendu. Pour le front, indiquer ce qu’on doit voir dans le navigateur.

Les relecteurs sont répartis par dossier dans [CODEOWNERS](.github/CODEOWNERS). Une approbation d’un coéquipier suffit. Le relecteur teste la branche et commente les lignes concernées. L’auteur répond dans chaque fil et pousse les corrections sur la même branche. Le relecteur vérifie le dernier changement avant de choisir **Approve**.

On fusionne avec **Create a merge commit**, comme pour les PR du README et des ADR. Après la fusion, supprimer la branche et vérifier que le ticket lié est fermé.

## Tenir la documentation à jour

Si une commande, une route ou un port change, corriger aussi l’exemple du README dans la même PR. Tester les instructions d’installation depuis un clone neuf. Pour un choix d’architecture, ouvrir un [ADR](docs/adr/) au statut Proposé, le faire relire puis mettre à jour son statut et l’index. La [répartition des rôles](docs/equipe.md) indique à qui demander une relecture.
