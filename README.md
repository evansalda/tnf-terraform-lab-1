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
- Accès à la [console](https://645860290752.signin.aws.amazon.com/console) du compte AWS dédié à votre formation
- Informations du tableau ci-dessous

| Nom             | Prénom       | AWS Console username      | AWS Console password | AWS Access key       | AWS Secret key                           | Digit |
|-----------------|--------------|---------------------------|----------------------|----------------------|------------------------------------------|-------|
| ARDOUIN         | Jean-Charles | jean-charles-ardouin      | 3gS}1$i9             | AKIAZMYCF6DAHXINWSZK | iqUl0KpmY1HbRdIc9cPMMmmRIhc7OSqHUp9o2c4Q | 01    |
| BAUDRY          | Samuel       | samuel-baudry             | s_3\|Y4+c            | AKIAZMYCF6DADI53CK5C | Ppy2iltkzIfowPzKAiCNxJ+iTv5uAr4jzMqQjRjO | 02    |
| BERNARD         | Christophe   | christophe-bernard        | n#O7dqC*             | AKIAZMYCF6DANCAT2LM3 | 3Ued67ZuyTCdW8/wLtdgo2o9lXrztuudZR8OOAI4 | 03    |
| BOUCHETA        | Mohamed      | mohamed-boucheta          | vZ9fB@^'             | AKIAZMYCF6DAMIVV5ZSI | bSTqxrQXGrHZHyh9LhIN506RIA4hyt+CBkuSXLtv | 04    |
| CUNHA DE ARAUJO | Jean-Paul    | jean-paul-cunha-de-araujo | Bk\|3G3%T            | AKIAZMYCF6DAMEF7FQMG | eavNq2GWzFIiZnGes83dEcTuHXei6HZRw7PLuqK6 | 05    |
| RIVIER          | Nicolas      | nicolas-rivier            | es5RpW5\|            | AKIAZMYCF6DAH5Z23IEU | TtngouyM25hCw5XD+kO3qJrig99CI0OHVocIkqVo | 06    |
| TAVERNIER       | David        | david-tavernier           | i(cB254+             | AKIAZMYCF6DACJOOZRPL | U4zeBmd1P7magFN/jrRJuDL2jC/xKhq0FXrK4NmI | 07    |

## Préparation de l'espace de travail

Sur votre poste de travail, créez un répertoire nommé nuumfactory-labs dans lequel vous créerez ensuite les répertoires suivants :

- mini-lab
- main-lab
- big-lab

**Vous travaillerez dans ce répertoire tout au long du module.**

# Installation de terraform

Installez **terraform** sur votre poste de travail en suivant les indications de la [documentation](https://developer.hashicorp.com/terraform/install).

Si vous êtes sous Windows, n'oubliez pas d'ajouter le binaire téléchargé à votre **Path**.

## Test d'utilisation

- Dans le menu **Démarrer**, tapez « Powershell » puis cliquez sur **Windows PowerShell**

- Sur le terminal PowerShell, exécutez la commande **terraform**. Vous devriez obtenir un résultat similaire à celui-ci-dessous :

<p align="left">
<img src="img/terraform-output.jpg"/>
</p>