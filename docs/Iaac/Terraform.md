# Terraform Lab

1. Création du provider : 

il faut créer un fichier main.tf contenant le code suivant : 

````
provider "aws" {
    region = "eu-west-3" # La région de Paris
    access_key = "votre-clé-dacces"
    secret_key = "votre-clé-secrète"
}

````

2. Création de la ressource  :

````
resource "aws_instance" "my_ec2_instance" {
    ami = "ami-0a89a7563fc68be84" # Ubuntu server 20.04 LTS SSD volume type
    instance_type = "t2.micro" # 1vCPU 1 Go RAM - inclus dans l'offre gratuit de AWS
}

````

3. Creation de l'instance 

En combinant les exemples précédents, nous nous retrouvons avec le code suivant :

```
provider "aws" {
    region = "eu-west-3" # La région de Paris
    access_key = "votre-clé-dacces"
    secret_key = "votre-clé-secrète"
}

provider "aws" {
    region = "eu-west-3" # La région de Paris
    access_key = "votre-clé-dacces"
    secret_key = "votre-clé-secrète"
}

```

Depuis un terminal, accéder au dossier contenant fichier main.tf et exécuter la commande suivante :

```
terraform init

```
![Comming Soon](img/comingsoon.png)