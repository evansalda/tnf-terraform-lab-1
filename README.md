# Introduction

L’objectif de ce lab est de créer une infrastructure complète sur AWS à l’aide de l’outil **Terraform**. Cette infrastructure hébergera une application web que vous installerez et testerez à la fin de ce lab.

## L'infrastructure

L’architecture de l’infrastructure est la suivante :

<p align="left">
<img src="img/infrastructure.jpg"/>
</p>

Les ressources à créer seront :
- 1 x load-balancer pour accueillir les requêtes http clientes 
- 1 x VM EC2 qui fera office de serveur web en hébergeant l’application web 
- 1 x base de données MySQL pour stocker les données applicatives 
- 3 x security group pour sécuriser les flux vers le load-balancer, le serveur web et la BDD

## L'application

Il s’agit d’une simple page web sur laquelle le visiteur est invité à soumettre un nom et une adresse qui apparaitront ensuite dans un tableau :

<p align="left">
<img src="img/application.jpg"/>
</p>

## Prérequis

Avant de démarrer ce lab, assurez-vous de disposer des éléments suivants :
- Compte administrateur sur votre poste de travail
- Accès à la console du compte AWS dédié à votre formation
- Access key AWS
- Secret key AWS
- Digit (numéro unique)

## Préparation de l'espace de travail

Sur votre poste de travail, créez un répertoire nommé nuumfactory-labs dans lequel vous créerez ensuite les répertoires suivants :

- mini-lab
- main-lab
- big-lab

**Vous travaillerez dans ce répertoire tout au long du module.**

# Installation de terraform

## Téléchargement du binaire

Téléchargez le le fichier [terraform.exe](assets/terraform.exe) et placez-le à la racine du répertoire nuumfactory-labs.

A ce stade vous pouvez dès à présent utiliser terraform depuis votre interface de ligne de commande, pour cela vous devrez d'abord vous placer dans le répertoire qui contient le fichier terraform.exe. Afin de s’affranchir de cette contrainte, ajoutez ce répertoire dans la variable d’environnement **Path** de Windows :

- Depuis le menu **Démarrer**, tapez « variables » et sélectionnez **Modifier les variables d’environnement système**
- Au bas de la fenêtre qui s’ouvre, cliquez sur la case **Variables d’environnement…**
- Dans la section « Variables système », sélectionnez la variable **Path** et cliquez sur **Modifier…**
- Cliquez sur **Nouveau** puis sur **Parcourir…**, et sélectionnez le dossier qui contient votre fichier terraform.exe

Une fois cette opération effectuée, vous pourrez exécuter terraform depuis n’importe quel emplacement de votre poste de travail.

Pour information, le binaire de terraform est téléchargeable depuis le [site officiel](https://developer.hashicorp.com/terraform/downloads).

## Test d'utilisation

- Dans le menu **Démarrer**, tapez « Powershell » puis cliquez sur **Windows PowerShell**

- Sur le terminal PowerShell, exécutez la commande **terraform**. Vous devriez obtenir un résultat similaire à celui-ci-dessous :

<p align="left">
<img src="img/terraform-output.jpg"/>
</p>