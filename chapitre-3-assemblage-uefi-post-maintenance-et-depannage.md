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

• **Préparer le boîtier**: Retirer les panneaux, vérifier les entretoises et installer la plaque arrière si la carte mère en utilise une séparée.

• **Installer le processeur.** Aligner les repères du processeur et du socket. Déposer le processeur sans forcer, puis verrouiller le mécanisme.

• **Installer la RAM et le SSD M.2**. Utiliser les emplacements recommandés par le manuel et s'assurer que les loquets sont fermés.

• **Installer le refroidisseur**. Appliquer la bonne quantité de pâte thermique si nécessaire, serrer progressivement et brancher le ventilateur sur CPU\_FAN.

• **Fixer la carte mère**. L'aligner sur les entretoises et serrer les vis sans excès.

• **Installer l'alimentation**. Orienter son ventilateur selon les ouvertures du boîtier et préparer les câbles nécessaires.

• **Installer les unités de stockage et les cartes d'extension**. Fixer les composants et verrouiller les cartes PCIe.

• **Brancher les câbles**. Relier l'alimentation, les données, les ventilateurs, les ports du boîtier et les boutons du panneau avant.

• **Organiser les câbles**. Éviter qu'ils touchent les ventilateurs ou bloquent la circulation d'air.

•  **Faire une inspection finale**. Vérifier les vis, les connecteurs, le refroidisseur et l'absence d'objet libre dans le boîtier.

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

### 2.3. Consulter et modifier les paramètres matériels

L’interface UEFI permet de consulter les informations sur les composants détectés et de modifier certains paramètres matériels afin d’adapter le fonctionnement de l’ordinateur à ses besoins.

* **Date et heure :** permet de régler l’horloge de l’ordinateur. Une heure incorrecte peut causer des problèmes avec les certificats, les journaux et les mises à jour.
* **Informations système :** affiche les principaux composants détectés, comme le processeur, la quantité de mémoire RAM, les unités de stockage et la version de l’UEFI.
* **Profil mémoire XMP ou EXPO :** permet d’utiliser la mémoire RAM à la fréquence prévue par son fabricant. Un mauvais réglage peut toutefois rendre l’ordinateur instable.
* **Virtualisation :** active les fonctions nécessaires à l’utilisation de machines virtuelles. Cette option peut porter le nom Intel VT-x, AMD-V ou SVM.
* **Contrôleur de stockage :** permet de choisir le mode de fonctionnement des unités de stockage, comme AHCI ou RAID. Modifier ce réglage après l’installation du système peut empêcher son démarrage.
* **Ventilateurs et températures :** permet de vérifier les températures, de surveiller la vitesse des ventilateurs et, sur certains ordinateurs, de modifier leur fonctionnement.
* **Périphériques intégrés :** permet d’activer ou de désactiver certains composants de la carte mère, comme l’audio, le réseau ou les ports USB.
* Gestion de l'énergie : règle le comportement après une panne de courant, le réveil par le réseau et certains modes de veille.
* Limites de puissance et surcadençage : modifient le comportement du processeur ou de la mémoire. Ces réglages peuvent augmenter la chaleur, la consommation et l'instabilité.

### 2.4. Fonctions de sécurité de l’UEFI

L’UEFI comprend plusieurs fonctions de sécurité qui permettent de protéger le démarrage de l’ordinateur, les clés de chiffrement et l’accès aux paramètres matériels.

* **Secure Boot (démarrage sécurisé) :** fonction qui vérifie que les programmes lancés au démarrage sont reconnus et fiables. Elle aide à empêcher l’exécution de logiciels malveillants avant le chargement du système d’exploitation.
* **TPM (Trusted Platform Module) :** composant de sécurité qui conserve et protège certaines informations sensibles, comme les clés utilisées pour chiffrer le disque. Il peut prendre la forme d’une puce sur la carte mère ou être intégré au micrologiciel.
* Mot de passe UEFI : peut protéger l'accès aux réglages. Il ne remplace pas le mot de passe du système d'exploitation et sa perte peut compliquer la maintenance.
* Démarrage externe : désactiver ou contrôler le démarrage USB peut réduire certains risques dans un environnement géré.

### 2.5. Mettre à jour l'UEFI

Une mise à jour de l’UEFI peut corriger des problèmes de sécurité ou de stabilité et ajouter la compatibilité avec du nouveau matériel. Cette opération doit toutefois être réalisée avec prudence, car une interruption pendant la mise à jour peut empêcher l’ordinateur de démarrer.

Avant de commencer, il faut :

* vérifier le modèle exact de la carte mère ou de l’ordinateur;
* consulter la description de la mise à jour pour savoir si elle est réellement nécessaire;
* télécharger le fichier uniquement depuis le site officiel du fabricant;
* sauvegarder les données importantes et noter les réglages actuels de l’UEFI;
* conserver la clé de récupération si le disque est chiffré;
* brancher l’ordinateur sur une alimentation stable;
* suivre les instructions du fabricant et ne jamais éteindre l’ordinateur pendant l’opération.

Après la mise à jour, il est important de vérifier les réglages de l’UEFI et de s’assurer que l’ordinateur démarre normalement.

### 2.6. Réinitialiser les réglages de l’UEFI

Si une modification dans l’UEFI cause un problème, on peut remettre les réglages par défaut avec l’option **Load Defaults** ou **Optimized Defaults**.&#x20;

Si l’interface UEFI n’est plus accessible, il est possible de réinitialiser les réglages à l’aide du bouton/cavalier **Clear CMOS** ou, sur certaines cartes mères, en retirant temporairement la pile.&#x20;

Cette réinitialisation ne supprime pas l’UEFI : elle remet seulement ses paramètres à leur valeur par défaut.

## 3. Séquence de démarrage et POST

### 3.1. Vue d’ensemble de la séquence de démarrage

La séquence de démarrage est l'ensemble des étapes réalisées entre l'appui sur le bouton et l'affichage du système d'exploitation.&#x20;

Chaque étape dépend de la précédente. Cette chaîne permet de localiser plus rapidement une panne.

<figure><img src=".gitbook/assets/image (44).png" alt="" width="563"><figcaption><p>Séquence simplifiée de démarrage d'un ordinateur moderne</p></figcaption></figure>

* **Mise sous tension :** lorsqu’on appuie sur le bouton, le bloc d’alimentation fournit l’électricité nécessaire aux composants.
* **Démarrage de l’UEFI :** le processeur commence à exécuter le programme UEFI enregistré sur la carte mère.
* **POST et initialisation :** l’UEFI vérifie et prépare les composants essentiels, comme le processeur, la mémoire RAM et la carte graphique.
* **Détection des périphériques :** l’UEFI recherche les unités de stockage, les cartes d’extension et les autres périphériques connectés.
* **Choix de l’unité de démarrage :** l’UEFI consulte l’ordre de démarrage pour déterminer où se trouve le système d’exploitation.
* **Lancement du gestionnaire de démarrage :** un petit programme présent sur l’unité de stockage indique quel système d’exploitation doit être lancé.
* **Chargement du système d’exploitation :** Windows, Linux ou un autre système charge ses fichiers, ses pilotes et ses services jusqu’à l’affichage de l’écran de connexion.

### 3.2. Le POST : définition et rôle

**POST** signifie _Power-On Self-Test_. Il s’agit d’une vérification automatique effectuée par l’UEFI au démarrage de l’ordinateur.&#x20;

Le POST vérifie que les composants essentiels, comme le processeur, la mémoire RAM et l’affichage, sont détectés et fonctionnent suffisamment bien pour poursuivre le démarrage.

### 3.3. Composants vérifiés et initialisés pendant le POST

Pendant le POST, l’UEFI vérifie notamment :

* si le processeur est présent et peut démarrer;
* si la mémoire RAM est détectée et peut être initialisée;
* si le système d’affichage peut fonctionner;
* si les unités de stockage sont détectées;
* si le ventilateur du processeur fonctionne, lorsque cette vérification est disponible;
* si les principaux périphériques et cartes d’extension sont reconnus;
* si les réglages de l’UEFI sont valides.

Le POST effectue seulement une vérification de base. Un ordinateur peut donc réussir le POST et rencontrer plus tard un problème de mémoire, de stockage, de pilote ou de surchauffe.

### 3.4. Diagnostiquer un échec du POST

<figure><img src=".gitbook/assets/image (45).png" alt="" width="563"><figcaption><p>Résultat possible lors d'une panne </p></figcaption></figure>

Lorsqu’un ordinateur ne réussit pas le POST, le système d’exploitation ne peut pas commencer à se charger. Il faut alors observer les signes fournis par l’ordinateur, comme l’absence d’image, les messages affichés, les bips ou les voyants de diagnostic CPU, DRAM, VGA et BOOT.&#x20;

<figure><img src=".gitbook/assets/image (46).png" alt="" width="563"><figcaption><p>Les voyants de diagnostic CPU, DRAM, VGA et BOOT.</p></figcaption></figure>

{% hint style="info" %}
Les voyants **CPU, DRAM, VGA et BOOT** sont de petites DEL de diagnostic présentes sur certaines cartes mères. Si un voyant reste allumé, il peut signaler un problème avec l’élément correspondant :

* **CPU :** problème lié au processeur ou à son alimentation;
* **DRAM :** problème de détection ou d’initialisation de la mémoire RAM;
* **VGA :** problème avec la carte graphique ou l’affichage;
* **BOOT :** aucune unité ou aucun système de démarrage valide n’a été trouvé.
{% endhint %}

Ces indices permettent de déterminer à quelle étape le démarrage s’est arrêté et quel composant doit être vérifié.

&#x20;Comme leur signification peut varier selon le fabricant, il est important de consulter le manuel de la carte mère ou de l’ordinateur.

### 3.5. Fin du POST et détection des périphériques

Lorsque les composants essentiels ont été vérifiés et initialisés, le POST se termine. L’UEFI poursuit alors la détection des périphériques connectés à l’ordinateur, notamment :

* les SSD et les disques durs;
* les clés USB et les autres périphériques externes;
* les cartes d’extension;
* les contrôleurs réseau et de stockage.

L’UEFI repère ensuite les périphériques qui peuvent contenir un système d’exploitation. Il consulte l’ordre de démarrage pour déterminer lequel doit être utilisé. Si aucun périphérique valide n’est trouvé, un message comme **No boot device** peut être affiché.

À cette étape, le matériel essentiel fonctionne généralement correctement. Un problème qui apparaît ensuite est donc plus probablement lié à l’unité de stockage, à l’ordre de démarrage ou au système d’exploitation.

### 3.6. Ordre de démarrage&#x20;

L’ordre de démarrage indique à l’UEFI où chercher le système d’exploitation. Il peut, par exemple, vérifier **Windows Boot Manager**, un SSD, une clé USB ou le réseau. Le premier choix valide trouvé est utilisé pour poursuivre le démarrage.

* **Entrée de démarrage :** information enregistrée dans l’UEFI qui indique où se trouve le programme permettant de lancer un système d’exploitation. Par exemple, **Windows Boot Manager** permet de lancer Windows.
* **Menu de démarrage ponctuel :** menu qui permet de choisir un périphérique pour un seul démarrage, sans modifier l’ordre permanent. Il est particulièrement utile pour démarrer sur une clé USB afin d’installer un système. Selon le fabricant, on y accède généralement avec **F8, F11 ou F12**.
* **Démarrage réseau :** permet à l’ordinateur de recevoir les fichiers nécessaires au démarrage depuis un serveur du réseau. Cette méthode, souvent appelée **PXE**, est principalement utilisée pour installer ou démarrer plusieurs ordinateurs dans une organisation.

## 4. Maintenance préventive et dépannage

### 4.1. Maintenance préventive et corrective

Maintenance préventive : actions réalisées régulièrement pour réduire la probabilité d'une panne ou d'une baisse de performance.

Maintenance corrective : actions réalisées après l'apparition d'un problème afin de rétablir le fonctionnement.

Une bonne maintenance ne consiste pas à démonter constamment l'ordinateur. Elle consiste à surveiller, nettoyer au bon moment et intervenir seulement lorsque c'est utile.

### 4.2. Environnement optimal

#### 4.2.1. Température et humidité

Un ordinateur doit être utilisé dans un endroit propre, sec et bien ventilé. Une température située entre **18 et 27 °C** et un taux d’humidité entre **30 et 60 %** conviennent généralement à une salle de travail.&#x20;

Une chaleur excessive, une forte humidité ou une grande quantité de poussière peuvent réduire la durée de vie des composants.

#### 4.2.2. Poussière, fumée et liquides

La poussière peut bloquer les filtres et les ventilateurs, réduire la circulation de l’air et faire augmenter la température des composants.&#x20;

La fumée et la graisse rendent cette poussière plus difficile à nettoyer. Les liquides peuvent également provoquer un court-circuit.

&#x20;Il faut donc garder l’ordinateur loin du sol, des boissons ouvertes et des endroits poussiéreux ou enfumés.

#### 4.2.3. Circulation d'air&#x20;

Dans un ordinateur, l’air frais entre généralement par l’avant ou le bas du boîtier, tandis que l’air chaud sort par l’arrière ou le haut. Les ventilateurs doivent donc être installés dans le bon sens. Les câbles doivent également être bien rangés pour ne pas bloquer la circulation de l’air.

### 4.3. Maintenance préventive matérielle

La maintenance préventive permet de repérer et de corriger de petits problèmes avant qu’ils causent une panne. Elle comprend principalement l’inspection, le nettoyage et la surveillance de l’état des composants.

#### 4.3.1. Inspection visuelle

Il faut vérifier régulièrement :

* l’état des câbles, des connecteurs et des ports;
* les bruits inhabituels provenant des ventilateurs ou des disques durs;
* l’accumulation de poussière et l’état des filtres;
* le bon fonctionnement des ventilateurs;
* la température des principaux composants;
* la présence d’une odeur de brûlé, d’une décoloration ou d’un dommage visible.

#### 4.3.2. Nettoyage

Avant de nettoyer l’intérieur d’un ordinateur :

* travailler dans un endroit propre et prendre les précautions antistatiques;
* retirer les panneaux du boîtier et nettoyer les filtres;
* utiliser de l’air comprimé par courtes pressions;
* enlever la poussière des ventilateurs, des dissipateurs et des grilles;
* vérifier les câbles et les connexions avant de refermer le boîtier.

{% hint style="info" %}
**À éviter :** ne pas utiliser un aspirateur domestique directement sur les composants, car il peut produire de l’électricité statique. Il ne faut pas non plus souffler avec la bouche, car l’humidité peut atteindre les circuits.
{% endhint %}

#### 4.3.3. Pâte thermique

La pâte thermique améliore le transfert de chaleur entre le processeur et son refroidisseur. Il n’est pas nécessaire de la remplacer régulièrement. Elle doit surtout être remplacée lorsque le refroidisseur est retiré ou lorsqu’un problème de température est causé par un mauvais contact.

#### 4.3.4. État des unités de stockage

Les SSD et les disques durs peuvent fournir des informations sur leur état grâce à la technologie **SMART**. Ces informations peuvent signaler une température élevée, des erreurs ou une usure importante.&#x20;

{% hint style="info" %}
**SMART :** une fonction intégrée aux SSD et aux disques durs qui surveille leur état. Elle recueille des informations comme la température, les erreurs et le niveau d’usure afin d’aider à détecter certains signes de panne

Les informations SMART peuvent être consultées :

* dans l’UEFI de certains ordinateurs;
* avec un logiciel comme **CrystalDiskInfo** sous Windows;
* avec la commande **`smartctl`** sous Linux.
{% endhint %}

### 4.4. Procédure générale de dépannage

Le dépannage doit être logique, reproductible et sécuritaire. Changer plusieurs réglages au hasard peut masquer la cause et créer de nouveaux problèmes.

<figure><img src=".gitbook/assets/image (47).png" alt="" width="563"><figcaption><p>Procédure de dépannage</p></figcaption></figure>

• **Identifier le problème**:  Décrire précisément ce qui ne fonctionne pas, depuis quand et dans quelles conditions.

• **Recueillir les informations**: Noter les messages, les codes, les bips, les voyants, les journaux et les changements récents.

• **Reproduire le problème**: Déterminer s'il est constant ou intermittent et quelles actions le déclenchent.

• **Établir des causes probables**: Commencer par les causes simples et fréquentes qui correspondent aux indices.

• **Tester une seule hypothèse**: Faire une modification contrôlée, puis observer le résultat.

• **Appliquer la solution**: Utiliser une procédure officielle ou une intervention réversible lorsque possible.

• **Vérifier complètement**: Confirmer que le problème initial est résolu et que les fonctions associées sont normales.

• **Documenter**: Noter le symptôme, la cause, les tests, la solution, les pièces et les réglages modifiés.

### 4.5. Problèmes courants et solutions

#### 4.5.1. Problème 1 - Aucun signe d'alimentation

**Symptômes** : aucune DEL, aucun ventilateur et aucun affichage.

**Causes possibles** : prise sans courant, câble débranché, interrupteur du bloc sur arrêt, connecteur ATX ou EPS mal branché, bouton du boîtier mal connecté, alimentation défectueuse.

**Vérifications** : tester la prise avec un appareil approprié, vérifier le câble et l'interrupteur, inspecter ATX 24 broches, EPS CPU et le connecteur du bouton. Débrancher les périphériques non essentiels.

**Solutions possibles** : rebrancher correctement, corriger le connecteur du panneau avant ou tester avec une alimentation compatible connue comme fonctionnelle. Ne jamais ouvrir le bloc d'alimentation.

#### 4.5.2. Problème 2 - Les ventilateurs tournent, mais il n'y a pas d'image

**Symptômes** : la machine semble alimentée, mais l'écran reste noir.

**Causes possibles** : écran ou entrée vidéo incorrecte, câble défectueux, RAM mal installée, carte graphique mal installée, alimentation GPU absente, sortie vidéo non appropriée, échec du POST.

**Vérifications :** vérifier l'écran, la source sélectionnée et le câble; utiliser la sortie de la carte graphique si elle est installée; lire les DEL CPU/DRAM/VGA/BOOT; réinstaller la RAM et le GPU après avoir débranché la machine.

**Solutions possibles** : corriger la connexion, tester une seule barrette, tester un autre câble ou écran et démarrer en configuration minimale.

#### 4.5.3. Problème 3 - Échec après l'ajout de mémoire

**Symptômes** : pas de POST, redémarrages répétés, quantité de RAM incorrecte ou instabilité.

**Causes possibles** : module incompatible, mauvais emplacement, barrette incomplètement insérée, profils XMP/EXPO instables, modules mélangés

**Vérifications** : attendre le délai recommandé, vérifier le manuel et la liste de compatibilité, tester un module à la fois et charger les réglages mémoire par défaut.

**Solutions possibles** : réinstaller les barrettes, utiliser les emplacements recommandés, désactiver le profil de performance, mettre à jour l'UEFI si le fabricant corrige ce problème ou utiliser un ensemble compatible.

#### 4.5.4. Problème 4 - Surchauffe ou arrêt pendant une tâche lourde

**Symptômes** : ventilateurs très rapides, baisse de performance, température élevée, gel ou arrêt.

**Causes possibles** : poussière, ventilateur arrêté, refroidisseur mal monté, pâte thermique inadéquate, film protecteur oublié, circulation d'air insuffisante, température ambiante élevée.

**Vérifications** : surveiller les températures et les vitesses, inspecter les ventilateurs et les filtres, vérifier le montage du refroidisseur et les câbles.

**Solutions possibles** : nettoyer, corriger le flux d'air, rebrancher ou remplacer un ventilateur, remonter correctement le refroidisseur et remplacer la pâte si le refroidisseur a été retiré.

#### 4.5.5. Problème 5 - Ordinateur lent

**Symptômes** : démarrage long, applications lentes, disque très occupé, manque de mémoire ou ralentissements intermittents.

**Causes possibles** : trop de programmes au démarrage, stockage presque plein ou défaillant, RAM insuffisante, surchauffe, logiciel malveillant, mises à jour en cours, application très exigeante.

**Vérifications** : observer l'utilisation du processeur, de la mémoire, du disque et du réseau; vérifier l'espace libre, les températures, SMART, les programmes au démarrage et les analyses de sécurité.

**Solutions possibles** : corriger la cause mesurée : libérer de l'espace, retirer un programme inutile, traiter un logiciel malveillant, réparer le stockage, améliorer le refroidissement ou ajouter de la RAM si l'utilisation le justifie.

#### 4.5.6. Problème 6 - Unité de stockage non détectée

**Symptômes** : le SSD ou le disque n'apparaît pas dans l'UEFI ou le système.

**Causes possibles** : câble SATA ou alimentation absent, connecteur M.2 incompatible, unité mal installée, port désactivé.

**Vérifications** : vérifier d'abord si l'UEFI voit l'unité; inspecter les câbles; vérifier la gestion des disques dans le système.

**Solutions possibles** : rebrancher, utiliser un port compatible, initialiser et partitionner une unité neuve, installer un pilote de contrôleur si nécessaire ou remplacer une unité défectueuse après récupération des données si possible.

#### 4.5.7. Problème 7 - Message « No boot device »

**Symptômes** : le POST réussit, mais aucun système ne se charge.

**Causes possibles** : mauvais ordre de démarrage, unité absente, entrée UEFI perdue, mode UEFI/Legacy modifié, chargeur endommagé&#x20;

**Vérifications** : vérifier que l'unité est détectée, choisir l'entrée correcte comme Windows Boot Manager, vérifier le mode UEFI et consulter l'état SMART.

**Solutions possibles** : corriger l'ordre, rétablir le mode précédent, utiliser les outils de réparation du chargeur ou restaurer depuis une sauvegarde. Remplacer l'unité si elle est défaillante.

#### 4.5.8. Problème 8 - Redémarrages, gels ou écrans bleus

**Symptômes** : le système se bloque, redémarre ou affiche une erreur sous charge ou de façon aléatoire.

**Causes possibles** : RAM instable, surchauffe, pilote défectueux, alimentation insuffisante, stockage en erreur, surcadençage, logiciel ou périphérique récent.

**Vérifications** : noter le code exact et le contexte; consulter les journaux; revenir aux réglages par défaut; tester la mémoire, les températures, le stockage et l'alimentation.

**Solutions possibles** : corriger le pilote ou la mise à jour fautive, remplacer le composant confirmé, améliorer le refroidissement ou supprimer le réglage instable.

#### 4.5.9. Problème 9 - Périphérique USB non reconnu

**Symptômes** : aucune détection, déconnexions ou message d'erreur.

**Causes possibles :** port, câble ou périphérique défectueux, manque d'alimentation, pilote, connecteur USB interne mal branché, économie d'énergie.

**Vérifications** : tester un autre port et un autre câble, essayer le périphérique sur une autre machine, vérifier le Gestionnaire de périphériques et les connecteurs internes.

**Solutions possibles** : remplacer le câble, utiliser un concentrateur alimenté si approprié, réinstaller le pilote officiel ou réparer le connecteur.

#### 4.5.10. Problème 10 - L'heure se réinitialise

**Symptômes** : date et heure incorrectes après le débranchement, paramètres UEFI perdus.

**Causes possibles** : pile RTC faible ou réglage remis à zéro.

**Vérifications** : régler l'heure, débrancher selon la procédure, puis vérifier si le problème revient; consulter le manuel pour le type de pile.

**Solutions possibles** : remplacer la pile par le modèle approprié en respectant la polarité, puis reconfigurer l'UEFI.

#### 4.5.11. Problème 11 - Bruit anormal

**Symptômes** : cliquetis, frottement, vibration ou sifflement nouveau.

**Causes possibles** : câble dans un ventilateur, ventilateur usé, vis desserrée, vibration du boîtier, disque dur mécanique en panne.

**Vérifications** : localiser le bruit sans toucher les composants sous tension; vérifier les câbles et les fixations après l'arrêt; sauvegarder immédiatement si un disque mécanique émet des clics répétés.

**Solutions possibles** : dégager le câble, resserrer correctement, remplacer le ventilateur ou le disque confirmé. Ne pas continuer à solliciter un disque qui semble défaillant.

#### 4.5.12. Problème 12 - Nouveau composant non reconnu dans le système

**Symptômes** : le POST réussit, mais le composant n'apparaît pas ou ne fonctionne pas correctement.

**Causes possibles** : pilote absent, composant désactivé dans l'UEFI, carte mal installée, emplacement partagé ou incompatible, système trop ancien.

**Vérifications** : vérifier la détection dans l'UEFI et le gestionnaire de périphériques, consulter le manuel, confirmer les pilotes et les exigences du système.

**Solutions possibles** : réinstaller le composant, activer le contrôleur, installer le pilote officiel, utiliser un autre emplacement compatible ou mettre à jour selon la procédure.

### 4.6. Exemple d'analyse d'une panne

#### Cas : l'ordinateur ne donne plus d'image après un nettoyage

•     **Symptôme:** Les ventilateurs tournent, mais l'écran reste noir.

•    **Changement récent:** Le boîtier a été ouvert et nettoyé.

•     **Indices:** La DEL DRAM reste allumée.

•     **Hypothèse prioritaire:** Une barrette a été déplacée ou n'est plus complètement insérée.

•     **Test:** Éteindre, débrancher, réinstaller une seule barrette dans l'emplacement recommandé et relancer.

•     **Résultat:** Le POST réussit avec une barrette, puis avec les deux après leur réinstallation.

•     **Conclusion:** La connexion de la RAM était incomplète.

•     **Documentation:** Noter l'intervention et vérifier la quantité de RAM détectée dans l'UEFI et le système.

