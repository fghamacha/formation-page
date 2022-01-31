# Lab 1 : Installation

Selon [la documentation officielle de Docker](https://docs.docker.com/engine/install/ubuntu/), Docker Engine peut être installé de différentes manières, selon nos besoins : 
-   La plupart des utilisateurs configurent les dépôt de Docker (Docker’s repositories) et les installent à partir de ceux-ci, pour faciliter les tâches d'installation et de mise à niveau. C'est l'approche recommandée. 

-   Certains utilisateurs téléchargent le package DEB, l'installent manuellement et gèrent les mises à niveau entièrement manuellement. Ceci est utile dans des situations telles que l'installation de Docker sur des systèmes isolés sans accès à Internet.

-   Dans les environnements de test et de développement, certains utilisateurs choisissent d'utiliser des scripts pratiques automatisés pour installer Docker.
## Linux 
Installation à l'aide de Repository :

Configurer le dépôt (Docker CE)
    Installez des packages pour permettre à apt d'utiliser un référentiel via HTTPS
Code block with title

```
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
``` 

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.
https://docs.docker.com/desktop/windows/install/ 

## Windows 10 / 11


## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.
