### README

`users` : Table contenant les informations des utilisateurs, avec des champs comme `user_id`, `username`, `email`, `password` et `created_at`.

`posts` : Table des publications faites par les utilisateurs, liée à la table `users` via `user_id`. Contient les champs `post_id`, `user_id`, `content` et `created_at`.

`comments` : Table des commentaires sur les publications, avec des références à la fois aux posts (via post_id) et aux users (via user_id). Le champ parent_comment_id permet de gérer les commentaires en réponse à d'autres commentaires.

`likes` : Table pour gérer les "likes" sur les posts ou les commentaires. Elle contient des contraintes pour s'assurer qu'un like est associé soit à un post, soit à un commentaire, mais pas aux deux simultanément. Les champs principaux sont like_id, user_id, post_id, comment_id et created_at, avec une contrainte d'unicité sur la combinaison de user_id, post_id et comment_id.

`user_tags` : Table permettant de taguer des utilisateurs dans des posts. Elle contient tag_id, post_id, tagged_user_id, tagged_by_user_id et created_at.

`post_views` : Nouvelle table qui enregistre les vues des posts par les utilisateurs, avec les champs view_id, post_id, user_id et viewed_at.

