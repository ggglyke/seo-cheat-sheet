# SEO cheat sheet
SEO recommandations for devs

### Sommaire
- [Balises html importantes pour le SEO](#tags)
  - [La balise title](#titleTag)
  - [La balise meta description](#descriptionTag)
  - [La balise de titre H1](#h1Tag)  
  - [La balise meta robots](#robotsTag)
  - [La balise canonical](#canonicalTag)
- [Les formulaires et le web invisible](#forms)
- [Les framework JavaScript modernes](#jsframework)
- [La duplication de contenu (à faire)](#duplicate)
- [Robots.txt et sitemap.xml](#robotsSitemap)
  - [Le fichier robots.txt](#robotsFile)
  - [Le fichier sitemap.xml](#sitemapFile)
- [Structure et navigation](#structure)
  - [HTML sémantique](#html)
  - [Hiérarchie des titres](#headings)  
  - [Structure des URLs](#url)
  - [Pagination](#pagination)  
- [Redirections](#redirects) 
- [Maillage interne (à faire)](#internalLinking)
- [Images](#images)
- [Performances (à faire)](#performance)
- [Gestion des langues (à faire)](#international)  

## <a name="tags">Balises html importantes pour le SEO</a>
### <a name="titleTag">La balise `<title>`
Peut-être la balise la plus importante de toutes. Son contenu apparait dans le titre de l'onglet du navigateur et dans le texte en bleu dans les résultats de recherche Google. Le contenu de la balise `<title>` n'est pas visible dans le contenu de la page, c'est une balise 'meta'. Voir la [balise h1](#h1tag) pour le titre principal

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
  
  La balise `<title>` doit :
- faire entre 50 et 70 caractères de long
- être présente sur chaque page
- être unique (différente sur toutes les pages)
- contenir les mots-clés importants pour la page (idéalement au début)

> un titre bien écrit influence le taux de clic
  
  ### <a name="descriptionTag">La balise meta description</a>
  Elle sert à décrire le contenu de la page. Elle apparait dans le texte en noir pour chaque résultat de recherche sur Google. Son contenu n'est pas pris en compte pour le SEO mais elle influence le taux de clic.
  
  ```xml
  <head>
    <meta name="description" content="Nantes : 296 annonces de location de bureaux à Nantes sur BureauxLocaux.com. Trouvez les bureaux de votre entreprise grâce à BureauxLocaux. Toutes les annonces immobilières pour les entreprises.">
  </head>
  ```  

<img src="https://github.com/ggglyke/seo-cheat-sheet/blob/main/snippet.jpg?raw=true" alt="SERP Snippet" width="750"/>

La balise `<meta name="description" content ="...">` doit :
- faire environ 160 caractères de long
- être présente sur chaque page indexable
- être unique (différente sur toutes les pages)
- décrire précisément le contenu de la page et inciter au clic

> Son contenu non pris en compte pour le ranking mais une description bien écrite influence le taux de clic

  ### <a name="h1tag">La balise `<h1></h1>`</a>
  Elle correspond au titre éditorial de la page. Visible dans le contenu, ce titre est le **titre principal** de la page. Il doit décrire le mieux possible le contenu de la page en utilisant les **mots-clés appropriés**.
  
```xml
<h1>Location du bureaux à Nantes (44000) - 216 annonces</h1>
```
  
  La balise `<h1>` doit :
  - être présente obligatoirement **une et une seule fois par page**
  - être **unique** (non dupliquée d'une page à l'autre)
  - décrire le contenu de la page précisément
  - contenir les mots-clés pertinents
  - avoir le même 'sens' que le contenu de la balise title, avec des mots-clés différents mais proches si possible
  
  ### <a name="robotsTag">La balise meta robots</a>
  Elle indique pour une page donnée si celle-ci doit être indexée par les moteurs de recherche (= enregistrée ou non dans leur base de données) et si les moteurs de recherche doivent suivre les liens présents sur la page ou non
  
  ```xml
  <head>
    <meta name=”robots” content=”index, follow” />
  </head>
  ```
  
2 couples de valeurs possibles : [index, noindex] et [follow, nofollow]
  - `index` (default) : les moteurs sont autorisés à indexer (enregistrer) la page
  - `noindex` : les moteurs ne sont pas autorisés à indexer (enregistrer) la page
  - `follow` (default) : les moteurs vont suivre les liens présents sur la page
  - `nofollow` : les moteurs ne vont pas suivre les liens présents sur la page
  
 Il existe d'autres directives possibles dans cette balise : [Meta robots, maitrisez votre indexation avec cette balise (seo.fr)](https://www.seo.fr/definition/meta-robots)
### <a name="canonicalTag">La balise canonical</a>

`<link rel="canonical" href="https://myhomepage.com" />`

Utiliser la balise canonical est un moyen d'indiquer à Google la copie originale d'une page donnée. La bonne utilisation de cette balise permet d'éviter les problèmes de contenu dupliqué.
- Par défaut, chaque page devra avoir une balise canonical pointant vers elle-même (self-canonical)
- Si la page B est une copie de la page A alors, la page B devra avoir une balise canonical pointant vers la page A
> Ne pas utiliser de balise canonical sur la pagination (erreur fréquente)
## <a name="jsframework">Les framework JavaScript modernes</a>
De nombreux sites utilisent aujourd'hui toutes les possibilités et les avantages que les frameworks JavaScript modernes comme React, Angular ou Vue proposent. Cependant, construire des sites web avec ces frameworks pose un **problème majeur pour le SEO : les moteurs de recherchent ne "voient" pas la structure html "normale"** nécessaire pour la bonne compréhension de son contenu. La plupart du temps, **uniquement une `<div>` vide est rendue** et présente dans le code source initial. Le framework se chargera d'appeler le reste du contenu et de construire le DOM qui ne sera pas vu par les moteurs de recherche.
> Aujourd'hui, les moteurs de recherche interprètent de mieux en mieux le JavaScript et les différents frameworks. Cependant, il faut partir du principe que les moteurs de recherche allouent un temps donné à l'exploration d'un site. Au-delà de ce temps, il quitte le site même s'il n'en a pas exploré tous les contenus. L'interprétation d'une page générée via JavaScript sera beaucoup plus gourmande en ressources que la lecture d'un simple code source en html.

Bonnes pratiques à mettre en place lors de l'utilisation d'un framework JavaScript :
- **mettre en place le SSR** (server-side rendering) : le serveur renvoit directement la version HTML de la page, lisible par les moteurs au moment du crawl.
- le pre(rendering peut être une alternative si le SSR est trop complexe à mettre en place
- Limiter la taille des bundles JavaScript. Les bundles de petite taille améliorent la vitesse de chargement, l'usage de mémoire et du processeur.
- Explorer les Chrome DevTools’ Timeline & JavaScript Profiler pour analyser l'impact du JavaScript.
## <a name="duplicate">La duplication de contenu</a>
### Duplication de la homepage
### Duplication http/https
### Duplication à cause du / (slash) de fin
### Duplication à cause des paramètres d'URL
### Duplication externe
Duplication externe = contenu identique sur plusieurs domaines différents.

Pour être efficace, un contenu doit être unique. Le copier-coller est un no-go absolu en terme de SEO.
Il faut être vigilant au contenu publié.
> Exemple : importer (copier-coller) les articles de medias dans une section "presse" n'aura aucun bienfait pour le SEO
## <a name="robotsSitemap">Robots.txt et sitemap.xml</a>
### <a name="robotsFile">Le fichier robots.txt</a>
➡️ Le fichier robots.txt indique les répertoires et pages autorisés ou non à l'exploration des moteurs de recherche.

- Il est le premier fichier consulté par les crawlers avant d'accéder aux contenu d'un site.
- Il doit être situé à la racine du site : `https://www.example.com/robots.txt`
- Il va permettre de donner des **instructions de crawl** aux robots. 

La première ligne concerne l'identification des robots concernés par les règles qui vont suivre. Les crawlers sont identifiés grâce à leur `user-agent`

Il est possible de donner des instructions différentes en fonction du crawler qui passe sur le site :

- `user-agent: *` : les règles s'appliqueront à tous les robots
- `user-agent: Googlebot` : les règles ne s'appliqueront qu'à Googlebot

Les directives `Allow` et `Disallow` :
- `Allow: /` : autorise l'accès à tout le site
- `Disallow: /` : interdit l'accès à tout le site
- `Allow: /directory` : autorise l'accès à tout le répertoire 'directory'
- `Disallow: /directory` : interdit l'accès au répertoire 'directory'

Les règles se cumulent, c'est à dire qu'on peut interdire l'accès à tout un site sauf un répertoire précis :
```txt
User-agent: *
Disallow: /
Allow: /directory
```

**❗ IMPORTANT : On indique l'adresse du fichier sitemap.xml de cette manière à la fin du fichier robots.txt :**

`Sitemap: https://www.example.com/sitemap.xml`

Exemple de fichier robots.txt par défaut sur Wordpress :
```text
User-agent: *

# On empêche l'indexation des dossiers sensibles
Disallow: /wp-admin
Disallow: /wp-includes
Disallow: /wp-content/plugins
Disallow: /wp-content/cache
Disallow: /trackback
Disallow: /*.php$
Disallow: /*.inc$
Disallow: /*.gz$

# On désindexe la page de connexion (contenu inutile)
Disallow: /wp-login.php

Sitemap: https://www.example.com/sitemap.xml
```
Le fichier robots.txt propose de nombreuses options et subtilités que nous n'allons pas détailler ici. Pour plus d'infos, rendez-vous sur cet article : https://smartkeyword.io/seo-technique-seo-robots-txt/

L'expert SEO fera des recommandations sur la manière de remplir correctement ce fichier.

### <a name="sitemapFile">Le fichier sitemap.xml</a>
➡️ Le fichier sitemap.xml communique l'ensemble des URLs indexables aux moteurs de recherche. 

Il doit être accessible à la racine du site, idéalement à cette adresse : `https://www.example.com/sitemap.xml`. Si ça n'est pas le cas, une redirection `301 redirect permanent` sera à mettre en place pour rediriger `.sitemap.xml` vers cette url.

Le fichier sitemap.xml peut ensuite être soumis directement à Google via Google Search Console
#### Syntaxe du fichier sitemap.xml :
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>http://www.example.com/foo.html</loc>
    <lastmod>2019-06-04</lastmod>
  </url>
  <url>
    <loc>http://www.example.com/foo-bar.html</loc>
    <lastmod>2019-06-04</lastmod>
  </url>
</urlset>
```
- `urlset` : encapsulation de l'ensemble des URLs
- `loc` : URL absolue de la page répondant en **`HTTP 200 OK`**
- `lastmod` : date de dernière modification

❗ ATTENTION : un fichier sitemap ne peut pas contenir plus de 50 000 URLs. Dans ce cas, utiliser un index de sitemaps.
#### Index de sitemaps
Lorsque le site comporte un très grand nombre de pages ou lorsqu'il en compte plus de 50 000, l'index de sitemaps devient indispensable. Il faut alors créer des fichiers sitemaps différents (par catagories par exemple) et les lier dans un fichier `sitemapindex` :
```xml
<?xml version="1.0" encoding="UTF-8"?>
<sitemapindex xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <sitemap>
    <loc>https://example.com/sitemap1.xml</loc>
    <lastmod>2019-01-01T18:23:17+00:00</lastmod>
  </sitemap>
  <sitemap>
    <loc>https://example.com/sitemap2.xml</loc>
    <lastmod>2019-01-01</lastmod>
  </sitemap>
</sitemapindex>
```
#### Les images dans le sitemap
Pour faciliter l'exploration des images, on peut aussi les inclure dans le sitemap. C'est une action recommandée lorsque l'enjeu SEO est important autour des images pour le site. La syntaxe est simple, comme pour le fichier `sitemap.xml` classique, chaque URL (`<loc>`) est associée aux images intégrées sur celle-ci (`<image:image>`) :
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"
        xmlns:image="http://www.google.com/schemas/sitemap-image/1.1">
  <url>
    <loc>http://example.com/sample.html</loc>
    <image:image>
      <image:loc>http://example.com/image.jpg</image:loc>
    </image:image>
    <image:image>
      <image:loc>http://example.com/photo.jpg</image:loc>
    </image:image>
  </url> 
</urlset> 
```
#### Les pages à y inclure, celles à exclure
De manière générale on y intègre toutes les pages que l'on souhaite voir indexées sur les moteurs de recherche.

Dans le fichier sitemap, exclure :
- la pagination au-delà de la 1ère page
- les pages de la section privée (avec formulaire de connexion)
- les URLs avec paramètres (s'il existe des équivalents avec URL clean)
- les pages "pauvres" (profil, attachement, dossier de redirections, login, logout...)

## <a name="forms">Les formulaires et le web invisible</a>
Le "web invisible" désigne en fait l'ensemble des contenus non accessibles aux moteurs de recherche. Il peut s'agir de contenus volontairement masqués aux robots car payants (abonnement), restreints (mot de passe), ou non accessibles grâces à différentes directives (robots.txt, meta robots etc.).

La plupart des contenu non accessibles ne le sont pas volontairement. Les robots d'exploration n'ont tout simplement pas les moyens de les crawler car ils sont accessibles derrière un formulaire.

Un robot d'exploration ne rempli ni ne valide les formulaire sur le web. Google ne précise pas la taille de l'appartement qu'il veut acheter comme nous le précise [Oseox](https://oseox.fr/referencement/formulaire-referencement.html).

En définitive, les contenus qui sont accessibles uniquement après validation d'un formulaire sont parfaitement invisibles. L'exploration de ces contenus n'aura jamais lieu et le site ne se positionnera jamais grâce à ces contenus.

Exemple : sur un site immobilier, les annonces ne sont accessibles qu'après une recherche avec le module de recherche du site. Google ne verra jamais les annonces.

Solutions :
- **Utiliser le maillage interne pour rendre les contenus accessibles via des liens hypertextes** (ex : un lien vers la page "achat appartement Nantes" existe)
- Ne pas utiliser les éléments de formulaire à la place des liens (un `<button>` n'a pas du tout le même rôle qu'un `<a>`)
- Intégrer les contenus derrière les formulaires au sitemap xml pour offrir un second chemin de navigation en plus du maillage interne
- Ne pas utiliser des éléments de formulaires pour charger la pagination (un `<button>` "Plus de résultats" ne sera jamais déclenché, les items resteront inaccessibles)
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
### <a name="pagination">Pagination</a>
Un système de pagination efficace est indispensable pour un bon SEO. Celui-ci permettra aux robots et aux internautes d'accéder aux contenus les plus profonds en un **minimum de clics**.

**Recommandation : pagination numéraire** :

Sur une page n, on présentera les liens hypertextes vers les pages (quand elles existent) n-30, n-20, n-10, n-3,n-2, n-1, n+1,n+2,n+3,n+10, n+20,n+30. Les URLs de ces pages existent et son réécrites correctement (voir point suivant)

#### Bonnes pratiques sur les pages de listing :
- les balises `<title>` et `<h1>` des pages de la série mentionnent le numéro de la page courant pour éviter la duplication (sauf page 1)
- un emplacement est prévu pour un **texte de 500 à 1500 mots sur la 1ère page de la série** uniquement
- les URLs sont réécrites sans paramètre
- toutes les pages de la série doivent être en `index, follow`
- toutes les pages de la série ont une balise `canonical` pointant vers elles-mêmes (self referencing canonical)
- Google a indiqué ne plus prendre en compte les directives `rel="prev"` et `rel="next"`, il n'est donc plus obligatoire de les utiliser

**A éviter** :
- les systèmes '< précédent - suivant >' (contenus profonds inaccessibles)
- lazy-loading (JS très mal interprété par les moteurs)
- les boutons 'charger la suite' déclenchant un script Javascript
> On peut proposer ses systèmes **en plus** de la pagination numéraire par liens hypertextes mais il ne doivent en aucun cas être les seuls moyens de naviguer.

Exemple de pagination **non optimisée** : **les contenus sont inaccessibles** à cause du bouton en JS:
<img src="https://github.com/ggglyke/seo-cheat-sheet/blob/main/pagination-gdc.jpg?raw=true" alt="pagination" width="500"/>

Exemple de pagination **optimisée** : liens hypertextes et contenus profonds accessibles aisément :
<img src="https://github.com/ggglyke/seo-cheat-sheet/blob/main/pagination.jpg?raw=true" alt="pagination" width="500"/>


#### URLs de pagination
Les URLs des pages de listing doivent être 'propres' et facilement compréhensibles. On utilisera donc la **réécriture d'URL** pour masquer les paramètres s'ils sont utilisés à la base.

Une URL de pagination non optimisée :
`https://www.bureauxlocaux.com/location/nantes/?page=3&offset=20`

Une URL de pagination optimisée :
`https://www.bureauxlocaux.com/location/nantes/page/3/`

> la page 1 doit toujours avoir la même url : idéalement `/location/nantes/` ou `/location/nantes/page/1` mais jamais les 2 à la fois (prévoir une redirection si c'est le cas)

## <a name="redirects">Redirections</a>
Les redirections permanentes `301 Moved Permanently` ou temporaires `302 Found` sont **indispensables en SEO** pour indiquer aux moteurs de recherche les nouvelles URLs des pages qui auraient migrées. En effet, les moteurs de recherchent gardent les URLs en mémoire et leur attribut un certain **'score' SEO**. Si une page change d'URL et que rien n'est fait alors celle-ci perd tout son potentiel SEO. Les redirections ont pour objectif de permettre la **transmission d'une partie de ce potentiel** aux nouvelles pages.

Dans quels cas utiliser les redirections ?
  - lors d'une refonte, lorsque les URLs sont modifiées
  - lorsqu'un produit n'est plus en stock
  - lorsqu'un contenu est modifié/déplacé
  
**Maillage interne = `200 OK` liens externes = redirections**

Les redirections sont utiles pour les moteurs de recherche qui ont les URLs en mémoire, comme pour les liens externes pointant vers votre site ou les internautes qui tentent d'accéder directement à un contenu. Ceux-ci vont alors solliciter une URL qui n'existe plus, ils vont donc devoir passer par la redirection pour arrivé au contenu demandé.
Au sein du site, aucun lien ne devrait pointer vers une page en redirection (temporaire ou permanente). Les URLs courantes sont connues et stables donc le maillage interne doit pointer uniquement vers des pages en statut http `200 OK`
## <a name="internalLinking">Maillage interne</a>
## <a name="images">Images</a>
Les images peuvent avoir plus ou moins d'importance pour le SEO. Pour un photographe, un site immobilier ou un site comme Pinterest, les images représentent un enjeu stratégique. Elle ne sont donc pas à négliger lors du développement web.

Comment optimiser ses images pour le SEO :
- [performance] images **à la bonne taille** : charger autant que possible les images à leur taille d'affichage en px (et non en taille XL redimensionnée en css)
- [performance] **optimiser ses images** : réduire le poids en `ko` en préservant le même niveau de qualité
- [performance] versions multiples de la même image pour son affichage responsive (grâce à l'attribut **`srcset`**)
- [performance] formats d'image nouvelle génération (JPEG 2000, JPEG XR et WebP)
- [performance] si l'enjeu est grand, utiliser un **CDN** pour les images (attention à bien le configurer pour que celles-ci soient indexables)
- [accessibilité] **attribut `alt=""`** sur chaque image importante et décrire son contenu comme vous le feriez à une personne malvoyante.
- [accessibilité] utiliser un nom de fichier compréhensible, qui permette d'identifier le contenu de l'image
- [contenu] le **contexte** autour de l'image est important. Placer les images dans un contexte qui permette aux moteurs de recherche de comprendre l'image (paragraphe, légende, commentaires...)
## <a name="performance">Performances</a>
## <a name="international">Gestion des langues</a>
---
Sources : 
- https://oseox.fr/referencement/formulaire-referencement.html
- https://d2v4zi8pl64nxt.cloudfront.net/seo-cheat-sheet.pdf
- https://9elements.com/seo-cheat-sheet/
- https://wpmarmite.com/robots-txt-wordpress/
- https://smartkeyword.io/seo-technique-seo-robots-txt/
