# Steps to build test site

## Prerequisites

Windows host:
  * Install WSL: [How to install WSL 2 on Windows 11](https://www.youtube.com/watch?v=eId6K8d0v6o)
  * Update kernel and install Ubuntu LTS
    >wsl --update
    
    >wsl --install Ubuntu
  
  * Continue with Ubuntu host instructions

Ubuntu host: 
* Install docker engine: [Install Docker Engine on Ubuntu | Docker Docs](https://docs.docker.com/engine/install/ubuntu/) 
* Install lando: [Installation | Lando](https://docs.lando.dev/getting-started/installation.html)

MacOS host:
* WIP

## Get core files

* Clone the repo [lcapriottiunicef/uniceftest (github.com)](https://github.com/lcapriottiunicef/uniceftest) 

## Start services

> lando start

## Configure Drupal site

Open [https://uniceftest.lndo.site/](https://uniceftest.lndo.site/) - you will be redirected to the Drupal installer

Specify the following values in the installer:

|Setup Database    |Values                                     |
|------------------|-------------------------------------------|
|Language          |`English`                                  |
|Profile           |`Demo: Umami Food Magazine (Experimental)` |
|Database name     |`drupal10`                                 |
|Database username | `drupal10`                                |
|Database password | `drupal10`                                |
|(Advanced) Host   | `database`                                |

|Configure site    |Values                                     |
|------------------|-------------------------------------------|
|Site email        |`<any>`                                    |
|Username          |`admin`                                    |
|Password          |`admin`                                    |
|Email address     | `<any>`                                   |
|Default country   | `United States`                           |

# Adding dependencies

It is good practice to manage Drupal dependencies using Composer instead of manually adding or removing the code.

Remember every time you need to add a new module, all you need to do is run:

>lando composer require `drupal/<modulename>`

If at some point we need to delete some module from the codebase, we'd need to run:

> lando composer remove `drupal/<modulename>`

## Running drush

To run drush commands, all you need to do is prepend the word lando to every normal command, for example:

-   To install modules:

> lando drush en devel `<modulename>`

-   To uninstall modules:

> lando drush pmu `<modulename>`

-   To rebuild drupal caches:

> lando drush cr

# Credits

[Working with Drupal in Lando (evolvingweb.com)](https://evolvingweb.com/working-drupal-lando)
