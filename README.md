# Featurisation d'Images pour l'entreprise Fruits


L'entreprise Fruits! souhaite créer un modèle de reconnaissance de fruits. Il met à disposition un jeu de données d'images (https://www.kaggle.com/moltean/fruits) de fruits pour entraîner un modèle. On effectue dans ce notebook l'étape de prétraitement des images en aval de l'entraînement du modèle. Cette étape se décompose en deux parties :
• une featurisation des images,
• une réduction de dimensions de l'espace de plongement.

La featurisation des images est effectuée avec le réseau de neuronnes convolutif (CNN) pré-entrainé Resnet50, développé par TensorFlow. La réduction des images est effectuée avec l'algorithme PCA. Ce pré-traitement permet de réduire la taille des données d'un facteur 120.

Étant donné le nombre important d'images à traiter (~6000 ou 300 Mo), la réduction dimensionnelle est une tâche lourde et nécessite la puissance du cloud. On utilse les ressources AWS EC2 (calcul) et S3 (stockage) pour effectuer cette tâche. Le code est écrit en Pyspark et est exécuté sur DataBricks. 
La temps de calcul est dominé par la PCA, qui prend à peu près 15 heures à tourner sur un cluster de 8 workers i3.xlarge (de 30.5 GB et 4 cores chacun). 
