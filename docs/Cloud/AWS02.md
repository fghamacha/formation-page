Configuration du Compte AWS

    Lors dr la premieres inscription à AWS, vous vous connectez initialement en tant qu'utilisateur root. Ce compte d'utilisateur a un accès complet, donc du point de vue de la sécurité, je vous recommande de l'utiliser uniquement pour créer d'autres comptes d'utilisateurs avec des autorisations plus limitées.


    Pour créer un compte d'utilisateur AWS limité, rendez-vous sur la console du service [Identity Access Management (IAM)](https://console.aws.amazon.com/iam/home) , cliquez sur "Users", puis sur le bouton bleu "Add User". Saisissez un nom pour l'utilisateur et assurez-vous de cocher l'option que "Programmatic access" afin de générer des clés d'accès que nous utiliserons tout au long de ce cours. Cliquez ensuite sur le bouton "Next:Permissions" :