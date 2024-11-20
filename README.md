# Hackademia 2024 - UNIGE
22-23 november 2024 à Battelle, Genève - https://www.unige.ch/hackademia/

## Informations sur le projet proposé
  * Titre : **Exploiter les techniques d’Intelligence Artificielle pour développer le nouvel outil de recherche de la Bibliothèque**
  * Porteurs du projet : **Pablo Iriarte** (pablo.iriarte@unige.ch) & Nicolas Prongué (nicolas.prongue@unige.ch), Division de l'Information Scientifique (DIS), UNIGE
  * Participants :
    * Abdoulaye Kadiatou Diallo
    * [à compléter]
  * Présentation : https://hackademia2024.sparkboard.com/project/6707a0c9b4a7d2d858f2f31c

## Résumé

**Quel problème tentez-vous de résoudre?**  
La recherche de documents dans swisscovery - l’outil de découverte de la Bibliothèque de l’UNIGE - n’est pas une chose aisée, la masse exponentielle d’informations à disposition provoque une quantité de bruit qui pose des problèmes aux algorithmes de classement par pertinence. En outre, notre moteur de recherche actuel n’est pas capable de traiter les recherches en langage naturel ce qui le rend obsolète au vu de l’explosion d’outils d’intelligence artificielle de plus en plus présents dans nos vies. Plusieurs bibliothèques dans le monde commencent à développer des assistants, souvent en utilisant ChatGPT comme « Large Language Model » (LLM) ce qui pose de problèmes de confidentialité et des risques de fournir des réponses inexistantes. Certains outils permettent la génération des réponses de type synthèse en fonction des meilleurs résultats trouvés, ce qui est intéressant mais réducteur dans le contexte de la recherche académique.
La recherche de documents dans swisscovery - l’outil de découverte de la Bibliothèque de l’UNIGE - n’est pas une chose aisée, la masse exponentielle d’informations à disposition provoque une quantité de bruit qui pose des problèmes aux algorithmes de classement par pertinence. En outre, notre moteur de recherche actuel n’est pas capable de traiter les recherches en langage naturel ce qui le rend obsolète au vu de l’explosion d’outils d’intelligence artificielle de plus en plus présents dans nos vies. Plusieurs bibliothèques dans le monde commencent à développer des assistants, souvent en utilisant ChatGPT comme « Large Language Model » (LLM) ce qui pose de problèmes de confidentialité et des risques de fournir des réponses inexistantes. Certains outils permettent la génération des réponses de type synthèse en fonction des meilleurs résultats trouvés, ce qui est intéressant mais réducteur dans le contexte de la recherche académique.

**Quelle est la solution que vous proposez pour le résoudre?**  
Le développement rapide des LLMs ouverts et des techniques d’IA open source nous permettraient de créer un outil de recherche innovant, capable de traiter les questions rédigées en langage naturel, de différencier le type de recherche en fonction des termes utilisés et de donner des résultats précis et pertinents. C’est par ce biais que nous pouvons faciliter l’appropriation de la collection à nos publics et développer l’outil de recherche du futur !
Le développement rapide des LLMs ouverts et des techniques d’IA open source nous permettraient de créer un outil de recherche innovant, capable de traiter les questions rédigées en langage naturel, de différencier le type de recherche en fonction des termes utilisés et de donner des résultats précis et pertinents. C’est par ce biais que nous pouvons faciliter l’appropriation de la collection à nos publics et développer l’outil de recherche du futur !

**Comment pensez-vous procéder pour arriver à cette solution?**  
Nous aimerions utiliser différentes techniques d’IA comme le « Retrieval-Augmented Generation » (RAG) ou le « Fine-Tuning » en utilisant l’un des LLMs ouverts qui existent (LLaMA, BLOOM, BERT, etc.). Ces techniques peuvent être appliquées au corpus de notre collection, ainsi qu’au traitement des termes utilisés par la personne qui recherche des documents. Nous mettons à disposition les données bibliographiques de tous les documents de la collection de la bibliothèque (les métadonnées de plusieurs millions de livres) augmenté avec les différents référentiels qui sont liés (Linked Open Data) comme la classification Dewey et les sujets IdRef. Les étapes envisagés pour ce développement sont :

1. Conception de l’architecture de l’outil et de la typologie des recherches (conceptuelle, thématique, d’un document connu, d’un auteur connu, etc.)
2. Choix du ou des LLMs ouverts et appropriés pour les différents besoins
3. Traitement des données bibliographiques et vectorisation à l’aide de NLTK (python)
4. Entrainement du modèle pour la tâche de classement des critères de recherche selon la typologie définie (fine-tuning)
5. Utilisation des APIs de swisscovery et du modèle entrainé pour mettre en place le RAG permettant de fournir une réponse sourcée
6. Mise ne place d’un prototype d’assistant capable de répondre à tous les types de recherche et de fournir les références et les liens des documents trouvés

