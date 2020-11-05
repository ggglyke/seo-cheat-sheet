# SEO cheat sheet
SEO recommandations for devs

### Sommaire
- [Balises html importantes](#tags)
  - [La balise title](#titleTag)
  - [La balise meta description](#descriptionTag)
  - [La balise de titre H1](#h1Tag)  
  - [La balise meta robots](#robotsTag)
  - [La balise canonical](#canonicalTag)
- [Le problème des formulaires et contenus cachés (à faire)](#forms)
- [Problèmes fréquents avec les framework JavaScript modernes](#jsframework)
- [Robots.txt et sitemap.xml (à faire)](#robotsSitemap)
  - [Le fichier robots.txt (à faire)](#robotsFile)
  - [Le fichier sitemap.xml (à faire)](#sitemapFile)
- [Structure et navigation](#structure)
  - [HTML sémantique](#html)
  - [Hiérarchie des titres](#headings)  
  - [Structure des URLs](#url)
  - [Pagination (à faire)](#pagination)  
- [Maillage interne (à faire)](#internalLinking)
- [Images (à faire)](#images)
- [Performances (à faire)](#performance)
- [Gestion des langues (à faire)](#international)  

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
### <a name="canonicalTag">La balise `<link rel="canonical" href="..." />`</a>
Utiliser la balise canonical est un moyen d'indiquer à Google la copie originale d'une page donnée. La bonne utilisation de cette balise permet d'éviter les problèmes de contenu dupliqué.
- Par défaut, chaque page devra avoir une balise canonical pointant vers elle-même (self-canonical)
- Si la page B est une copie de la page A alors, la page B devra avoir une balise canonical pointant vers la page A

`<link rel="canonical" href="https://myhomepage.com" />`
> Ne pas utiliser de balise canonical sur la pagination (erreur fréquente)
## <a name="jsframework">Problèmes fréquents avec les framework JavaScript modernes</a>
De nombreux sites utilisent aujourd'hui toutes les possibilités et les avantages que les frameworks JavaScript modernes comme React, Angular ou Vue proposent. Cependant, construire des sites web avec ces frameworks pose un **problème majeur pour le SEO : les moteurs de recherchent ne "voient" pas la structure html "normale"** nécessaire pour la bonne compréhension de son contenu. La plupart du temps, **uniquement une `<div>` vide est rendue** et présente dans le code source initial. Le framework se chargera d'appeler le reste du contenu et de construire le DOM qui ne sera pas vu par les moteurs de recherche.
> Aujourd'hui, les moteurs de recherche interprètent de mieux en mieux le JavaScript et les différents frameworks. Cependant, il faut partir du principe que les moteurs de recherche allouent un temps donné à l'exploration d'un site. Au-delà de ce temps, il quitte le site même s'il n'en a pas exploré tous les contenus. L'interprétation d'une page générée via JavaScript sera beaucoup plus gourmande en ressources que la lecture d'un simple code source en html.

Bonnes pratiques à mettre en place lors de l'utilisation d'un framework JavaScript :
- **mettre en place le SSR** (server-side rendering) : le serveur renvoit directement la version HTML de la page, lisible par les moteurs au moment du crawl.
- le pre(rendering peut être une alternative si le SSR est trop complexe à mettre en place
- Limiter la taille des bundles JavaScript. Les bundles de petite taille améliorent la vitesse de chargement, l'usage de mémoire et du processeur.
- Explorer les Chrome DevTools’ Timeline & JavaScript Profiler pour analyser l'impact du JavaScript.
## <a name="forms">Le problème des formulaires</a>
## <a name="structure">Structure et navigation</a>
### <a name="html">Structure HTML sémantique</a>
Aujourd'hui, une structure HTML **sémantique** est un must pour chaque page web. La sémantique aide les moteurs de recherche à évaluer le contenu et à le proposer de la bonne manière aux utilisateurs. Il faut voir la structure sémantique comme la colonne vertébrale du site autour de laquelle s'articule tout le SEO.
1. utiliser les balises essentielles au SEO mentionnées ici
2. remplacer les ```<div>``` par les éléments sémantiques lorsque cela est possible : `<header>, <nav>, <section>, <main>, <aside>, <article>, <footer>`
### <a name="headings">Hiérarchie des titres</a>
Les titres et sous-titres des contenus doivent être structurés avec les balises sémantiques appropriées. Il s'agit des balises `<h1>, <h2>, <h3>, <h4>, <h5>, <h6>`. Elles sont importantes pour le SEO et l'utilisabilité du site. Voici quelques points à retenir
- Chaque page doit posséder **obligatoirement un et un seul** `<h1></h1>`
- Le contenu de la balise `<h1>` doit être pertinent par rapport à la page et utiliser des **mots-clés cohérents**
- Les balises de titres sont utilisées pour **structurer le contenu central** d'une page. On ne doit pas les retrouver dans les parties annexes (pas de `<hn></hn>` dans le header, menu principal, sidebar, footer etc.)
- Les balises de titre n'ont **pas pour rôle de styliser le contenu**, c'est le rôle d'un CSS bien conçu. (ne pas utiliser une balise titre pour obtenir un certain style)

Un exemple de structure de titres correcte :
```xml
<h1>Titre principal</h1>
  
  <h2>Titre de la section 1</h2>
   
    <h3>Sous-titre 1.1</h3>
   
    <h3>Sous-titre 1.2</h3>
  
  <h2>Titre de la section 2</h2>
    
    <h3>Sous-titre 2.1</h3>
    
    <h3>Sous-titre 2.2</h3>
```
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
## Redirections
Les redirections permanentes `301 Moved Permanently` ou temporaires `302 Found` sont **indispensables en SEO** pour indiquer aux moteurs de recherche les nouvelles URLs des pages qui auraient migrées. En effet, les moteurs de recherchent gardent les URLs en mémoire et leur attribut un certain **'score' SEO**. Si une page change d'URL et que rien n'est fait alors celle-ci perd tout son potentiel SEO. Les redirections ont pour objectif de permettre la **transmission d'une partie de ce potentiel** aux nouvelles pages.

Dans quels cas utiliser les redirections ?
  - lors d'une refonte, lorsque les URLs sont modifiées
  - lorsqu'un produit n'est plus en stock
  - lorsqu'un contenu est modifié/déplacé
  
**Maillage interne = `200 OK` liens externes = redirections**

Les redirections sont utiles pour les moteurs de recherche qui ont les URLs en mémoire, comme pour les liens externes pointant vers votre site ou les internautes qui tentent d'accéder directement à un contenu. Ceux-ci vont alors solliciter une URL qui n'existe plus, ils vont donc devoir passer par la redirection pour arrivé au contenu demandé.
Au sein du site, aucun lien ne devrait pointer vers une page en redirection (temporaire ou permanente). Les URLs courantes sont connues et stables donc le maillage interne doit pointer uniquement vers des pages en statut http `200 OK`
