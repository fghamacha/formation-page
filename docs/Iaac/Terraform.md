# Terraform Lab


Terraform est un outil qui permet de créer, modifier et versionner une infrastructure de manière sûre et efficace.

Il peut gérer différents fournisseurs d'infrastructure du Cloud Public (AWS, Azure, OVH, GcP, Alibaba Cloud, etc ...) ainsi que des solutions du cloud privé internes personnalisées (VmWare, Openstack, Kubernetes, etc ...)

Cette page est un tutoriel pour créer un première infrastructure cloud sur AWS avec terraform.

1. Prérequis

    Avant de commencer ce tutoriel, il faut s'assurer que les prérequis suivants sont présents : 

    === "AWS"

        - Avoir un compte AWS. Le compte peut être crée ici [https://aws.amazon.com/fr/free](https://aws.amazon.com/fr/free)
        - Terraform installé [https://developer.hashicorp.com/terraform/downloads](https://developer.hashicorp.com/terraform/downloads)
        - Créer La clé d'accès AWS [https://console.aws.amazon.com/iam](https://console.aws.amazon.com/iam)
        - Ce document détaille [La création de la clé d'accès sur AWS ](../../Cloud/AWS02).

    === "OVH"
        - Avoir un compte OVHCloud
        - Terraform installé [https://developer.hashicorp.com/terraform/downloads](https://developer.hashicorp.com/terraform/downloads)
        - Générer des identifiants depuis [cette page](https://www.ovh.com/auth/api/createToken?GET=/*&POST=/*&PUT=/*&DELETE=/*)

    === "Azure"
        ``` terraform title="Ce n'est pas encore disponible"


        ```

2. Création du premier code terraform : 

    Commençant par la création un fichier main.tf, dans un dossier vide,  contenant le code suivant : 

    === "AWS"

        ``` terraform title="Définir le cloud provider , la région et les codes d'accès à utiliser "

        # Ce code permet de 

        provider "aws" {
            region = "eu-west-1" # La région d'irlande'
            access_key = "ta-clé-dacces" #
            secret_key = "ta-clé-secrète"
        }
        ```

    === "OVH"

        ``` terraform title="Définir le cloud provider , la région et les codes d'accès à utiliser "

        provider "ovh" {
            endpoint           = "ovh-eu"
            application_key    = "saisir-application-key"
            application_secret = "saisir-application-secret"
            consumer_key       = "saisir-consumer-key"
        }
        ```

    === "Azure"
        ``` terraform title="Ce n'est pas encore disponible"


        ```
    

    Ensuite, ajouter ces lignes en dessous du code précedent dans le même fichier main.tf

    === "AWS"

        ``` terraform title="L'instance AWS à créer"

        resource "aws_instance" "my_ec2_instance" {
            ami = "ami-0a89a7563fc68be84" # Ubuntu server 20.04 LTS SSD volume type
            instance_type = "t2.micro" # 1vCPU 1 Go RAM - inclus dans l'offre gratuit de AWS
        }

        ```
    
    === "OVH"
        ``` terraform title="Ce n'est pas encore disponible"


        ```
    === "Azure"

        ``` terraform title="Ce n'est pas encore disponible"


        ```

3. Creation de l'instance 

    En combinant les exemples précédents, nous nous retrouvons avec le code suivant :

    === "AWS"

        ```` terraform title="main.tf"

        provider "aws" {
            region = "eu-west-1" # La région d'irlande'
            access_key = "votre-clé-dacces"
            secret_key = "votre-clé-secrète"
        }

        resource "aws_instance" "my_ec2_instance" {
            ami = "ami-0a89a7563fc68be84" # Ubuntu server 20.04 LTS SSD volume type
            instance_type = "t2.micro" # 1vCPU 1 Go RAM - inclus dans l'offre gratuit de AWS
        }
        ````
    === "OVH"
        ```` terraform title="Ce n'est pas encore disponible"
        
        ````

    === "Azure"

        ```` terraform title="Ce n'est pas encore disponible"
        
        ````

    Depuis un terminal, accéder au dossier contenant fichier main.tf et exécuter la commande suivante :

    ``` shell

    terraform init

    ```

    le output sera :  

    === "AWS"

        ``` terraform

        Initializing the backend...

        Initializing provider plugins...
        - Reusing previous version of hashicorp/aws from the dependency lock file
        - Using previously-installed hashicorp/aws v4.51.0

        Terraform has been successfully initialized!

        You may now begin working with Terraform. Try running "terraform plan" to see  
        any changes that are required for your infrastructure. All Terraform commands  
        should now work.

        If you ever set or change modules or backend configuration for Terraform,      
        rerun this command to reinitialize your working directory. If you forget, other
        commands will detect it and remind you to do so if necessary

        ``` 
    === "OVH"

        ```` terraform title="Ce n'est pas encore disponible"
        
        ````

    === "Azure"

        ```` terraform title="Ce n'est pas encore disponible"
        
        ````

    ''' terraform init''' demander à Terraform  de scanner le code pour déterminera le fournisseur utilisé et pour ensuite initier le projet avec les bons plugins terraform

    Un dossier .terraform est crée.

    Maintenant , il faut éxécuter la commande suivante pour crée un plan d'éxexution : 

    ``` terraform 

    terraform plan

    ```

    Le output est 

    === "AWS"

        ``` ps1 

        Terraform used the selected providers to generate the following execution plan.
        Resource actions are indicated with the following symbols:

        + create

        Terraform will perform the following actions:

        # aws_instance.my_ec2_instance will be created
        + resource "aws_instance" "my_ec2_instance" {
            + ami                                  = "ami-0a89a7563fc68be84"
            + arn                                  = (known after apply)    
            + associate_public_ip_address          = (known after apply)    
            + availability_zone                    = (known after apply)    
            + cpu_core_count                       = (known after apply)    
            + cpu_threads_per_core                 = (known after apply)    
            + disable_api_stop                     = (known after apply)    
            + disable_api_termination              = (known after apply)    
            + ebs_optimized                        = (known after apply)    
            + get_password_data                    = false
            + host_id                              = (known after apply)    
            + host_resource_group_arn              = (known after apply)    
            + iam_instance_profile                 = (known after apply)    
            + id                                   = (known after apply)    
        }

        ```
    === "OVH"

        ```` terraform title="Ce n'est pas encore disponible"
        
        ````
    === "Azure"

        ```` terraform title="Ce n'est pas encore disponible"
        
        ````

    ```Terraform plan``` n'est pas une commande obligatoire mais elle reste un excellent moyen de vérifier les modifications avant de les appliquer

    Maintenant, passant à la création de la ressource Terraform en exécutant la commande suivante :
    
    ``` shell title="Application du code"

    terraform apply
    
    ```

    Et pour en finir, saisir yes pour confirmer l'application du code terraform 

    ``` terraform title="résultat"
        Terraform used the selected providers to generate the following execution plan.
        Resource actions are indicated with the following symbols:
        + create

        Terraform will perform the following actions:

        # aws_instance.my_ec2_instance will be created
        + resource "aws_instance" "my_ec2_instance" {
        + ami                                  = "ami-0a89a7563fc68be84"  
        + cpu_threads_per_core                 = (known after apply)    
        + disable_api_stop                     = (known after apply)    
        + host_id                              = (known after apply)    
        + id                                   = (known after apply)    
        + instance_initiated_shutdown_behavior = (known after apply)
        + instance_state                       = (known after apply)
        + instance_type                        = "t2.micro"
        Plan: 2 to add, 0 to change, 0 to destroy.

        Changes to Outputs:
        + public_ip = (known after apply)

        Do you want to perform these actions?
        Terraform will perform the actions described above.
        Only 'yes' will be accepted to approve.

        Enter a value: yes
    ```

    La ressource a été bien deployée sur le founisseur cloud. il est possible de le vérifiant en se connectant à la console web du cloud Provider

    -   AWS :   [Console AWS](https://console.aws.amazon.com/ec2/v2/home)
    -   OVH :   [OVH Cloud](https://ovhcloud.com)
    -   Azure : [ Azure Portal](https://portal.azure.com)

    Si le message suivant s'affiche, penser à [créer un VPC par défaut](https://docs.aws.amazon.com/vpc/latest/userguide/default-vpc.html#create-default-vpc) dans la région choisie ( ici L'irlande)

    ``` terraform title="Message d'erreur VPC"
    Error: creating EC2 Instance: VPCIdNotSpecified: No default VPC for this user. GroupName is only supported for EC2-Classic  and default VPC.
    ```
4. Modifications des ressources:

    Terraform maintient un enregistrement de toutes les ressources qu'il a générées auparavant. Si une information est ajoutée, Terraform est capable de reconnaître l'existence d'une instance EC2 existante et de signaler les différences entre ce qui est actuellement déployé et les éléments présents dans le code Terraform. Pour démontrer cette fonctionnalité, il est possible de nommer une instance en créant une balise avec la clé "Name" et la valeur "terraform-001", ce qui se traduit par le code suivant :

    ``` terraform title="Modification des ressources"

    provider "aws" {
        region = "eu-west-1" # La région d'irlande'
        access_key = "votre-clé-dacces"
        secret_key = "votre-clé-secrète"
    }

    resource "aws_instance" "my_ec2_instance" {
        ami = "ami-0a89a7563fc68be84" # Ubuntu server 20.04 LTS SSD volume type
        instance_type = "t2.micro" # 1vCPU 1 Go RAM - inclus dans l'offre gratuit de AWS
        tags = {
            Name = "terraform-001"
        }
    }
    ```
    Exécutons ensuite le code :

    ``` terraform
    terraform init && terraform apply
    ```
    Output : 

    ```terraform

    Terraform used the selected providers to generate the following execution plan
    Resource actions are indicated with the following symbols:
    ~ update in-place
    Terraform will perform the following actions:
    # aws_instance.my_ec2_instance will be updated in-place
    ~ resource "aws_instance" "my_ec2_instance" {
        ~ tags                                 = {
            + "Name" = "terraform-001"
            }
        }
    Plan: 0 to add, 1 to change, 0 to destroy.
    Do you want to perform these actions?
    Terraform will perform the actions described above.
    Only 'yes' will be accepted to approve.

    Enter a value: yes

    aws_instance.my_ec2_instance: Modifying... 
    aws_instance.my_ec2_instance: Modifications complete after 1s
    Apply complete! Resources: 0 added, 1 changed, 0 destroyed.
    ```
5. Destruction de l'infrastructure

    Grâce à Terraform, le netoyage devient vraiment facile et rapide. il suffit de lancer la commande suivante dans le dossier où on a initier notre code:

    ``` terraform title="Netoyage"

    terraform destroy

    ```

    Les messages suivants s'affiche 

    ``` terraform title="destruction des ressources"

        Terraform will perform the following actions:

        # aws_instance.my_ec2_instance will be destroyed
        - resource "aws_instance" "my_ec2_instance" {
            ...
        }

        # aws_security_group.instance_sg will be destroyed
        - resource "aws_security_group" "instance_sg" {
            ...
        }

        Enter a value: yes

        aws_instance.my_ec2_instance: Destruction complete after 15s
        aws_security_group.instance_sg: Destruction complete after 2s

        Destroy complete! Resources: 2 destroyed.
    ```