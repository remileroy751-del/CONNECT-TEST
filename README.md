# CONNECT TEST — ÉCOLE TEST

Application mobile de gestion scolaire basée sur Kotlin / Jetpack Compose, avec interface Super Admin web et Supabase.

## Structure
- `app/` : application Android Parent / Enseignant.
- `admin/index.html` : interface Super Admin Direction.
- `index.html` : copie de l'interface web, utile pour GitHub Pages à la racine.
- `supabase/CONNECT_TEST_SCHEMA_COMPLET.sql` : script SQL complet à exécuter dans Supabase.
- `.github/workflows/android.yml` : compilation automatique de l'APK Debug.

## Supabase
Projet : `https://aexuugygfuesjumtjnmk.supabase.co`

La clé Publishable est intégrée dans l'application et dans l'interface web. Elle est conçue pour un usage client. Ne jamais mettre une clé `service_role` dans le dépôt.

## Installation de la base
Dans Supabase > SQL Editor, créer une nouvelle requête, copier tout le contenu de `supabase/CONNECT_TEST_SCHEMA_COMPLET.sql`, puis cliquer sur **Run**.

Ensuite, dans Supabase > Authentication > Users, créer le compte e-mail + mot de passe de la Direction. Depuis l'interface Super Admin, utiliser l'initialisation du compte Direction avec ce compte.

## Message de la Direction
Les messages de la Direction sont enregistrés dans `announcements`. Le parent consulte les messages liés à l'enfant sélectionné via `student_announcements`. Le suivi est maintenant fait avec `announcement_reads` : le bouton affiche « 1 nouveau message », « 2 nouveaux messages », etc., puis le compteur revient à zéro lorsque le parent ouvre « Message de la Direction ». L'ancien système « Bien reçu / accusé de réception » a été supprimé.

## Compilation GitHub
Le workflow installe Java 17, Gradle 8.9 et Android SDK 35, puis exécute `gradle assembleDebug`.

## Mot de passe supplémentaire pour créer une classe
Pour conserver l'architecture existante, la création d'une classe depuis l'admin demande un mot de passe Direction distinct du mot de passe Supabase. Dans le script SQL fourni, sa valeur initiale est : `TEST-Classe-2026!`. Vous pouvez la remplacer avant l'exécution du script si vous le souhaitez.

### Sécurité de l'initialisation Direction
Le premier compte Auth qui exécute l'initialisation devient administrateur. Une fois un administrateur présent, un autre compte Auth ne peut pas s'auto-ajouter comme administrateur via cette fonction.

## Mise à jour identité visuelle — École Test
- Un logo générique **Connect Test** est utilisé dans les espaces Parents et Enseignants ainsi que dans l'interface Super Admin.
- La palette UI est alignée sur le logo : bleu marine, blanc, noir et bordeaux.
- Le logo fourni « Connect Test » est utilisé comme identité visuelle par défaut sur les interfaces Parent, Enseignant et Super Admin, ainsi que comme icône de l'application Android.
- L'interface d'administration conserve toutes les fonctions existantes tout en bénéficiant d'une présentation responsive et d'une hiérarchie visuelle renforcée.

## Mise à jour identité — V12
- Interface admin : marque affichée « École Test » avec « CONNECT TEST » en sous-titre.
- Suppression de l’ancienne mention institutionnelle de l’interface.
- Liste des élèves par classe : uniquement les noms et prénoms, par ordre alphabétique.
- Accueil Android : « École Test » puis « Connect Test ».
- Mention « Version de démonstration » pour distinguer cette édition des applications d’établissements réels.
