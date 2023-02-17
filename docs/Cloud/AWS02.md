Configuration du Compte AWS

Lors dr la premieres inscription à AWS, vous vous connectez initialement en tant qu'utilisateur root. Ce compte d'utilisateur a un accès complet, donc du point de vue de la sécurité, je vous recommande de l'utiliser uniquement pour créer d'autres comptes d'utilisateurs avec des autorisations plus limitées.


Pour créer un compte d'utilisateur AWS limité :

- Se rendre sur la console du service [Identity Access Management (IAM)](https://console.aws.amazon.com/iam/home) 
- Cliquer sur ```Users```, puis sur le bouton bleu ```Add User```.

![AWS02-01](img/AWS02-01.jpg)

- Saisir un nom pour l'utilisateur. Par exemple : ```terraform-user```.
- Cliquer sur le bouton ```Next``` :

![AWS02-02](img/AWS02-02.jpg)

-  Cocher la case  ```Attach policies directly```,
-  Choisir la policy déjà pré-configurée d'AWS nommée ```AmazonEC2FullAccess```,
-  Cliquer sur "Next"

![AWS02-03](img/AWS02-03.jpg)

- Vérifier les informations
- Cliquer sur ```Create user```

![AWS02-04](img/AWS02-04.jpg)

- Le message suivant s'affiche 

![AWS02-05](img/AWS02-05.jpg)

Pour créer une clé d'accès :

- Accéder à [la liste des utilisateurs](https://us-east-1.console.aws.amazon.com/iamv2/home#/users)
- Selectionner l'utilisateur crée ( dans mon cas : ```terraform-user``` )

![AWS02-06](img/AWS02-06.jpg)

- Sélectionner l'onglet ```Security credentials```
- Cliquer sur ``` Create Access Key ```

![AWS02-07](img/AWS02-07.jpg)

- Choisir le cas d'utilisation de la clé d'accès ( J'ai choisit ```Local code```), Ensuite cocher la case en bas et cliquer sur ```Next```.
- Décrire le cas d'utilisation de la clé ( J'ai écrit Terraform )
- Cliquer sur ``` Create access key ```

![AWS02-08](img/AWS02-08.jpg)

- Il faut Copier le ``` Secret access key ``` dans un endroit sûr parce qu'il n'est visible qu'une seule fois.

![AWS02-09](img/AWS02-09.jpg)

- L'utilisateur est dorénavant prêt à être utilisé