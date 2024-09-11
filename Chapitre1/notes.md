<details>
<summary>Chapitre 1 - Introduction au Data Engineering et Bash + Vim (0/16)</summary>

-  Introduction au Data Engineering : Aperçu général et historique
-  Concepts clés : Différences entre Data Engineer, Data Scientist, Data Analyst, etc.
-  Parcours professionnel en Data Engineering
-  Collaboration entre les différents rôles data
-  Comparaison : Data Engineering vs Data Science
-  Outils et utilisation des données en entreprise
-  Évaluation de la maturité d'un projet Data
-  Rôle de l'IA, des LLM et du Data Engineering
-  Introduction à la modélisation des données
-  Systèmes distribués : fonctionnement et avantages
-  Scale Up vs Scale Out : stratégies de mise à l'échelle
-  Design Pattern d'une plateforme de données
-  Types de Data Pipelines : Batch et Streaming
-  Gestion de la qualité des données
-  Commandes Bash essentielles pour Windows/Mac
-  Introduction à l'utilisation de Vim
</details>


# Introduction au Data Engineering; Concepts clés 
Le data engineering est la discipline qui a pour but de developper des architectures pour la collecte le traitement et le stockages de grandes masses de données de diverses natures. Le data engineer permet au data scientist, analyst de ne pas "chercher une aiguille dans une bote de foin". Mettre en place des data plateformes pour permet l'acces à la bonne information grace à des data pipilines bien modlélisés(robuste et tolerant à la pane).

- Différence data engineer dev backend

    - Une approche fonctionnelle avec des frameworks pour le dev backend (logique côté servers) et plus une approche design en utilisant des outils dédiés du big data(choix des technologies) pour le data engineer.
    - Le data engineer va beaucoup plus loin dans ses architectures dans la mesure qu'il assure une supervision des pipelines qu'il developpe. Il a pour rôle d'assurer le flux de données tandis que le dev backend developpe et maintient de fonctionnalités côté serveur.

- Différences entre Data Engineer, Data Scientist, Data Analyst : le data engineer met en place des data plateformes pour permettre aux data scientist, analyst d'utiliser facielement la bonne information dans l'enorme masse de données de l'entreprise.


- De plus en plus le data engineer a pour mission de metre en production des modèles de machine learning. L'on tend vers un depassement de la fonction historique en faisant un peu du MLOps.


# Scale Up vs Scale Out : stratégies de mise à l'échelle :
- Scale Up (vertical) : Augmentation des ressources d'un seul serveur (CPU, RAM, stockage).
- Scale Out (horizontal) : Ajout de serveurs supplémentaires pour répartir la charge.


# Design Pattern d'une plateforme de données 
Un design pattern courant pour une plateforme de données comprend :
- Couche d'ingestion : Collecte des données de diverses sources
- Couche de stockage : Stockage des données brutes (data lake) et traitées (data warehouse)
- Couche de traitement : Transformation et analyse des données
- Couche de service : Exposition des données via API ou interfaces utilisateur


# Types de Data Pipelines : Batch et Streaming :
- Batch : Traitement périodique de grands volumes de données statiques.
- Streaming : Traitement continu des données en temps réel à mesure qu'elles arrivent.










# References

1. [Vidéo] (2022). *Qu'est-ce qu'un Data Engineer ?* [Vidéo en ligne]. YouTube. Disponible à : https://www.youtube.com/watch?v=IeyYWxaMP3M

2. [Article en ligne] (11 juillet 2022). *Qu'est-ce que le Data Engineering et pourquoi est-il si important ?* Organisation Performante. Disponible à : https://www.organisation-performante.com/quest-ce-que-le-data-engineering-et-pourquoi-est-il-si-important/
