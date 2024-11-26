
# Énoncé des Exercices

## Exercice 1 : Utilisation des CTE et sous-requêtes (6 points)
Trouvez les utilisateurs qui ont commenté leurs propres posts. Affichez les colonnes :
- `username` : le nom d'utilisateur
- `post_id` : l'ID du post commenté
- `comment_id` : l'ID du commentaire

## Exercice 2 : Fonctions Fenêtres (5 points)
Trouvez les trois utilisateurs les plus actifs en termes de nombre total de likes reçus sur leurs posts. Affichez :
- `username` : le nom d'utilisateur
- `total_likes` : le nombre total de likes reçus
- `rank` : le rang de l'utilisateur basé sur le nombre de likes.

## Exercice 3 : GROUPING SETS, ROLLUP, CUBE (5 points)
Calculez le nombre total de posts et de commentaires créés par chaque utilisateur. Affichez :
- `user_id` : l'ID de l'utilisateur (peut être `NULL` pour les totaux globaux)
- `content_type` : 'Post', 'Comment' ou `NULL` pour les totaux globaux
- `total_count` : le nombre total de contenus créés pour ce groupe.

## Exercice 4 : Triggers ou Procédures Stockées (4 points)
Créez un trigger qui, à chaque fois qu'un utilisateur est tagué dans un post, insère une notification dans une table `notifications`.
La table `notifications` doit contenir les colonnes suivantes :

`notification_id` : clé primaire
`user_id` : l'ID de l'utilisateur qui reçoit la notification
`message` : le contenu de la notification
`created_at` : la date et l'heure de la notification

## Exercice Bonus : Optimisation avec Index et EXPLAIN
Analysez et optimisez cette requête lente en ajoutant un index ou en optimisant cette requête. 
Montrez les plans d'exécution avant et après optimisation.
<pre>
SELECT p.post_id, p.content, u.username
FROM posts p
JOIN users u ON p.user_id = u.user_id
WHERE p.created_at >= NOW() - INTERVAL '7 days'
ORDER BY p.created_at DESC;
</pre>
