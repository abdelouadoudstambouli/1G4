# Chapitre 4 - Virtualisation et création de machine virtuelle.

## Objectifs d'apprentissage&#x20;

* Expliquer le principe de la **virtualisation** et le rôle d’un **hyperviseur**&#x20;
* Distinguer les hyperviseurs de **type 1** et de **type 2**&#x20;
* Créer et configurer une **machine virtuelle Windows 11 avec VMware Workstation Pro**&#x20;
* Attribuer correctement les principales ressources d’une VM : **vCPU, RAM, stockage et réseau**&#x20;
* Préparer une machine virtuelle afin qu’elle puisse servir de **modèle (template)**&#x20;
* Créer et utiliser des **clones** d’une machine virtuelle afin de déployer rapidement plusieurs environnements de travail.

## 1. La virtualisation&#x20;

La **virtualisation** permet de faire fonctionner plusieurs machines virtuelles sur un même ordinateur physique.

Une **machine virtuelle**, ou **VM (Virtual Machine)**, se comporte comme un ordinateur normal, mais ses composants sont créés de façon logicielle.

Une VM possède par exemple :

* Un ou plusieurs processeurs virtuels (**vCPU**)&#x20;
* Une quantité de mémoire RAM&#x20;
* Un disque virtuel&#x20;
* Une carte réseau virtuelle&#x20;
* Son propre système d’exploitation.

On peut donc avoir, sur un même ordinateur physique, plusieurs systèmes d’exploitation qui fonctionnent en même temps.

Exemple :&#x20;

```
Ordinateur physique
Windows 11 (système hôte)
        │
        └── VMware Workstation Pro
                │
                ├── VM Windows 11
                ├── VM Ubuntu
                └── VM Windows Server
```

L’ordinateur physique sur lequel les machines virtuelles sont exécutées est appelé **machine hôte**.

Le système d’exploitation installé dans une machine virtuelle est appelé **système invité**.

### Pourquoi utiliser la virtualisation ?

La virtualisation est très pratique lorsqu’on veut travailler avec plusieurs systèmes sans avoir besoin de plusieurs ordinateurs physiques.

Elle permet par exemple de:

* Tester un autre système d’exploitation&#x20;
* Créer un environnement de laboratoire&#x20;
* Tester une configuration sans modifier directement son ordinateur&#x20;
* Créer plusieurs machines qui communiquent entre elles&#x20;
* Supprimer et recréer facilement une machine&#x20;
* Revenir à un état précédent en cas de problème.

### 1.1. Virtualisation des serveurs

La virtualisation est aussi très utilisée dans les entreprises.

Au lieu d’acheter un serveur physique pour chaque service, on peut utiliser un serveur plus puissant et y créer plusieurs serveurs virtuels.

Par exemple :

```
Serveur physique
      │
      ├── VM Serveur Web
      ├── VM Serveur de fichiers
      └── VM Serveur DNS
```

Chaque machine virtuelle fonctionne alors comme un serveur indépendant.

Cette façon de faire permet entre autres de&#x20;

* Mieux utiliser les ressources disponibles&#x20;
* Réduire le nombre de serveurs physiques&#x20;
* Créer plus rapidement de nouveaux serveurs&#x20;
* Simplifier certaines opérations de sauvegarde ou de migration.

Pour créer et gérer ces machines virtuelles, on utilise un **hyperviseur**.

### 1.2. Types d'hyperviseurs&#x20;

Un **hyperviseur** est le logiciel qui permet de créer et de faire fonctionner les machines virtuelles.

C’est lui qui fait le lien entre la machine physique et les différentes VM.

Lorsqu’on crée une machine virtuelle, l’hyperviseur nous permet de choisir les ressources qu’on souhaite lui attribuer, par exemple :

* 2 processeurs virtuels
* 4 Go de RAM
* 60 Go de stockage
* Une carte réseau virtuelle.

Il existe principalement deux types d’hyperviseurs.

#### Hyperviseur de type 1

Un hyperviseur de **type 1**, aussi appelé **Bare Metal**, est installé directement sur le matériel physique.

Il n’a donc pas besoin d’un système d’exploitation classique comme Windows ou Ubuntu pour fonctionner.

```
┌─────────────────────────┐
│   Machines virtuelles   │
├─────────────────────────┤
│ Hyperviseur de type 1   │
├─────────────────────────┤
│   Matériel physique     │
└─────────────────────────┘
```

Ce type d’hyperviseur est surtout utilisé sur des serveurs.

Quelques exemples : VMware ESXi,  Microsoft Hyper-V, Proxmox VE&#x20;

Dans ce cours, nous allons surtout nous intéresser au deuxième type.

#### Hyperviseur de type 2

Un hyperviseur de **type 2** est un logiciel installé sur un système d’exploitation déjà présent sur l’ordinateur.

Par exemple, on peut avoir un ordinateur sous Windows 11 et installer VMware Workstation dessus.

```
VM Windows      VM Ubuntu
      │             │
      └──────┬──────┘
             │
     VMware Workstation
             │
         Windows 11
             │
      Matériel physique
```

Dans cet exemple :

* **Windows 11** est le système d’exploitation de la machine hôte ;
* **VMware Workstation** est l’hyperviseur ;
* Windows ou Ubuntu peuvent être les systèmes invités.

Les hyperviseurs de type 2 sont particulièrement pratiques pour les laboratoires, les tests et la formation.

Quelques exemples : VMware Workstation, Oracle VirtualBox, VMware Fusion ..

### 1.3. Les ressources d’une machine virtuelle

Lorsqu’on crée une VM, il faut lui attribuer une partie des ressources de la machine physique. Prenons un ordinateur qui possède :

```
Processeur : 8 cœurs 
Mémoire : 16 Go de RAM 
Stockage : SSD de 500 Go
```

On pourrait créer une machine virtuelle avec :

```
2 vCPU 
4 Go de RAM 
60 Go de stockage
```

Ces ressources ne viennent pas de nulle part : elles sont prises sur les ressources disponibles de l’ordinateur physique.

Il faut donc faire attention à ne pas attribuer trop de ressources aux machines virtuelles.

Par exemple, si un ordinateur possède 16 Go de RAM, donner 14 Go à une seule VM risque de ralentir fortement la machine hôte.

Il faut toujours conserver suffisamment de ressources pour :

* Windows ou Linux sur la machine hôte ;
* l’hyperviseur ;
* les autres applications ouvertes.

#### Le processeur virtuel

Une machine virtuelle utilise des **processeurs virtuels**, appelés **vCPU**.

L’hyperviseur fait le lien entre ces vCPU et le processeur physique de l’ordinateur.

Par exemple, une machine physique possédant plusieurs cœurs peut en mettre une partie à disposition d’une VM.

Il n’est pas toujours utile de donner beaucoup de vCPU à une machine virtuelle. Pour une VM de laboratoire, 2 ou 4 vCPU sont souvent suffisants selon le système utilisé.

#### La mémoire RAM

La mémoire RAM attribuée à une machine virtuelle est utilisée pendant que celle-ci fonctionne.

Si une VM possède 4 Go de RAM, cette mémoire doit être disponible sur la machine physique pendant son utilisation.

Plus on démarre de machines virtuelles en même temps, plus la consommation de RAM augmente.

C’est souvent la RAM qui limite le nombre de VM qu’on peut exécuter simultanément.

#### Le disque virtuel

Une machine virtuelle possède également un disque.

Cependant, ce disque n’est généralement pas un véritable disque physique séparé.

L’hyperviseur crée plutôt un **fichier sur le disque de l’ordinateur hôte** et présente ce fichier à la machine virtuelle comme s’il s’agissait d’un vrai disque.

```
SSD de l’ordinateur
        │
        └── Fichier du disque virtuel
                │
                └── Vu comme un disque par la VM
```

Le système d’exploitation invité peut ensuite utiliser ce disque normalement :

* Créer des partitions&#x20;
* Le formater&#x20;
* Installer le système d’exploitation&#x20;
* Enregistrer des fichiers.

Pour la VM, il ressemble donc à un disque physique normal.

#### La carte réseau virtuelle

Une machine virtuelle possède aussi une ou plusieurs **cartes réseau virtuelles**.

Le système invité les utilise de la même façon qu’une carte réseau physique.

```
Machine virtuelle
        │
Carte réseau virtuelle
        │
Hyperviseur
        │
Carte réseau de l’ordinateur
```

Selon la configuration choisie dans l’hyperviseur, une machine virtuelle peut :

* Avoir accès à Internet&#x20;
* Communiquer avec la machine hôte&#x20;
* Communiquer avec d’autres machines virtuelles&#x20;
* Être placée dans un réseau complètement isolé.

Cette possibilité est particulièrement utile lorsqu’on veut créer un petit réseau de laboratoire composé de plusieurs VM.

### 1.4. Démarrage d’une machine virtuelle

Lorsqu’on démarre une VM, elle démarre presque comme un ordinateur physique. On retrouve notamment :

```
BIOS / UEFI
    │
    ▼
Processeur
    │
    ▼
Mémoire RAM
    │
    ▼
Disque
    │
    ▼
Démarrage du système d’exploitation
```

La différence est que la plupart de ces composants sont virtuels et sont fournis par l’hyperviseur.

Pour le système invité, ils apparaissent comme du matériel normal.

### 1.5. Les snapshots

Un **snapshot** permet de conserver l’état d’une machine virtuelle à un moment précis.

C’est particulièrement pratique avant de faire une manipulation importante.

Par exemple :

```
VM fonctionnelle
      │
      ▼
Création d’un snapshot
      │
      ▼
Modification de la configuration
      │
      ▼
Problème
      │
      ▼
Retour au snapshot
```

Si la configuration ne fonctionne plus, on peut revenir à l’état enregistré précédemment.

{% hint style="info" %}
Dans un laboratoire, il est donc conseillé de prendre un snapshot avant une modification importante ou avant une manipulation qui pourrait rendre la VM inutilisable.
{% endhint %}

### 1.6. Pourquoi utiliser un hyperviseur de type 2 dans nos laboratoires ?

L’intérêt principal est de pouvoir créer plusieurs ordinateurs virtuels sur un seul poste. Par exemple :

```
PC physique du local
    │
    └── VMware Workstation Pro
            │
            ├── VM Windows 11
            ├── VM Ubuntu
            └── VM Windows Server
```

Ces machines peuvent ensuite être configurées pour communiquer entre elles.

On peut ainsi reproduire une petite infrastructure informatique sans avoir besoin de trois ordinateurs physiques.

L’hyperviseur de type 2 permet aussi de :

* Tester des configurations ;
* Faire des erreurs sans endommager le système principal ;
* Utiliser différents systèmes d’exploitation ;
* Revenir rapidement à un état précédent ;
* Créer ou supprimer facilement des machines de laboratoire.

## 2. Création et clonage d'une machine virtuelle Windows 11

Ce guide présente la création d'une machine virtuelle Windows 11 dans VMware Workstation Pro, son installation, sa préparation avec Sysprep, sa conservation comme modèle et la création d'un clone. Suivez les captures dans l'ordre et appliquez les paramètres indiqués.

### 2.1. Création et configuration de la machine virtuelle

Cette première partie crée le matériel virtuel, choisit son emplacement et associe l'image ISO de Windows 11.

Ouvrez le menu Démarrer, recherchez VMware Workstation Pro, puis cliquez sur l'application pour la lancer.

<figure><img src=".gitbook/assets/image (49).png" alt="" width="375"><figcaption></figcaption></figure>

Dans l'écran d'accueil de Workstation Pro, cliquez sur Create a New Virtual Machine pour ouvrir l'assistant de création.

<figure><img src=".gitbook/assets/image (50).png" alt="" width="375"><figcaption></figcaption></figure>

Sélectionnez Custom (advanced), puis cliquez sur Next. Ce mode permet de régler précisément le matériel virtuel et les options de compatibilité.

<figure><img src=".gitbook/assets/image (51).png" alt="" width="372"><figcaption></figcaption></figure>

Conservez Workstation 17.5 or later afin d'utiliser le niveau de matériel virtuel proposé par la version installée, puis cliquez sur Next.

<figure><img src=".gitbook/assets/image (52).png" alt="" width="372"><figcaption></figcaption></figure>

Sélectionnez I will install the operating system later. Cette option évite l'installation automatisée et permet de choisir manuellement l'édition de Windows, le disque et les paramètres initiaux.

<figure><img src=".gitbook/assets/image (53).png" alt="" width="372"><figcaption></figcaption></figure>

Choisissez Microsoft Windows comme système invité, sélectionnez Windows 11 x64 dans la liste Version, puis cliquez sur Next.

<figure><img src=".gitbook/assets/image (54).png" alt="" width="374"><figcaption></figcaption></figure>

Saisissez un nom significatif, par exemple T\_Windows11x64. Cliquez ensuite sur Browse pour remplacer l'emplacement proposé par défaut.

<figure><img src=".gitbook/assets/image (55).png" alt="" width="351"><figcaption></figcaption></figure>

Dans la fenêtre de sélection, choisissez le disque D:. L'utilisation du deuxième disque évite de remplir le disque système avec les fichiers volumineux de la VM.

Si vous avez un disque dur externe, choisissez ce dernier comme emplacement de stockage de votre machine.&#x20;

<figure><img src=".gitbook/assets/image (56).png" alt="" width="371"><figcaption></figcaption></figure>

Vérifiez que le nom de la VM et le chemin, par exemple D:\VM\T\_Windows11x64, sont corrects, puis cliquez sur Next.

<figure><img src=".gitbook/assets/image (57).png" alt="" width="377"><figcaption></figcaption></figure>

Saisissez et confirmez un mot de passe de chiffrement. VMware utilise ce chiffrement pour protéger les fichiers nécessaires au module TPM virtuel. Conservez ce mot de passe dans un endroit

<figure><img src=".gitbook/assets/image (58).png" alt="" width="372"><figcaption></figcaption></figure>

Conservez UEFI comme type de micrologiciel. Il convient à Windows 11 et permet l'utilisation du TPM virtuel; le démarrage sécurisé pourra être activé si le laboratoire l'exige.

<figure><img src=".gitbook/assets/image (59).png" alt="" width="374"><figcaption></figcaption></figure>

Attribuer les processeurs virtuels. Configurez deux processeurs avec deux coeurs par processeur, soit quatre processeurs virtuels au total, puis cliquez sur Next.

<figure><img src=".gitbook/assets/image (60).png" alt="" width="372"><figcaption></figcaption></figure>

Attribuer la mémoire vive.  Exemple : attribuer 6 Go de RAM.

<figure><img src=".gitbook/assets/image (61).png" alt="" width="374"><figcaption></figcaption></figure>

Choisir le mode réseau NAT. Sélectionnez Use network address translation (NAT). La VM accédera au réseau en partageant la connexion de l'ordinateur hôte, sans apparaître comme un appareil directement connecté au réseau physique

<figure><img src=".gitbook/assets/image (62).png" alt="" width="372"><figcaption></figcaption></figure>

Choisir le contrôleur SCSI. Conservez LSI Logic SAS (Recommended). Ce contrôleur de périphériques E/S offre une bonne compatibilité avec Windows 11 et ne nécessite pas de pilote supplémentaire pendant l'installation

<figure><img src=".gitbook/assets/image (63).png" alt="" width="372"><figcaption></figcaption></figure>

Choisir le type de disque de stockage pour la machine virtuelle. Sélectionnez NVMe (Recommended). Ce type de contrôleur de stockage moderne convient bien à Windows 11 et offre de bonnes performances.

<figure><img src=".gitbook/assets/image (64).png" alt="" width="372"><figcaption></figcaption></figure>

Créer un nouveau disque virtuel. Sélectionnez Create a new virtual disk. VMware créera un fichier de disque destiné uniquement à cette nouvelle machine virtuelle.

<figure><img src=".gitbook/assets/image (65).png" alt="" width="372"><figcaption></figcaption></figure>

Définir la capacité du disque. Fixez la taille maximale à 80 Go, laissez Allocate all disk space now décoché et sélectionnez Store virtual disk as a single file. Le fichier grandira progressivement jusqu'à la limite de 80 Go.

<figure><img src=".gitbook/assets/image (66).png" alt="" width="374"><figcaption></figcaption></figure>

Sauvegarder le fichier du disque virtuel. Conservez le nom proposé ou attribuez un nom clair au fichier VMDK. Ce fichier contiendra Windows, les logiciels et les données enregistrées dans la VM.

{% hint style="info" %}
Ce fichier est important pour le fonctionnement de votre machine. Gardez-le dans le même emplacement que celui choisi pour enregistrer votre machine virtuelle afin de ne pas le perdre.
{% endhint %}

<figure><img src=".gitbook/assets/image (67).png" alt="" width="371"><figcaption></figcaption></figure>

Ouvrir la personnalisation du matériel. Dans le résumé, cliquez sur Customize Hardware avant de terminer. Il reste à associer l'image ISO de Windows 11 au lecteur CD/DVD virtuel.

Préparer le lecteur CD DVD virtuel. Sélectionnez CD/DVD (SATA), cochez Connect at power on, choisissez Use ISO image file, puis cliquez sur Browse

<figure><img src=".gitbook/assets/image (68).png" alt="" width="487"><figcaption></figcaption></figure>

Sélectionner l'image ISO de Windows 11. Repérez le fichier ISO de Windows 11 fourni pour le laboratoire, sélectionnez-le, puis cliquez sur Ouvrir.

<figure><img src=".gitbook/assets/image (69).png" alt="" width="486"><figcaption></figcaption></figure>

Créer la machine virtuelle. Relisez le résumé final, vérifiez notamment les 4 processeurs virtuels, les 6 Go de RAM, le réseau NAT et le disque de 80 Go, puis cliquez sur Finish.

<figure><img src=".gitbook/assets/image (71).png" alt="" width="372"><figcaption></figcaption></figure>

### 2.2. Installation de Windows 11

Démarrer la machine virtuelle. La VM apparaît maintenant dans la bibliothèque de Workstation Pro. Cliquez sur Power on this virtual machine pour démarrer sur l'image ISO et lancer l'installation.

<figure><img src=".gitbook/assets/image (72).png" alt="" width="563"><figcaption></figcaption></figure>



Démarrer sur le lecteur CD/DVD virtuel. Pour lancer l’installation de Windows à partir de l’image ISO, utilisez les flèches du clavier pour sélectionner : **EFI VMware Virtual SATA CDROM Drive.**

Appuyez ensuite sur **Entrée**. La machine virtuelle démarrera alors sur l’image ISO de Windows montée dans le lecteur CD/DVD virtuel, ce qui lancera le programme d’installation de Windows.

<figure><img src=".gitbook/assets/image (131).png" alt="" width="521"><figcaption></figcaption></figure>

Choisir la langue d'installation. Sélectionnez Français (Canada) pour la langue, ainsi que le format régional correspondant, puis cliquez sur Suivant

<figure><img src=".gitbook/assets/image (73).png" alt="" width="530"><figcaption></figcaption></figure>

Choisir le clavier d'installation. Sélectionnez Français (Canada) comme clavier ou méthode d'entrée, puis cliquez sur Suivant.

<figure><img src=".gitbook/assets/image (74).png" alt="" width="563"><figcaption></figcaption></figure>

Lancer une nouvelle installation. Choisissez Installer Windows 11 et confirmez que les données, applications et paramètres existants peuvent être supprimés. La VM utilise un disque virtuel neuf, donc aucune donnée réelle de l'hôte ne sera effacée.

<figure><img src=".gitbook/assets/image (75).png" alt="" width="533"><figcaption></figcaption></figure>

Continuer sans clé de produit. Cliquez sur Je n'ai pas de clé de produit. L'activation pourra être effectuée plus tard selon la licence utilisée dans l'établissement

<figure><img src=".gitbook/assets/image (76).png" alt="" width="510"><figcaption></figcaption></figure>

Sélectionner l'édition de Windows. Choisissez Windows 11 Professionnel Education, ou l'édition demandée par l'enseignant, puis cliquez sur Suivant.

<figure><img src=".gitbook/assets/image (77).png" alt="" width="563"><figcaption></figcaption></figure>

Choisir le disque d'installation. Sélectionnez l'espace non alloué de 80 Go, puis cliquez sur Suivant. Le programme d'installation créera automatiquement les partitions nécessaires.

<figure><img src=".gitbook/assets/image (78).png" alt="" width="563"><figcaption></figcaption></figure>

Confirmer l'installation. Vérifiez l'édition choisie et l'option Ne rien conserver, puis cliquez sur Installer. Windows copiera ses fichiers et redémarrera automatiquement la VM.

<figure><img src=".gitbook/assets/image (79).png" alt="" width="563"><figcaption></figcaption></figure>

### 2.3. Configuration initiale de Windows 11

#### La configuration OOBE&#x20;

L'OOBE, ou Out-of-Box Experience, est l'assistant affiché au premier démarrage. Il permet de choisir la région, le clavier, le compte utilisateur et les paramètres de confidentialité.

Choisir le pays ou la région. Au premier démarrage de Windows, sélectionnez Canada, puis cliquez sur Oui pour commencer la configuration initiale OOBE.

<figure><img src=".gitbook/assets/image (80).png" alt="" width="528"><figcaption></figcaption></figure>

Confirmer la disposition du clavier. Choisissez Français (Canada), puis cliquez sur Oui. Cette disposition pourra être modifiée ultérieurement dans les paramètres de Windows.

<figure><img src=".gitbook/assets/image (81).png" alt="" width="528"><figcaption></figcaption></figure>

Ignorer une deuxième disposition. Cliquez sur Ignorer si une seule disposition de clavier suffit.&#x20;

<figure><img src=".gitbook/assets/image (82).png" alt="" width="563"><figcaption></figcaption></figure>

Vérifier la connexion réseau. Lorsque Windows indique que le réseau est connecté, cliquez sur Suivant. Le mode NAT configuré dans VMware fournit cette connexion par l'intermédiaire de l'hôte.

<figure><img src=".gitbook/assets/image (83).png" alt="" width="563"><figcaption></figcaption></figure>

Ignorer le nom de l'appareil pour le moment. Laissez le champ vide et cliquez sur Ignorer, puisque cette VM deviendra le modèle. Un nom unique sera attribué à chaque clone lors de son premier démarrage.

<figure><img src=".gitbook/assets/image (84).png" alt="" width="563"><figcaption></figcaption></figure>

Choisir une configuration pour le travail ou l'école. Sélectionnez Configurer pour le travail ou l'école, puis cliquez sur Suivant afin d'accéder aux options adaptées à l'édition Education.

<figure><img src=".gitbook/assets/image (85).png" alt="" width="540"><figcaption></figcaption></figure>

Afficher les options de connexion. Sur l'écran de connexion Microsoft, cliquez sur Options de connexion. Cette commande donne accès à la création d'un compte local.

<figure><img src=".gitbook/assets/image (86).png" alt="" width="560"><figcaption></figcaption></figure>

Choisir la création d'un compte local. Cliquez sur Joindre le domaine à la place. Dans cet assistant, ce lien permet de créer un compte local; il ne joint pas immédiatement la VM à un domaine.

<figure><img src=".gitbook/assets/image (87).png" alt="" width="563"><figcaption></figcaption></figure>

Créer le compte utilisateur temporaire. Saisissez un nom d'utilisateur local, par exemple info, puis cliquez sur Suivant. Ce compte servira seulement à terminer la première configuration du modèle.

<figure><img src=".gitbook/assets/image (88).png" alt="" width="510"><figcaption></figcaption></figure>

Définir le mot de passe local. Saisissez un mot de passe pour le compte local, conservez-le de manière sécuritaire, puis cliquez sur Suivant.

<figure><img src=".gitbook/assets/image (89).png" alt="" width="517"><figcaption></figcaption></figure>

Configurer les questions de sécurité. Choisissez trois questions de sécurité et fournissez une réponse pour chacune. Elles permettront de réinitialiser le mot de passe du compte local en cas d'oubli.

<figure><img src=".gitbook/assets/image (90).png" alt="" width="563"><figcaption></figcaption></figure>

Attendre la fin de la configuration. Laissez Windows appliquer les paramètres et télécharger les éléments nécessaires. N'éteignez pas la VM pendant cette étape; plusieurs redémarrages peuvent avoir lieu.

<figure><img src=".gitbook/assets/image (95).png" alt="" width="563"><figcaption></figcaption></figure>

Ouvrir la première session. À l'écran de connexion, saisissez le mot de passe du compte local créé précédemment, puis validez pour ouvrir la session.

<figure><img src=".gitbook/assets/image (96).png" alt="" width="344"><figcaption></figcaption></figure>

Vérifier l'accès au bureau Windows. Lorsque le bureau apparaît, confirmez que la session fonctionne correctement. La VM peut maintenant être préparée comme machine de référence.

<figure><img src=".gitbook/assets/image (97).png" alt="" width="563"><figcaption></figcaption></figure>

### 2.4. Préparation de la machine virtuelle modèle (Template)

Une machine virtuelle modèle, aussi appelée template, est une VM de référence préparée une seule fois avec le système, les pilotes, les mises à jour et les logiciels communs. Elle n'est pas utilisée comme poste de travail quotidien : elle est conservée dans un état propre et arrêté afin de créer rapidement des VM cohérentes.

#### Rôle de Sysprep

Sysprep est l'outil intégré à Windows qui prépare une installation à être dupliquée. Le mode Audit permet de terminer les réglages avec le compte Administrateur intégré.&#x20;

Lors de l'étape finale, l'option Généraliser retire les informations propres à l'installation, notamment le SID de l'ordinateur, et l'option OOBE oblige chaque clone à reprendre la configuration initiale afin de recevoir son propre nom et son propre compte.

{% hint style="info" %}
Évitez d'installer ou de mettre à jour manuellement des applications depuis Microsoft Store avant la généralisation, car des applications associées à un seul profil peuvent faire échouer Sysprep.
{% endhint %}

Ouvrir la commande Exécuter. Cliquez avec le bouton droit sur Démarrer, ou utilisez Windows + X, puis choisissez Exécuter.

<figure><img src=".gitbook/assets/image (98).png" alt="" width="321"><figcaption></figcaption></figure>

Ouvrir le dossier Sysprep. Dans la fenêtre Exécuter, saisissez sysprep, puis cliquez sur OK. Windows ouvrira le dossier qui contient l'outil de préparation du système.

<figure><img src=".gitbook/assets/image (99).png" alt="" width="438"><figcaption></figcaption></figure>

Lancer l'outil Sysprep. Dans le dossier C:\Windows\System32\Sysprep, double-cliquez sur l'application sysprep

<figure><img src=".gitbook/assets/image (100).png" alt="" width="537"><figcaption></figcaption></figure>

Redémarrer en mode Audit. Choisissez Entrer en mode Audit du système, laissez Généraliser décoché, sélectionnez Redémarrer, puis cliquez sur OK. Windows redémarrera avec le compte Administrateur intégré afin de poursuivre la préparation du modèle.

<figure><img src=".gitbook/assets/image (101).png" alt="" width="329"><figcaption></figcaption></figure>

Ouvrir la gestion des autres utilisateurs. Après le redémarrage en mode Audit, recherchez compte dans le menu Démarrer, puis ouvrez Autres utilisateurs pour gérer le compte temporaire créé pendant l'OOBE.

<figure><img src=".gitbook/assets/image (102).png" alt="" width="326"><figcaption></figcaption></figure>

Supprimer le compte temporaire. Sélectionnez le compte créé précédemment et confirmez Supprimer le compte et les données. Vérifiez d'abord qu'aucun fichier utile n'est conservé dans ce profil

<figure><img src=".gitbook/assets/image (103).png" alt="" width="559"><figcaption></figcaption></figure>

#### Installation de VMware Tools et mises à jour

Installez les pilotes d'intégration VMware et les mises à jour de Windows avant de figer le modèle. Ainsi, chaque clone partira d'une base déjà fonctionnelle et à jour.

Monter le programme d'installation de VMware Tools. Dans la barre de menus de Workstation Pro, ouvrez VM, puis choisissez Install VMware Tools. Un disque virtuel d'installation sera inséré dans Windows

<figure><img src=".gitbook/assets/image (104).png" alt="" width="260"><figcaption></figcaption></figure>

Ouvrir le disque VMware Tools. Cliquez sur la notification d'exécution automatique du lecteur DVD VMware Tools afin d'afficher les actions disponibles

<figure><img src=".gitbook/assets/image (105).png" alt="" width="335"><figcaption></figcaption></figure>

Exécuter le programme d'installation. Dans la fenêtre d'exécution automatique, cliquez sur Exécuter setup64.exe pour démarrer l'installation des outils VMware en version 64 bits.

<figure><img src=".gitbook/assets/image (106).png" alt="" width="335"><figcaption></figcaption></figure>

Démarrer l'assistant VMware Tools. Dans l'écran de bienvenue de l'assistant, cliquez sur Suivant.

<figure><img src=".gitbook/assets/image (107).png" alt="" width="374"><figcaption></figcaption></figure>

Choisir l'installation typique. Sélectionnez Typique, puis cliquez sur Suivant. Cette option installe automatiquement les pilotes et fonctions d'intégration nécessaires

<figure><img src=".gitbook/assets/image (108).png" alt="" width="377"><figcaption></figcaption></figure>

Installer VMware Tools. Cliquez sur Installer. VMware Tools améliorera notamment l'affichage, la gestion de la souris et l'intégration entre le système hôte et la VM.

<figure><img src=".gitbook/assets/image (109).png" alt="" width="357"><figcaption></figcaption></figure>

Redémarrer après l'installation. Cliquez sur Oui pour redémarrer Windows et charger correctement les pilotes et services installés par VMware Tools.

<figure><img src=".gitbook/assets/image (110).png" alt="" width="311"><figcaption></figcaption></figure>

Ouvrir Windows Update. Après le redémarrage, recherchez Vérifier les mises à jour dans le menu Démarrer, puis ouvrez la page Windows Update.

<figure><img src=".gitbook/assets/image (111).png" alt="" width="563"><figcaption></figcaption></figure>

Installer les mises à jour Windows. Cliquez sur Tout télécharger et installer. Répétez la vérification et redémarrez au besoin jusqu'à ce qu'aucune mise à jour importante ne soit proposée.

<figure><img src=".gitbook/assets/image (112).png" alt="" width="410"><figcaption></figcaption></figure>

#### Généralisation et protection du modèle

Cette phase généralise Windows, arrête la VM, active le mode modèle de Workstation Pro et crée un snapshot de référence.

#### Le mode modèle dans Workstation Pro

Dans VMware Workstation Pro, le mode modèle (Template)  ne crée pas une nouvelle VM. Il désigne la VM comme source de clonage et protège surtout la machine parente et ses snapshots contre une suppression accidentelle, ce qui est particulièrement important lorsqu'un clone lié en dépend.

Généraliser Windows et arrêter la VM. Relancez Sysprep, choisissez Entrer en mode OOBE, cochez Généraliser et sélectionnez Arrêter le système. Sysprep retirera les informations propres à cette installation, puis éteindra la VM. Ne redémarrez plus le modèle avant de créer le snapshot et le clone.

<figure><img src=".gitbook/assets/image (113).png" alt="" width="326"><figcaption></figcaption></figure>

Ouvrir les paramètres de la VM. Lorsque la VM est complètement arrêtée, ouvrez le menu VM et cliquez sur Settings pour accéder à ses options avancées

<figure><img src=".gitbook/assets/image (114).png" alt="" width="254"><figcaption></figcaption></figure>

Activer le mode modèle. Dans l'onglet Options, ouvrez Advanced, cochez Enable Template mode (to be used for cloning), puis cliquez sur OK. Ce mode protège la VM parente et ses snapshots contre une suppression accidentelle.

<figure><img src=".gitbook/assets/image (115).png" alt="" width="563"><figcaption></figcaption></figure>

Commencer la création d'un snapshot. Ouvrez VM, puis Snapshot et Take Snapshot. Le snapshot conservera le point de référence arrêté immédiatement après la généralisation.

<figure><img src=".gitbook/assets/image (116).png" alt="" width="415"><figcaption></figcaption></figure>

Nommer le snapshot de référence. Attribuez un nom clair au snapshot et précisez dans la description que la VM a été arrêtée après Sysprep, puis cliquez sur Take Snapshot. Un snapshot facilite le retour à cet état, mais ne remplace pas une sauvegarde.

<figure><img src=".gitbook/assets/image (117).png" alt=""><figcaption></figcaption></figure>

### 2.5. Création et premier démarrage du clone

#### Le clonage

Un clone est une nouvelle machine virtuelle créée à partir d'un état précis de la VM modèle. Un clone complet possède sa propre copie du disque et fonctionne indépendamment du modèle. Un clone lié occupe moins d'espace, mais partage le disque de base et dépend donc de la VM parente et de son snapshot.&#x20;

Ouvrir l'assistant de clonage. Sélectionnez la VM modèle, ouvrez VM, puis Manage et Clone pour lancer l'assistant de clonage.

<figure><img src=".gitbook/assets/image (118).png" alt="" width="461"><figcaption></figcaption></figure>

Choisir le snapshot comme source. Sélectionnez An existing snapshot, choisissez le snapshot créé après Sysprep, puis cliquez sur Suivant. Le clone sera construit à partir de cet état stable.

<figure><img src=".gitbook/assets/image (119).png" alt="" width="349"><figcaption></figcaption></figure>

Créer un clone complet. Sélectionnez Create a full clone, puis cliquez sur Suivant.&#x20;

<figure><img src=".gitbook/assets/image (120).png" alt="" width="349"><figcaption></figcaption></figure>

Nommer le nouveau clone. Saisissez un nom unique, par exemple Clone1\_Windows11x64, puis cliquez sur Browse pour choisir son emplacment de stockage.

<figure><img src=".gitbook/assets/image (121).png" alt="" width="349"><figcaption></figcaption></figure>

Choisir le dossier parent du clone. Dans la fenêtre de sélection, ouvrez le dossier prévu sur le disque D:, puis cliquez sur Créer un nouveau dossier.

<figure><img src=".gitbook/assets/image (122).png" alt="" width="260"><figcaption></figcaption></figure>

Créer le dossier du clone. Donnez au nouveau dossier le même nom clair que le clone, sélectionnez-le, puis cliquez sur OK.

<figure><img src=".gitbook/assets/image (123).png" alt="" width="260"><figcaption></figcaption></figure>

Valider le nom et l'emplacement du clone. Vérifiez le nom et le chemin du nouveau clone, puis cliquez sur Terminer. La copie peut prendre plusieurs minutes selon la taille du disque virtuel.

<figure><img src=".gitbook/assets/image (124).png" alt="" width="352"><figcaption></figcaption></figure>

Démarrer le clone. Lorsque le clone apparaît dans la bibliothèque de Workstation Pro, sélectionnez-le et cliquez sur Power on this virtual machine.

<figure><img src=".gitbook/assets/image (125).png" alt="" width="241"><figcaption></figcaption></figure>

Choisir la région du clone. Le clone démarre dans l'OOBE comme une nouvelle installation. Sélectionnez Canada, puis cliquez sur Oui.

<figure><img src=".gitbook/assets/image (126).png" alt="" width="413"><figcaption></figcaption></figure>

Choisir le clavier du clone. Sélectionnez Français (Canada), puis cliquez sur Oui.

<figure><img src=".gitbook/assets/image (127).png" alt="" width="418"><figcaption></figcaption></figure>

Attribuer un nom unique au clone. Saisissez un nom d'appareil propre à cette VM, par exemple Client1, puis cliquez sur Suivant. Chaque clone doit recevoir un nom distinct.

<figure><img src=".gitbook/assets/image (128).png" alt="" width="438"><figcaption></figcaption></figure>

Choisir la configuration professionnelle du clone. Sélectionnez Configurer pour le travail ou l'école, puis cliquez sur Suivant. Continuez ensuite l'OOBE et créez le compte demandé pour ce clone.

<figure><img src=".gitbook/assets/image (129).png" alt="" width="432"><figcaption></figcaption></figure>

Refaites ensuite les mêmes étapes de création d’un utilisateur et créez votre propre compte utilisateur local.

Vérifier le clone terminé. Une fois l'OOBE terminé, vérifiez que le bureau s'affiche, que le nouveau nom est appliqué et que Windows fonctionne correctement. Le clone est maintenant prêt à être utilisé sans modifier la VM modèle.

<figure><img src=".gitbook/assets/image (130).png" alt="" width="563"><figcaption></figcaption></figure>
