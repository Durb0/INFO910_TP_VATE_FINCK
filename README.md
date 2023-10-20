# Rendu TP
Jules Finck & Thomas Vaté

## Setup

Avant de commencer, nous devons démarrer minikube avec un paramètre particulier:
`minikube start --static-ip 192.168.200.200`

L'ensemble de nos ressources sont dans un namespace. Le namespace s'appelle v-books, pour le créer, vous devez executer la commande suivante:
`kubectl apply -f namespace.yaml`

Pour gagner du temps, vous pouvez mettre le namespace v-books en tant que namespace par default pour l'ensemble des commandes qui vont suivre:
`kubectl config set-context --current --namespace=v-books`

Avant d'executer l'ensemble de nos ressources, nous avons besoin d'initialiser notre base de donnée.

pour initialiser la bdd : `kubectl create configmap mysql-initdb-config --from-file=./init.sql`

Nous pouvons maintenant executer l'ensemble de nos ressources via :
`kubectl apply -f . -R`

ouverture des ports de l'api : `kubectl port-forward service/api-service 8080:8080`

Pour acceder au front, vous devez acceder au service via minikube:
`minikube service front-service -n v-books`