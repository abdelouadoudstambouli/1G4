---
hidden: true
---

# Chapitre 3 - Assemblage, UEFI, POST, maintenance et dépannage

## Objectifs d'apprentissage

&#x20;•     Préparer et décrire l'assemblage sécuritaire d'un ordinateur de bureau;

•     Vérifier la compatibilité d'une mise à niveau;

•     Expliquer le rôle du micrologiciel BIOS ou UEFI;

•     Décrire la séquence de démarrage et le rôle du POST;

•     Appliquer les principes de maintenance préventive;

•     Suivre une procédure structurée pour résoudre un problème courant.

## 1. Assemblage et mise à niveau d'un ordinateur&#x20;

Assembler un ordinateur, c’est **installer les différents composants dans le boîtier, les connecter ensemble et vérifier que l’ordinateur fonctionne correctement**.

Faire une **mise à niveau**, c’est **ajouter ou remplacer un composant** pour améliorer l’ordinateur, par exemple en ajoutant de la mémoire RAM ou en installant un SSD plus rapide.

### 1.1. Préparer l'assemblage ou la mise à niveau&#x20;

Avant d’ouvrir un ordinateur, il est important de bien se préparer. Cela permet d’éviter d’acheter un composant incompatible, de perdre des données ou d’endommager le matériel.

* **Définir le besoin :** déterminer ce qu’on veut améliorer : la vitesse, la mémoire, le stockage, les ports ou les performances graphiques.
* **Vérifier le matériel actuel :** noter les principaux composants déjà présents, comme la carte mère, le processeur, la RAM, le stockage, l’alimentation et le boîtier.
* **Vérifier la compatibilité :** s’assurer que le nouveau composant peut fonctionner avec l’ordinateur et qu’il possède les bons formats et connecteurs.
* **Sauvegarder les données :** faire une copie des fichiers importants avant de commencer.
* **Préparer l’espace de travail :** travailler sur une surface propre, stable, bien éclairée et suffisamment dégagée.

### 1.2. Vérification de compatibilité&#x20;

Avant d’acheter ou d’installer un composant, il faut vérifier qu’il est compatible avec le reste de l’ordinateur.

* **Processeur et carte mère :** le processeur doit utiliser le même socket que la carte mère. Il faut aussi vérifier que la carte mère et son BIOS/UEFI prennent en charge ce processeur.
* **Mémoire RAM :** il faut choisir le bon type de mémoire qui fonctionne avec la carte mère, par exemple DDR4 ou DDR5. Il faut aussi vérifier le nombre de barrettes qu’on peut installer, la capacité maximale et les vitesses supportées.
* **Carte graphique :** la carte mère doit avoir un port PCIe compatible. Il faut aussi vérifier que la carte graphique entre dans le boîtier et que l’alimentation est assez puissante pour la faire fonctionner.
* **Stockage M.2 :** tous les SSD M.2 ne sont pas identiques. Certains utilisent SATA et d’autres PCIe/NVMe. Il faut donc vérifier le type de connexion et la taille du SSD acceptés par la carte mère.
* **Bloc d’alimentation :** l’alimentation doit entrer dans le boîtier, fournir assez de puissance et posséder les connecteurs nécessaires pour les composants.
* **Boîtier et refroidissement :** il faut vérifier qu’il y a assez d’espace pour la carte mère, la carte graphique, l’alimentation, le refroidisseur du processeur et les ventilateurs.
* **Système d’exploitation :** il faut aussi vérifier que le matériel est compatible avec Windows, Linux ou le système utilisé et que les pilotes nécessaires sont disponibles.

{% hint style="info" %}
Deux composants peuvent parfois être installés ensemble sans pour autant être compatibles. Par exemple, un SSD M.2 SATA ne fonctionnera pas dans un port M.2 conçu uniquement pour les SSD PCIe/NVMe.
{% endhint %}

### 1.3. Ordre général d'assemblage&#x20;

L’ordre d’installation peut changer selon le boîtier et les composants utilisés. L’important est de travailler dans un ordre logique et de garder les connecteurs faciles d’accès.

•     Préparer le boîtier. Retirer les panneaux, vérifier les entretoises et installer la plaque arrière si la carte mère en utilise une séparée.

•     Installer le processeur. Aligner les repères du processeur et du socket. Déposer le processeur sans forcer, puis verrouiller le mécanisme.

•     Installer la RAM et le SSD M.2. Utiliser les emplacements recommandés par le manuel et s'assurer que les loquets sont fermés.

•     Installer le refroidisseur. Appliquer la bonne quantité de pâte thermique si nécessaire, serrer progressivement et brancher le ventilateur sur CPU\_FAN.

•     Fixer la carte mère. L'aligner sur les entretoises et serrer les vis sans excès.

•     Installer l'alimentation. Orienter son ventilateur selon les ouvertures du boîtier et préparer les câbles nécessaires.

•     Installer les unités de stockage et les cartes d'extension. Fixer les composants et verrouiller les cartes PCIe.

•     Brancher les câbles. Relier l'alimentation, les données, les ventilateurs, les ports du boîtier et les boutons du panneau avant.

•     Organiser les câbles. Éviter qu'ils touchent les ventilateurs ou bloquent la circulation d'air.

•     Faire une inspection finale. Vérifier les vis, les connecteurs, le refroidisseur et l'absence d'objet libre dans le boîtier.

### 1.4. Connecteurs à reconnaître&#x20;

* ATX 24 broches : alimentation principale de la carte mère.
* EPS CPU 4+4 ou 8 broches : alimentation du processeur, généralement près du haut de la carte mère.
* PCIe ou 12V-2x6 : alimentation supplémentaire de certaines cartes graphiques. Utiliser uniquement les câbles prévus par le fabricant de l'alimentation.
* SATA données : relie une unité SATA à la carte mère.
* SATA alimentation : alimente un SSD, un disque dur ou certains accessoires.
* CPU\_FAN, SYS\_FAN ou CHA\_FAN : alimente et contrôle les ventilateurs. Le ventilateur du processeur doit être relié à CPU\_FAN.
* Panneau avant : petits connecteurs du bouton d'alimentation, du bouton de réinitialisation et des voyants. Leur polarité peut être importante pour les DEL.
* USB et audio internes : relient les ports avant du boîtier à la carte mère.

### 1.5. Démonstration d’un assemblage

Une démonstration vidéo complète de l’assemblage d’un ordinateur est disponible dans le cours intitulé **Notions de base sur le matériel informatique (Computer Hardware Basics)**,offert sur la plateforme **Cisco Networking Academy (NetAcad)**.

Lien vers NetAcad : [https://www.netacad.com/](https://www.netacad.com/)&#x20;

### 1.6. Mise à niveau selon le besoin&#x20;

Avant de remplacer un composant, il faut d’abord trouver ce qui ralentit réellement l’ordinateur:&#x20;

* **Pas assez de mémoire RAM :** si l’ordinateur devient lent quand plusieurs applications ou onglets sont ouverts, ajouter de la RAM peut aider. Il faut d’abord vérifier si la mémoire est vraiment presque pleine.
* **Stockage plein ou lent :** remplacer le disque par un SSD plus grand ou plus rapide peut améliorer l’espace disponible et réduire les temps de chargement.
* **Carte graphique trop faible :** une carte graphique plus performante peut être utile pour les jeux, la 3D ou certaines applications. Il faut cependant vérifier que l’alimentation est assez puissante et que la carte entre dans le boîtier.
* **Processeur trop lent :** changer de processeur peut améliorer les performances, mais il faut vérifier sa compatibilité avec la carte mère. Dans certains cas, il faudra aussi remplacer la carte mère ou la RAM.
* **Températures trop élevées :** avant de remplacer le refroidisseur, il faut vérifier la poussière, les ventilateurs, la pâte thermique et la circulation de l’air dans le boîtier.
* **Alimentation insuffisante :** si de nouveaux composants demandent plus de puissance, il peut être nécessaire de remplacer le bloc d’alimentation. Le nouveau modèle doit fournir assez de puissance et avoir les bons connecteurs.

## 2. UEFI et micrologiciel&#x20;

Un micrologiciel, ou firmware, est un logiciel enregistré dans une mémoire non volatile d'un appareil.&#x20;

Sur la carte mère, ce micrologiciel initialise le matériel et prépare le démarrage du système d'exploitation.

* **BIOS :** ancienne technologie utilisée pour démarrer et configurer les ordinateurs. Le mot « BIOS » est encore souvent utilisé aujourd’hui, même si les ordinateurs récents utilisent plutôt l’UEFI.

<figure><img src=".gitbook/assets/image (42).png" alt="" width="480"><figcaption><p>Interface BIOS classique</p></figcaption></figure>

* **UEFI :** version moderne du BIOS. Il offre plus de fonctions et permet notamment de gérer le démarrage de l’ordinateur, le **Secure Boot** et plusieurs paramètres du matériel.

<figure><img src=".gitbook/assets/image (43).png" alt=""><figcaption><p>Interface UEFI</p></figcaption></figure>

### 2.1. Où sont conservés le micrologiciel et les réglages?

Généralement, ils se trouvent dans :&#x20;

* **Puce flash :** c’est une petite mémoire située directement sur la carte mère qui contient le programme UEFI. Lorsqu’on met à jour l’UEFI, le contenu de cette mémoire est modifié.
* **NVRAM :** c’est une petite zone de mémoire située sur la carte mère, souvent dans la même mémoire flash que l’UEFI. Elle conserve certains réglages, comme l’ordre de démarrage et certaines options matérielles.
* **Pile RTC/CMOS :** Elle sert surtout à maintenir l’horloge de l’ordinateur lorsque celui-ci est débranché.

### 2.2. Accéder à l'interface UEFI

On accède généralement à l'UEFI en appuyant sur une touche au début du démarrage. Les touches fréquentes sont Suppr, F2, F10, F12 ou Échap.&#x20;

La touche dépend du fabricant. Certains systèmes permettent aussi de redémarrer vers l'UEFI depuis les options de récupération du système d'exploitation.

