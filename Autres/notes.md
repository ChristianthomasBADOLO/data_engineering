# REST API
Le **REST API** est bien une **architecture de communication légère** entre différentes applications, qui respecte un certain formalisme basé sur le protocole **HTTP**. Ce formalisme permet aux systèmes de s’échanger des informations de manière standardisée, tout en restant simple et flexible.

Voici une synthèse des points clés :

1. **Architecture** : REST (Representational State Transfer) définit un ensemble de règles que les développeurs suivent pour structurer leurs APIs. C'est une façon d'organiser la communication entre un **client** (comme une application web ou mobile) et un **serveur**.
   
2. **Légèreté** : REST est léger car il repose sur les verbes et les fonctionnalités déjà existants du protocole **HTTP** (comme `GET`, `POST`, `PUT`, `DELETE`), et n'ajoute pas de surcouches complexes. Les données échangées sont souvent en **JSON**, un format très léger et facile à utiliser.

3. **Formalisme** : REST définit des principes de communication que les applications doivent suivre :
   - **Utilisation des verbes HTTP** pour définir l’action à effectuer (ex. : `GET` pour récupérer des données, `POST` pour en envoyer, etc.).
   - **Représentation des ressources** via des **URLs** claires et logiques (ex. : `http://monapi.com/users` pour accéder à la ressource “utilisateurs”).
   - **Stateless** (sans état) : chaque requête est indépendante et contient toutes les informations nécessaires, le serveur ne garde pas de mémoire d'une requête à l'autre.

4. **Interopérabilité** : REST API est indépendant de la technologie ou du langage utilisé par les applications. Cela signifie qu'une application écrite en **Python** peut facilement communiquer avec un serveur développé en **Java** via un REST API, tant qu'ils respectent le même formalisme.

### Pourquoi REST API est léger et populaire :
- **Facile à comprendre** : Grâce à l'utilisation des verbes HTTP et à une structure d'URL intuitive, les API REST sont simples à utiliser et à implémenter.
- **Pas de surcharge** : Il n'y a pas de surcharge supplémentaire comme dans d'autres architectures plus lourdes (par exemple, SOAP).
- **Flexibilité** : REST permet à des applications de s’échanger des données dans différents formats (JSON, XML, etc.), mais JSON est souvent privilégié pour sa légèreté.

# SDK
Un SDK (Software Development Kit) est un ensemble d'outils, de bibliothèques et de documentations mis à disposition par une entreprise ou une plateforme pour permettre aux développeurs de créer des applications ou des fonctionnalités spécifiques sur une plateforme donnée.

# BLOBs
Les bases de données BLOBs (Binary Large Objects) sont des types de données qui permettent de stocker de grandes quantités d'informations sous forme de fichiers binaires dans une base de données. Cela inclut des fichiers tels que des images, des vidéos, des documents ou tout autre contenu non structuré.
En termes simples, c'est comme une "boîte" dans la base de données où tu peux déposer des fichiers lourds et de formats variés, un peu comme stocker un fichier dans un dossier sur ton ordinateur, mais à l'intérieur de la base de données.

# .NET
.NET est une plateforme de développement créée par Microsoft qui permet de construire et d'exécuter des applications sur plusieurs systèmes d'exploitation (Windows, macOS, Linux) et pour différents types d'appareils (ordinateurs, serveurs, mobiles, etc.). Elle fournit un ensemble d'outils, de bibliothèques et de langages de programmation qui facilitent le développement d'applications robustes et performantes.