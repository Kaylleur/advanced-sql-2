
# Explication du Schéma de Base de Données

Voici le schéma des tables utilisées pour l'évaluation :

### Table `users`
- **user_id** (SERIAL PRIMARY KEY) : Identifiant unique de l'utilisateur.
- **username** (VARCHAR) : Nom unique de l'utilisateur.
- **email** (VARCHAR) : Email unique de l'utilisateur.
- **password** (VARCHAR) : Mot de passe de l'utilisateur.
- **created_at** (TIMESTAMP) : Date de création de l'utilisateur.

### Table `posts`
- **post_id** (SERIAL PRIMARY KEY) : Identifiant unique du post.
- **user_id** (INTEGER) : Référence à l'utilisateur ayant créé le post.
- **content** (TEXT) : Contenu du post.
- **created_at** (TIMESTAMP) : Date de création du post.

### Table `comments`
- **comment_id** (SERIAL PRIMARY KEY) : Identifiant unique du commentaire.
- **post_id** (INTEGER) : Référence au post commenté.
- **user_id** (INTEGER) : Référence à l'utilisateur ayant fait le commentaire.
- **parent_comment_id** (INTEGER) : Référence au commentaire parent, pour les réponses.
- **content** (TEXT) : Contenu du commentaire.
- **created_at** (TIMESTAMP) : Date de création du commentaire.

### Table `likes`
- **like_id** (SERIAL PRIMARY KEY) : Identifiant unique du "like".
- **user_id** (INTEGER) : Référence à l'utilisateur ayant aimé.
- **post_id** (INTEGER) : Référence au post aimé (ou `NULL` si commentaire).
- **comment_id** (INTEGER) : Référence au commentaire aimé (ou `NULL` si post).
- **created_at** (TIMESTAMP) : Date du "like".
- **CHECK** : Soit `post_id` est renseigné, soit `comment_id`.

### Table `user_tags`
- **tag_id** (SERIAL PRIMARY KEY) : Identifiant unique de la mention.
- **post_id** (INTEGER) : Référence au post contenant la mention.
- **tagged_user_id** (INTEGER) : Référence à l'utilisateur mentionné.
- **tagged_by_user_id** (INTEGER) : Référence à l'utilisateur ayant fait la mention.
- **created_at** (TIMESTAMP) : Date de la mention.

### Table `post_views`
- **view_id** (SERIAL PRIMARY KEY) : Identifiant unique de la vue.
- **post_id** (INTEGER) : Référence au post vu.
- **user_id** (INTEGER) : Référence à l'utilisateur ayant vu le post.
- **viewed_at** (TIMESTAMP) : Date de la vue.

---
