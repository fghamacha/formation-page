# Vagrant Labs 
___
#### 1. VMware Workstation
___
###### Prerequis :
- Vagrant installé sur la machine hôte ==> https://www.vagrantup.com/downloads
- vmware utility installé  ==> https://www.vagrantup.com/vmware/downloads
- Installer VMware provider plugin avec la commande :
````
vagrant plugin install vagrant-vmware-desktop
````
###### Création de la VM :
Cloner le depôt :
```` 
git clone git@github.com:fghamacha/vagrant.git
````
accéder au dossier souhaiter et créer le VM en lançant la commande : 
````
vagrant up
````
!!! note " la création de la VM n'est pas instantanée, il faut vagrant download l'image de la VM depuis le site https://vagrantcloud.com "

###### Création de la VM :
Pour lancer powershell de la machine guest dans la machine hôte :
````
vagrant powershell
````
Lancer directement une commande powershell
````
vagrant powershell -c MaCommande
````

##### Détruire la VM

Pour détruire la VM :

````
vagrant destroy
````
___
#### 2. VMware ESXI
___

___
#### 3. VirtualBox
___