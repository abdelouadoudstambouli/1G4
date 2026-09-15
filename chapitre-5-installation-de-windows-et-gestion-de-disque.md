---
description: Introduction au systèmes d'exploitation Windows, Gestion de disque
hidden: true
---

# Chapitre 5 - Installation de Windows et gestion de disque

## Objectifs d'apprentissage&#x20;

* Expliquer le rôle d’un système d’exploitation et la façon dont il gère le matériel, les logiciels et les ressources de l’ordinateur.
* Faire la différence entre les architectures x64 et ARM64 et comprendre leur impact sur la compatibilité du matériel et des logiciels.
* Réaliser les principales étapes d’une installation de Windows 11.
* Effectuer les mises à jour de Windows et vérifier le bon fonctionnement des périphériques et de leurs pilotes.
* Faire la différence entre un disque, une partition, un volume et un système de fichiers.
* Comparer les méthodes de partitionnement MBR et GPT et choisir celle qui convient selon la situation.
* Reconnaître les principaux systèmes de fichiers comme et connaître leurs principaux usages.
* Expliquer le fonctionnement des principaux niveaux RAID : RAID 0, 1, 5, 6 et 10.

## 1. Le rôle d'un système d'exploitation&#x20;

Un système d’exploitation est l’ensemble des logiciels qui gèrent les ressources de l’ordinateur et permettent aux applications de fonctionner. Windows, les distributions Linux et macOS sont des exemples de systèmes d’exploitation pour ordinateurs. Android et iOS remplissent un rôle comparable sur les appareils mobiles.

Quand vous ouvrez un document, l’application demande au système de lire le fichier sur le disque, de réserver de la mémoire et d’afficher son contenu. L’application n’a pas à connaître directement le fonctionnement électrique du SSD ou de l’écran. Elle utilise des services fournis par le système.

Il faut distinguer trois éléments. Le matériel comprend les composants physiques. Le système d’exploitation gère leur utilisation. Les applications réalisent les tâches de l’utilisateur, comme rédiger un texte ou modifier une photo.&#x20;

Le bureau et le menu Démarrer ne représentent que la partie visible du système. Même lorsque personne n’a ouvert de session, Windows peut gérer le réseau, exécuter des services et appliquer certaines opérations de maintenance.

### 1.1. Partager le temps du processeur

Un programme installé sur le disque n’est pas forcément en cours d’exécution. Lorsqu’il démarre, Windows crée un processus, c’est-à-dire un programme en cours d’exécution avec les ressources dont il a besoin. Une même application peut créer plusieurs processus. Un navigateur le fait notamment pour séparer différentes activités.

À l’intérieur d’un processus, un ou plusieurs threads portent les suites d’instructions à exécuter. Le système répartit le temps de processeur entre les threads qui sont prêts à travailler. Cette répartition est appelée ordonnancement.

Sur un processeur possédant plusieurs cœurs, certaines tâches peuvent réellement s’exécuter en parallèle. Sur un même cœur, le système peut passer rapidement d’une tâche à une autre. C’est ce qui permet d’écouter de la musique pendant qu’un téléchargement et une analyse antivirus se poursuivent.

### 1.2. Gérer la mémoire

La mémoire vive, ou RAM, contient les données et les instructions utilisées pendant le travail courant. Windows réserve des espaces de mémoire aux processus et les isole les uns des autres. Une application ne devrait pas pouvoir modifier librement la mémoire d’une autre. Cette séparation contribue à la stabilité et à la sécurité du système.

La mémoire virtuelle donne aux processus leur propre espace d’adressage. Windows peut aussi déplacer certaines pages de mémoire vers un fichier d’échange sur le disque. Le fichier d’échange soutient donc la gestion de la mémoire, mais un SSD reste beaucoup plus lent que la RAM pour ce type d’accès.

{% hint style="info" %}
Exemple: Un poste possède 8 Go de RAM. Plusieurs applications et une VM sont ouvertes. Le système doit multiplier les échanges avec le disque et le poste devient lent. Ajouter de l’espace libre sur le SSD peut éviter un blocage par manque d’espace, mais cela ne remplace pas l’ajout de RAM ou la fermeture d’applications.
{% endhint %}

### 1.3. Organiser les fichiers et les accès au matériel

Windows crée les fichiers et les dossiers, conserve leurs noms et leurs propriétés, retrouve leur contenu et vérifie les permissions d’accès. Ces opérations s’appuient sur un système de fichiers, comme NTFS.

Pour communiquer avec les périphériques, Windows utilise des pilotes. Un pilote est un logiciel qui permet au système de commander un périphérique ou une catégorie de périphériques. Une carte réseau peut être correctement branchée tout en restant inutilisable si son pilote manque.

{% hint style="info" %}
Exemple : Prenons l’impression d’un document. L’application transmet une demande à Windows. Le système organise le travail d’impression, utilise le pilote approprié et communique avec l’imprimante. L’utilisateur n’a pas à gérer lui-même chaque échange de données.
{% endhint %}

### 1.4. Le noyau et les services

Le noyau est la partie centrale du système. Il intervient notamment dans la gestion du processeur, de la mémoire et des échanges avec le matériel. Les applications ordinaires fonctionnent généralement en mode utilisateur, avec des possibilités limitées. Le noyau et certains pilotes disposent d’un niveau d’accès plus élevé.

Cette différence explique pourquoi une application qui se ferme soudainement ne fait pas nécessairement fermer tout Windows, alors qu’un problème dans un pilote fonctionnant au niveau du noyau peut provoquer un arrêt du système.

Un service est un programme qui réalise des tâches en arrière-plan. Le service d’impression, par exemple, peut fonctionner sans fenêtre ouverte. Tous les services ne sont pas indispensables dans toutes les situations, mais les désactiver au hasard peut créer des problèmes difficiles à diagnostiquer.

## 2. Les architectures x64 et ARM64

L’architecture d’un processeur définit la manière dont il traite les données et exécute les instructions. Un logiciel doit donc être compatible avec l’architecture du processeur pour fonctionner correctement.

**x64** et **ARM64** sont deux architectures différentes de processeurs 64 bits. Elles ne représentent ni le nombre de cœurs du processeur ni la quantité de mémoire RAM installée.&#x20;

Par exemple, un processeur 64 bits peut avoir 4 cœurs et fonctionner dans un ordinateur équipé de 8 Go de RAM.

### 2.1. Les ordinateurs x64

L’architecture x64, aussi appelée x86-64 ou AMD64, est utilisée par de nombreux processeurs Intel et AMD. Le nom AMD64 peut apparaître dans un fichier d’installation même lorsque le processeur est fabriqué par Intel. Il désigne alors l’architecture, pas une obligation d’utiliser une marque particulière.

Dans les téléchargements, x86 désigne souvent une version 32 bits. Windows 11 x64 peut exécuter de nombreuses applications x86 grâce à sa couche de compatibilité. Cela ne signifie pas qu’il accepte tous les anciens logiciels, ni qu’un pilote 32 bits convient à un système 64 bits.

### 2.2. Les ordinateurs ARM64

ARM64 est utilisé notamment dans certains ordinateurs Windows équipés de processeurs Qualcomm Snapdragon. Windows 11 existe dans une version conçue pour cette architecture.

Une application ARM64 native exécute directement les instructions prévues pour ce type de processeur. Windows 11 sur ARM peut aussi exécuter de nombreuses applications x86 et x64 par émulation. Cette traduction peut avoir un effet sur les performances et ne garantit pas la compatibilité de tous les logiciels.&#x20;

### 2.3. Architecture et édition de Windows

L’architecture indique le type de processeur visé. L’édition indique l’ensemble de fonctions et les droits d’utilisation associés au produit. Famille, Professionnel et Éducation sont des éditions de Windows.&#x20;

Exemple. Deux postes peuvent utiliser Windows 11 x64, l’un en édition Famille et l’autre en édition Professionnel. Ils utilisent la même architecture, mais certaines fonctions d’administration diffèrent.

## 3. La préparation et l’installation de Windows

Avant l’installation, déterminez à quoi servira le poste. Un ordinateur destiné à la bureautique n’a pas nécessairement les mêmes besoins qu’un poste qui exécutera plusieurs VM. Vérifiez les applications, les périphériques, la capacité de stockage et les fonctions d’administration attendues.

Sur un ordinateur déjà utilisé, identifiez les données à conserver. Une installation propre, une suppression de partition ou un formatage peuvent rendre ces données inaccessibles. Une sauvegarde n’est utile que si elle contient les bons fichiers et qu’on peut les relire.

Notez aussi l’édition autorisée par la licence de l’établissement, la langue, la disposition du clavier et les informations nécessaires à la configuration réseau. Si le disque est chiffré, assurez-vous de disposer de la clé de récupération avant les interventions qui pourraient la rendre nécessaire.

### 3.1. Vérifier les prérequis de Windows 11

Les exigences minimales générales comprennent notamment un processeur 64 bits compatible d’au moins deux cœurs, 4 Go de RAM, un périphérique de stockage d’au moins 64 Go, un micrologiciel UEFI capable de prendre en charge Secure Boot et un TPM 2.0.&#x20;

Les exigences graphiques comprennent DirectX 12 avec un pilote WDDM 2.0, ainsi qu’un affichage adapté. Il faut aussi vérifier la compatibilité précise du processeur.

Vous pouvez voir la [configuration requise pour Windows 11](https://www.microsoft.com/en-us/windows/windows-11-specifications).

Pour la VM de cours, on peut prévoir 4 processeurs virtuels, 6 Go de RAM et un disque système de 80 Go, à ajuster selon les ressources de l’ordinateur hôte. Le poste hôte doit garder suffisamment de mémoire pour son propre système.&#x20;

Le TPM aide à protéger certains secrets cryptographiques. Secure Boot vérifie la confiance accordée aux composants de démarrage. Le chiffrement de disque protège les données au repos. Ces fonctions sont liées à la sécurité, mais elles ne sont pas interchangeables.

### 3.2. Comprendre le support d’installation

Une image ISO est un fichier qui contient la représentation d’un disque optique et ses fichiers. Elle peut inclure les éléments nécessaires au démarrage du programme d’installation.

Sur un ordinateur physique, on peut préparer une clé USB botable. Copier simplement le fichier ISO dans une clé ordinaire ne rend pas forcément cette clé bootable. L’outil de préparation doit installer  des fichiers que le micrologiciel peut utiliser.

Dans une VM, on associe l’ISO au lecteur CD/DVD virtuel. Pour Windows invité, cette image apparaît comme un disque inséré dans un lecteur. Le fichier ISO reste sur le stockage de l’ordinateur hôte.

### 3.3. Choisir le type d'installation&#x20;

| Opération                        | But                                                                                     | Conséquence à prévoir                                                                                        |
| -------------------------------- | --------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| Installation propre              | Installer un système neuf sur une destination choisie                                   | Les applications doivent être réinstallées et les données doivent être protégées avant l’opération           |
| Mise à niveau sur place          | Passer à une version admissible en conservant ce que le programme d’installation permet | Vérifier la compatibilité et les options de conservation proposées                                           |
| Réinitialisation                 | Réinstaller Windows avec les outils de récupération                                     | L’option de conservation des fichiers ne conserve pas nécessairement les applications ni tous les paramètres |
| Déploiement d’une image préparée | Réutiliser une configuration standard                                                   | L’image doit être adaptée et préparée pour le déploiement sur plusieurs postes                               |

### 3.4. Installer Windows dans une VM&#x20;

1. Préparer la machine. Vérifiez la mémoire, les processeurs virtuels, le disque système, le réseau et les paramètres UEFI. Donnez un nom clair à la VM et enregistrez ses fichiers dans le dossier prévu.
2. Associer l’ISO. Dans les paramètres du lecteur CD/DVD, sélectionnez l’image de Windows et activez sa connexion au démarrage.
3. Démarrer sur le lecteur virtuel. Utilisez le menu de démarrage de la VM si nécessaire. Choisissez le lecteur CD/DVD UEFI contenant l’ISO. Si le message demandant d’appuyer sur une touche apparaît, cliquez dans la fenêtre de la VM et appuyez sur une touche.
4. Vérifier les choix de base. Sélectionnez la langue et le clavier. Une mauvaise disposition du clavier peut modifier les caractères d’un mot de passe.
5. Choisir l’édition autorisée. Utilisez l’édition prévue par le cours et la méthode d’activation de l’établissement.
6. Sélectionner l’installation neuve. Selon la version de l’assistant, les écrans peuvent présenter une installation personnalisée ou une sélection directe de la destination.
7. Choisir le disque cible. Vérifiez sa capacité. Sur la VM neuve, sélectionnez l’espace non alloué du disque système. Laissez l’assistant créer les partitions nécessaires. Ne supprimez pas les partitions d’un autre disque.
8. Laisser l’installation se terminer. Windows prépare les fichiers et redémarre plusieurs fois. Après le premier redémarrage, laissez la machine démarrer sur son disque système. N’appuyez plus sur une touche pour relancer l’installation depuis l’ISO.
9. Terminer la configuration initiale. Vérifiez la région, le clavier, le réseau, le compte et les paramètres proposés.&#x20;
10. Effectuer les vérifications finales. Contrôlez les mises à jour, les pilotes, l’activation, le réseau, les comptes et la capacité disponible. Dans une VM, installez aussi les VMware Tools prévus pour la configuration utilisée

## 4. Les comptes et les droits des utilisateurs

Un compte permet à Windows d’identifier une personne ou une identité technique. Il associe une authentification à des droits. Des comptes distincts facilitent la séparation des fichiers, la personnalisation et le suivi des actions.

Le compte et le profil ne sont pas identiques. Le compte représente l’identité. Le profil contient l’environnement de cette identité sur le poste : bureau, paramètres et dossiers personnels. Les profils locaux se trouvent généralement sous C:\Users.

Windows utilise un identifiant interne appelé SID pour représenter une identité dans de nombreux mécanismes de sécurité. Recréer un compte avec le même nom ne lui redonne donc pas automatiquement les permissions de l’ancien compte.

### 4.1. Identifier le type de compte&#x20;

Un compte local est créé sur un ordinateur et géré par cet ordinateur. Un compte Microsoft correspond à une identité personnelle associée aux services Microsoft. Un compte professionnel ou scolaire est géré par une organisation. Dans une infrastructure administrée, l’identité peut relever notamment d’Active Directory ou de Microsoft Entra ID.

Ces distinctions décrivent où l’identité est gérée. Elles ne disent pas à elles seules si l’utilisateur est administrateur. Un compte local peut être administrateur ou standard. Un compte Microsoft peut également disposer de l’un ou de l’autre rôle sur un poste.

### 4.2. Distinguer utilisateur standard et administrateur

Un **utilisateur standard** peut utiliser l’ordinateur normalement, lancer des applications et modifier certains de ses paramètres. Par contre, il ne peut pas effectuer certaines modifications importantes du système ou gérer les autres comptes sans autorisation.

Un **administrateur** possède plus de droits. Il peut installer certains logiciels, modifier des paramètres système et gérer les comptes utilisateurs.

Lorsqu’une action demande des droits administrateur, Windows utilise le **contrôle de compte d’utilisateur (UAC)**. Une fenêtre peut alors demander une confirmation ou le mot de passe d’un administrateur.

Pour des raisons de sécurité, il est préférable d’utiliser un compte standard pour les tâches quotidiennes et d’utiliser les droits administrateur seulement lorsque c’est nécessaire.

## 5. Les mises à jour et les pilotes

Les mises à jour corrigent des défauts, comblent des vulnérabilités et font évoluer le système. Certaines modifient peu l’apparence de Windows. D’autres apportent des changements plus visibles et peuvent nécessiter davantage de préparation.

Une mise à jour téléchargée n’est pas nécessairement complètement appliquée. Certains fichiers utilisés par le système ne peuvent être remplacés qu’au redémarrage. L’indication « Redémarrage requis » fait donc partie du suivi normal.

On distingue notamment les mises à jour de qualité et de sécurité, les changements de version, les mises à jour de pilotes et les mises à jour de renseignements de sécurité de l’antivirus. Dans une organisation, leur distribution peut être encadrée par une politique interne.

### 5.1. Le rôle d'un pilote&#x20;

Un **pilote** est un logiciel qui permet à Windows de communiquer avec un périphérique, par exemple une carte Wi-Fi, une carte graphique ou une imprimante.

Chaque pilote doit être compatible avec :

* le matériel utilisé;
* la version de Windows;
* l’architecture du système, par exemple x64 ou ARM64.

Un pilote conçu pour un périphérique ne fonctionne donc pas forcément avec un autre.

Windows possède déjà plusieurs pilotes et peut en télécharger automatiquement avec **Windows Update**. Dans certains cas, il peut être nécessaire d’installer un pilote provenant du **site officiel du fabricant**.

Dans une machine virtuelle, Windows utilise principalement du **matériel virtuel fourni par VMware**. Les pilotes installés dans la VM correspondent donc à ce matériel virtuel et non directement au matériel physique de l’ordinateur.

### 5.2. Le Gestionnaire de périphériques

Le **Gestionnaire de périphériques** permet de voir les composants matériels reconnus par Windows et leurs pilotes.

Pour l’ouvrir :

* clic droit sur **Démarrer** → **Gestionnaire de périphériques**;
* ou exécuter `devmgmt.msc`.

Les périphériques sont classés par catégories : cartes réseau, cartes graphiques, disques, contrôleurs USB, etc.

Un **triangle jaune** indique qu’un problème a été détecté. Cela ne signifie pas nécessairement que le matériel est défectueux.

Dans les propriétés du périphérique, Windows affiche généralement un message et un **code d’erreur**. Par exemple :

* **Code 28** : le pilote n’est généralement pas installé;
* **Code 10** : le périphérique ne peut pas démarrer.

L’onglet **Pilote** permet de voir le fabricant, la version et la date du pilote.

L’onglet **Détails** permet notamment de consulter les **identifiants matériels**, qui peuvent aider à identifier un périphérique inconnu.

Dans le Gestionnaire de périphériques, plusieurs actions sont possibles :

* **Mettre à jour le pilote** : rechercher ou installer une autre version du pilote.
* **Restaurer le pilote** : revenir à la version précédente.
* **Désactiver l’appareil** : empêcher temporairement son utilisation.
* **Désinstaller l’appareil** : retirer sa configuration actuelle. Windows pourra généralement le détecter de nouveau.

Il faut éviter de modifier plusieurs éléments en même temps. Un technicien devrait d’abord identifier le problème, effectuer **une correction à la fois**, puis vérifier si le problème est réglé.

## 6. Les modes de démarrage&#x20;

### 6.1. Démarrer normalement ou chercher un problème

Le démarrage normal charge les composants habituels du système et les éléments activés dans sa configuration. Lorsqu’un problème apparaît, on peut utiliser un démarrage plus limité pour vérifier si un pilote, un service ou une application participe au problème.

Le but d’un mode de diagnostic est de recueillir de l’information ou de rendre possible une correction. Un ordinateur qui fonctionne en mode sans échec n’est pas nécessairement réparé.

### 6.2. Le mode sans échec

Le **mode sans échec** démarre Windows avec seulement les pilotes et les services essentiels. Certaines fonctions peuvent donc être désactivées et l’affichage peut être différent du mode normal.

Ce mode est surtout utilisé pour le **dépannage**.

Si un problème disparaît en mode sans échec, cela signifie qu’un élément chargé pendant le démarrage normal peut être responsable, par exemple :

* un pilote;
* un logiciel;
* un service Windows.

Le mode sans échec aide donc à **trouver l’origine d’un problème**, mais il ne permet pas à lui seul de savoir exactement quel composant est responsable.

Pour accéder au **mode sans échec** dans Windows 11 :

1. Ouvrez **Paramètres > Système > Récupération**.
2. Dans **Démarrage avancé**, choisissez **Redémarrer maintenant**.

Une autre méthode consiste à maintenir la touche **Maj (Shift)** enfoncée pendant que vous cliquez sur **Redémarrer**.

Après le redémarrage :

**Dépannage > Options avancées > Paramètres de démarrage > Redémarrer**

Choisissez ensuite le mode souhaité :

* **4 ou F4** : mode sans échec;
* **5 ou F5** : mode sans échec avec réseau;
* **6 ou F6** : mode sans échec avec invite de commandes.

La touche **F8** n’est plus une méthode fiable sur les versions modernes de Windows.

Pour quitter le mode sans échec, il suffit généralement de **redémarrer l’ordinateur normalement**.

| **Mode**                                     | **Ce qui change**                                                           | **Utilisation possible**                                          |
| -------------------------------------------- | --------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| **Mode sans échec**                          | Windows démarre avec seulement les pilotes et services essentiels.          | Diagnostiquer un problème ou supprimer un logiciel problématique. |
| **Mode sans échec avec réseau**              | Même fonctionnement que le mode sans échec, mais avec les fonctions réseau. | Accéder à Internet ou au réseau pendant le dépannage.             |
| **Mode sans échec avec invite de commandes** | Windows démarre avec une invite de commandes au lieu du bureau habituel.    | Exécuter des commandes de dépannage.                              |

### 6.3. Le démarrage minimal&#x20;

Le **démarrage minimal**, ou **Clean Boot**, permet de démarrer Windows avec le moins possible de logiciels et de services non essentiels.

Il est surtout utilisé pour trouver si un **programme ou un service installé** cause un problème.

Pour le faire, on utilise notamment **msconfig** et les applications de démarrage. Dans l’onglet **Services**, il faut d’abord cocher **Masquer tous les services Microsoft**, puis désactiver les services restants pour faire le test.

On peut ensuite réactiver les services et programmes petit à petit jusqu’à trouver celui qui cause le problème.

Le démarrage minimal est différent du **mode sans échec** :

* le **mode sans échec** démarre Windows avec très peu de pilotes et de services;
* le **démarrage minimal** conserve un fonctionnement plus normal de Windows, mais réduit surtout les programmes et services ajoutés.

## 7. Les disques et le partitionnement&#x20;

### 7.1. Disque physique et disque virtuel

Un **disque physique** est un vrai périphérique de stockage, par exemple un **SSD NVMe** ou un **disque dur SATA**.

Dans VMware Workstation, une machine virtuelle utilise plutôt un **disque virtuel**. Ce disque est généralement enregistré sous la forme d’un ou plusieurs fichiers **VMDK** sur l’ordinateur hôte.

Pour Windows installé dans la VM, ce disque virtuel ressemble à un vrai disque.

La taille du disque virtuel et l’espace réellement utilisé sur l’ordinateur hôte peuvent être différents. Par exemple, un disque virtuel de **80 Go** peut utiliser seulement **20 Go** sur le disque physique si peu de données y sont enregistrées.

Il faut donc surveiller :

* l’espace libre dans la machine virtuelle;
* l’espace libre sur le disque de l’ordinateur hôte.

### 7.2. Disques, partitions et volumes sous Windows

Le disque fournit la capacité. Le partitionnement définit des régions sur ce disque. Le système de fichiers organise les fichiers à l’intérieur d’un espace de stockage. La lettre de lecteur est un moyen utilisé par Windows pour rendre un volume accessible.

Une partition est une région définie dans la table de partitionnement. Un volume est un espace logique que Windows peut présenter au système de fichiers et monter. Sur un disque de base ordinaire, un volume correspond généralement à une partition. Dans des organisations plus complexes, un volume peut reposer sur plusieurs disques.

{% hint style="info" %}
La lettre D: ne prouve donc pas qu’un deuxième disque physique existe. Elle peut désigner une autre partition du même disque, un disque distinct ou un lecteur optique.
{% endhint %}

Exemple. Un SSD de 1 To contient C: pour Windows et D: pour des données. Si le SSD tombe complètement en panne, les deux volumes sont touchés. Leur séparation peut faciliter l’organisation, mais elle n’isole pas les données de la panne du périphérique.

### 7.3. Initialiser un disque

Lorsqu’on ajoute un nouveau disque à Windows, il faut généralement d’abord **l’initialiser**. Cette étape consiste à choisir une méthode de partitionnement, généralement **MBR** ou **GPT**.

L’initialisation ne suffit pas pour commencer à enregistrer des fichiers sur le disque.

Pour préparer un disque classique, on effectue généralement les étapes suivantes :

1. **Initialiser le disque** en MBR ou GPT.
2. **Créer une partition ou un volume**.
3. **Formater** le volume avec un système de fichiers, par exemple NTFS.
4. **Attribuer une lettre de lecteur**, par exemple D:.

Windows peut regrouper plusieurs de ces étapes dans le même assistant.

### 7.4. La norme MBR

**MBR** signifie _Master Boot Record_. C’est une ancienne méthode utilisée pour organiser les partitions d’un disque.

Avec des secteurs de 512 octets, MBR peut gérer des disques d’environ **2 To maximum**.

Un disque MBR peut contenir jusqu’à **4 partitions principales**.

Pour dépasser cette limite, on peut remplacer une partition principale par une **partition étendue**, dans laquelle on crée plusieurs **lecteurs logiques**.

MBR est surtout utilisé pour assurer la compatibilité avec des ordinateurs ou des systèmes plus anciens.

Pour une nouvelle installation de **Windows 11**, on utilise généralement plutôt **GPT**.

### 7.5. La norme GPT&#x20;

**GPT** signifie _GUID Partition Table_. C’est la méthode de partitionnement moderne utilisée sur la plupart des ordinateurs récents.

GPT permet de gérer des disques de très grande capacité et Windows peut généralement créer jusqu’à **128 partitions** sur un disque GPT.

Contrairement à MBR, GPT n’utilise pas les notions de partition principale, étendue et logique.

GPT conserve aussi une **copie de secours** des informations de partitionnement et utilise des mécanismes permettant de détecter certaines erreurs dans ces informations.

Pour les installations modernes de **Windows 11 avec UEFI**, GPT est généralement le choix recommandé.

| Critère                       | MBR                                                               | GPT                                                             |
| ----------------------------- | ----------------------------------------------------------------- | --------------------------------------------------------------- |
| Contexte fréquent             | Compatibilité avec des configurations anciennes                   | Installations modernes et disques de grande capacité            |
| Limite à connaître            | Environ 2 Tio avec secteurs logiques de 512 octets                | Capacités bien supérieures aux besoins ordinaires du poste      |
| Organisation des partitions   | Quatre entrées principales, avec possibilité de partition étendue | Jusqu’à 128 partitions dans l’usage Windows courant             |
| Démarrage habituel de Windows | BIOS traditionnel et disque MBR                                   | UEFI et disque système GPT                                      |
| Protection de la table        | Pas de copie de secours comparable à GPT                          | Structures principales et de secours avec contrôles d’intégrité |

### 7.6. Les partitions créées par Windows

Sur une installation UEFI classique, l’assistant prépare plusieurs partitions. Toutes ne reçoivent pas une lettre dans l’Explorateur. Leur absence de l’Explorateur ne signifie pas qu’elles sont inutiles

| **Partition**    | **À quoi elle sert**                                                      | **Format habituel**            |
| ---------------- | ------------------------------------------------------------------------- | ------------------------------ |
| **EFI (ESP)**    | Contient les fichiers nécessaires pour démarrer Windows avec UEFI.        | FAT32, sans lettre             |
| **MSR**          | Espace réservé par Windows pour gérer certaines opérations sur le disque. | Pas de fichiers utilisateur    |
| **Windows**      | Contient Windows, les logiciels et les fichiers des utilisateurs.         | NTFS, généralement **C:**      |
| **Récupération** | Contient les outils permettant de réparer ou récupérer Windows.           | Généralement NTFS, sans lettre |

La taille exacte des petites partitions peut varier selon l’image, la version et les contraintes du disque. Pour une première installation sur un disque vide, laissez l’assistant les créer. Supprimer une partition peut compromettre le démarrage ou la récupération.

### 7.7. Utiliser Gestion des disques

Pour ouvrir **Gestion des disques** :

* faites un clic droit sur **Démarrer** puis choisissez **Gestion des disques**;
* ou exécutez `diskmgmt.msc`.

Cet outil permet de voir les **disques physiques**, leurs **partitions** et leurs **volumes**.

Un disque peut apparaître comme :

* **non initialisé** : il faut d’abord choisir MBR ou GPT;
* **hors connexion** : Windows ne l’utilise pas actuellement;
* **espace non alloué** : cet espace n’appartient encore à aucune partition ou volume.

Un espace non alloué n’apparaît donc pas encore dans l’Explorateur de fichiers.

Pour préparer un nouveau disque de données :

1. Vérifiez que vous travaillez sur le bon disque.
2. Initialisez-le, généralement en **GPT**.
3. Créez un **volume simple**.
4. Choisissez sa taille.
5. Attribuez une lettre, par exemple **D:**.
6. Formatez-le, généralement en **NTFS**.
7. Donnez-lui un nom.
8. Vérifiez qu’il apparaît dans l’Explorateur de fichiers.

Un **volume simple** créé dans Gestion des disques n’est pas la même chose qu’un **espace simple** créé avec les Espaces de stockage Windows.

### 7.8. Réduire et étendre un volume

**Réduire un volume** permet de diminuer sa taille afin de créer de l’**espace non alloué**. Cet espace peut ensuite servir à créer un nouveau volume.

Windows ne peut pas toujours utiliser tout l’espace libre disponible, car certains fichiers système ne peuvent pas être déplacés.

**Étendre un volume** permet d’augmenter sa taille en utilisant de l’espace non alloué.

Avec l’outil **Gestion des disques**, cet espace doit généralement être placé **immédiatement à droite du volume** que l’on veut agrandir.

**Exemple :**

`C: | Récupération | Espace non alloué`

Dans cette situation, Windows ne peut pas simplement agrandir **C:**, car la partition de récupération se trouve entre **C:** et l’espace non alloué.

Il ne faut pas supprimer une partition de récupération sans connaître son rôle et les conséquences possibles.

### 7.9. Formater et convertir

**Formater un volume** prépare son système de fichiers afin qu’il puisse enregistrer des fichiers, par exemple avec **NTFS**.

Un **formatage rapide** recrée surtout les structures du système de fichiers. Il ne garantit pas que les anciennes données sont complètement effacées.

Il ne faut pas confondre :

* **Convertir MBR en GPT** : modifie la façon dont les partitions sont organisées sur le disque.
* **Formater en NTFS** : prépare un volume pour stocker et organiser des fichiers.

Avant de modifier le partitionnement d’un disque, il est recommandé de **sauvegarder les données importantes**.

## 8. Les systèmes de fichiers&#x20;

Un **système de fichiers** est la méthode utilisée pour organiser et retrouver les fichiers sur un disque ou un volume.

Il permet notamment de gérer :

* le nom des fichiers
* leur emplacement
* leur taille
* leurs dates
* et, selon le système de fichiers, les permissions d’accès.

Par exemple, lorsqu’on ouvre :

`D:\Comptabilite\budget.xlsx`

le système de fichiers permet à Windows de savoir où se trouve réellement ce fichier sur le disque.

### 8.1. FAT32

**FAT32** est un ancien système de fichiers encore utilisé pour certains supports amovibles, comme les clés USB, surtout pour sa grande compatibilité avec différents appareils.

Sa principale limite est la taille maximale d’un fichier : environ **4 Go**.

Par exemple, une clé USB FAT32 peut avoir **20 Go d’espace libre**, mais refuser un fichier de **6 Go** parce que ce fichier est trop gros.

FAT32 ne possède pas certaines fonctions avancées de NTFS, comme les **permissions** et la **journalisation**.

Pour la partition principale de **Windows 11**, on utilise plutôt **NTFS**.

### 8.2. NTFS&#x20;

**NTFS** est le système de fichiers principalement utilisé par Windows pour ses disques internes.

Il permet notamment :

* de stocker de **très gros fichiers**;
* de gérer des **permissions d’accès**;
* d’utiliser la **journalisation** pour aider à maintenir le système de fichiers en bon état.

Les permissions NTFS permettent, par exemple, d’autoriser un utilisateur à **lire** un dossier et un autre à **modifier** son contenu.

La **journalisation** aide Windows à récupérer plus facilement après certaines interruptions ou erreurs. Elle ne remplace cependant pas une **sauvegarde**.

**Exemple :** pour un SSD contenant des machines virtuelles Windows, **NTFS est un bon choix**, car les fichiers des VM peuvent être très volumineux.

### 8.3. exFAT&#x20;

**exFAT** est un système de fichiers souvent utilisé pour les **clés USB** et les **disques externes**.

Il permet de stocker des **fichiers de plus de 4 Go**, contrairement à FAT32.

Il est aussi bien reconnu par plusieurs systèmes récents, comme Windows et macOS, ce qui le rend pratique pour **échanger des fichiers entre différents ordinateurs**.

Par contre, exFAT ne possède pas toutes les fonctions avancées de NTFS, comme les **permissions** et la **journalisation**.

Pour éviter les problèmes, il est recommandé d’**éjecter correctement** le disque ou la clé USB avant de le débrancher.

## 9. Les technologies RAID&#x20;

**RAID** signifie _Redundant Array of Independent Disks_. Cette technologie permet de combiner plusieurs disques pour améliorer selon le cas :

* la **capacité**;
* les **performances**;
* la **tolérance aux pannes**.

Le fonctionnement dépend du **niveau RAID** utilisé.

Pour comprendre le principe, imaginez un fichier découpé en plusieurs blocs : **A, B, C et D**. Selon le type de RAID, ces blocs peuvent être :

* répartis entre plusieurs disques;
* copiés sur plusieurs disques;
* accompagnés d’informations permettant de reconstruire des données perdues.

Attention : malgré le mot **Redundant**, le **RAID 0 ne possède aucune redondance**. Si un disque tombe en panne, les données sont perdues.

On distingue aussi :

* **Capacité brute** : somme de la capacité de tous les disques.
* **Capacité utile** : espace réellement disponible pour stocker les données après avoir réservé l’espace nécessaire à la redondance.

**Exemple :** avec 2 disques de 1 To, la capacité brute est de **2 To**, mais la capacité utile dépend du niveau RAID choisi.

### 9.1. Le RAID 0 et la répartition des blocs

Le RAID 0 utilise au moins deux disques et répartit les blocs en bandes, une méthode appelée _striping_. Les disques peuvent participer ensemble aux lectures ou aux écritures.

| Ordre des blocs | Disque 1 | Disque 2 |
| --------------- | -------- | -------- |
| Première bande  | A        | B        |
| Deuxième bande  | C        | D        |
| Troisième bande | E        | F        |

Avec **2 disques de 1 To**, on obtient environ **2 To de capacité utile**, car aucune copie des données n’est conservée.

Par contre, le RAID 0 n’offre **aucune tolérance aux pannes**.

Si un seul disque tombe en panne, une partie des données devient manquante et le volume RAID peut devenir inutilisable.

Le RAID 0 peut donc être intéressant pour :

* améliorer certaines performances;
* stocker des données temporaires;
* stocker des données qui peuvent facilement être recréées.

Il ne convient pas pour protéger des fichiers importants.

Les performances obtenues dépendent aussi du type de disques, du contrôleur et de l’utilisation de l’ordinateur.

### 9.2. Le RAID 1 et le miroir

Dans un miroir classique à deux disques, les mêmes blocs sont conservés sur chacun des deux membres.

| Ordre des blocs | Disque 1 | Disque 2 |
| --------------- | -------- | -------- |
| Premier bloc    | A        | A        |
| Deuxième bloc   | B        | B        |
| Troisième bloc  | C        | C        |

Le **RAID 1** utilise au minimum deux disques et conserve une **copie identique des données** sur chacun d’eux.

Avec **2 disques de 1 To**, la capacité utile est d’environ **1 To**.

Si un disque tombe en panne, les données restent accessibles sur l’autre disque.

Le RAID passe alors en état **dégradé** : il fonctionne encore, mais il n’est plus protégé contre une deuxième panne. Il faut donc remplacer le disque défectueux rapidement.

{% hint style="info" %}
Attention : le RAID 1 n’est **pas une sauvegarde**. Si un fichier est supprimé ou modifié par erreur, cette modification est aussi reproduite sur l’autre disque.
{% endhint %}

### 9.3. Le RAID 5 et la parité simple

Le **RAID 5** utilise au minimum **3 disques**.

Les données sont réparties entre les disques et le système ajoute aussi des informations appelées **parité**.

La parité permet de **reconstruire les données si un seul disque tombe en panne**.

Contrairement au RAID 1, la parité n’est pas une copie complète des fichiers. Ce sont des informations calculées qui permettent de retrouver les données manquantes.

La parité est répartie entre les différents disques.

**Exemple :**

Avec **4 disques de 2 To** :

* capacité brute : **8 To**;
* capacité utile : environ **6 To**;
* l’équivalent de **2 To** est utilisé pour la parité.

Le RAID 5 peut donc continuer à fonctionner après la panne d’**un seul disque**.

Par contre, si **deux disques tombent en panne**, les données risquent d’être perdues.

Les écritures peuvent aussi être un peu plus lentes, car le système doit calculer et mettre à jour la parité.

### 9.4. Le RAID 6 et la double parité

Le **RAID 6** utilise au minimum **4 disques**.

Il fonctionne un peu comme le RAID 5, mais utilise **deux informations de parité** au lieu d’une seule.

Cela lui permet de continuer à fonctionner même si **deux disques tombent en panne**.

**Exemple :**

Avec **4 disques de 2 To** :

* capacité brute : **8 To**;
* capacité utile : environ **4 To**;
* l’équivalent de **2 disques** est utilisé pour la redondance.

Le RAID 6 offre donc une meilleure tolérance aux pannes que le RAID 5, mais il utilise davantage d’espace pour la protection des données.

Les écritures peuvent également être plus lentes, car le système doit calculer et gérer deux informations de parité.

Le RAID 6 est particulièrement intéressant lorsque l’on veut réduire le risque de perte de données pendant le remplacement ou la reconstruction d’un disque défectueux.

### 9.5. Le RAID 10

Le **RAID 10** combine le **RAID 1** et le **RAID 0**.

Il utilise au minimum **4 disques**, regroupés en **paires miroir**.

Par exemple, avec 4 disques :

* les disques 1 et 2 forment une première paire;
* les disques 3 et 4 forment une deuxième paire.

Les données sont réparties entre les deux paires, puis copiées à l’intérieur de chaque paire.

Avec **4 disques de 2 To** :

* capacité brute : **8 To**;
* capacité utile : environ **4 To**.

Le RAID 10 peut continuer à fonctionner après la panne d’un disque.

Il peut aussi tolérer **deux pannes**, mais seulement si elles ne touchent pas les deux disques de la même paire.

Par exemple :

* panne du disque 1 et du disque 3 : le RAID peut continuer à fonctionner;
* panne du disque 1 et du disque 2 : le RAID devient inutilisable.

Le RAID 10 offre donc de bonnes performances et une bonne tolérance aux pannes, mais seulement environ **la moitié de la capacité totale** est utilisable.

