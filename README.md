# SEO cheat sheet
SEO recommandations for devs

### Sommaire
- [Balises html importantes](#tags)
  - [La balise title](#titleTag)
  - [La balise meta description](#descriptionTag)
  - [La balise meta robots](#robotsTag)
- [Structure et navigation](#structure)
  - [Structure HTML](#html)
  - [Structure des URLs](#url)  

## <a name="tags">Balises html importantes</a>
### <a name="titleTag">La balise ```<title>```
Peut-être la balise la plus importante de toutes. Son contenu apparait dans le titre de l'onglet du navigateur et dans le texte en bleu dans les résultats de recherche Google. 

<img src="https://github.com/ggglyke/seo-cheat-sheet/blob/main/snippet.jpg?raw=true" alt="SERP Snippet" width="750"/>

Chaque page du site doit avoir une balise ```<title>``` unique incluant les mots-clés pertinents.
  
  Une balise ```<title>``` non optimisée :
  ```xml
  <head>
    <title>Accueil</title>
  </head>
  ```
  Une balise ```<title>``` optimisée :
  ```xml
  <head>
    <title>Location bureaux Nantes - Bureaux locaux</title>
  </head>
  ```
  > - entre 50 et 70 caractères
  > - chaque page doit avoir un balise ```<title>``` unique
  > - mots-clés importants au début
  > - un titre bien écrit influence le taux de clic
  
  ### <a name="descriptionTag">La balise meta description</a>
  Elle sert à décrire le contenu de la page. Elle apparait dans le texte en noir pour chaque résultat de recherche sur Google. Son contenu n'est pas pris en compte pour le SEO mais elle influence le taux de clic.
  
  ```xml
  <head>
    <meta name="description" content="Nantes : 296 annonces de location de bureaux à Nantes sur BureauxLocaux.com. Trouvez les bureaux de votre entreprise grâce à BureauxLocaux. Toutes les annonces immobilières pour les entreprises.">
  </head>
  ```  

<img src="https://github.com/ggglyke/seo-cheat-sheet/blob/main/snippet.jpg?raw=true" alt="SERP Snippet" width="750"/>

  > - environ 160 caractères de long
  > - chaque page doit avoir un balise ```<meta name="description" content="">``` unique
  > - contenu non pris en compte pour le ranking
  > - un description bien écrite influence le taux de clic
  
  ### <a name="robotsTag">La balise meta robots</a>
  Elle indique pour une page donnée si celle-ci doit être indexée par les moteurs de recherche (= enregistrée ou non dans leur base de données) et si les moteurs de recherche doivent suivre les liens présents sur la page ou non
  
  ```xml
  <head>
    <meta name=”robots” content=”index, follow” />
  </head>
  ```
  
2 couples de valeurs possibles : [index, noindex] et [follow, nofollow]
  - index (default) : les moteurs sont autorisés à indexer (enregistrer) la page
  - noindex : les moteurs ne sont pas autorisés à indexer (enregistrer) la page
  - follow (default) : les moteurs vont suivre les liens présents sur la page
  - nofollow : les moteurs ne vont pas suivre les liens présents sur la page
  
 Il existe d'autres directives possibles dans cette balise : [Meta robots, maitrisez votre indexation avec cette balise (seo.fr)](https://www.seo.fr/definition/meta-robots)

## <a name="structure">Structure et navigation</a>
### <a name="html">Structure HTML globale</a>
Aujourd'hui, une structure HTML **sémantique** est un must pour chaque page web. La sémantique aide les moteurs de recherche à évaluer le contenu et à le proposer de la bonne manière aux utilisateurs. Il faut voir la structure sémantique comme la colonne vertébrale du site autour de laquelle s'articule tout le SEO.
1. utiliser les balises essentielles au SEO mentionnées ici
2. remplacer les ```<div>``` par les éléments sémantiques lorsque cela est possible : ```<header>, <nav>, <main>, <aside>, <article>, <footer>``` etc.
### <a name="url">Structure des URLs</a>
Les URLs sont une version humainement lisible des adresses IP des serveurs où sont hébergées les pages. Les moteurs de recherche les utilisent pour déterminer la pertinence d'une page par rapport à une requête de recherche. Elles sont donc importantes pour le référencement.

1. utiliser des URLs **courtes** et pertinentes. Idéalement avec des mot-clés
2. lorsqu'un utilisateur ou un moteur de recherche lit une URL, il doit savoir à quoi s'attendre à lire comme contenu
3. utiliser uniquement des **tirets** pour séparer les mots
4. utiliser uniquement des **minuscules**, sans caractères spéciaux
5. utiliser une **structure de répertoires** claire et simple

URL non optimisée :

```https://www.myhomepage.com/blog/title/2379118/?ref_=ttep_ep1```

URL optimisée :

```https://www.myhomepage.com/shop/trainers/adidas/red-trainers-MB-6400TN```
