---
description: Stockage, cartes d’extension, connecteurs et périphériques
hidden: true
---

# Chapitre 2 - Architecture d'un ordinateur moderne (Suite)

## Objectifs d'apprentissage&#x20;

* Distinguer un HDD, un SSD SATA et un SSD NVMe;
* Reconnaître les principales cartes d’extension;
* Identifier les connecteurs internes et externes courants;
* Différencier un connecteur USB-A d’un connecteur USB-C;
* Comprendre que deux ports USB-C identiques peuvent offrir des fonctions différentes;
* Classer les périphériques comme dispositifs d’entrée, de sortie ou mixtes;
* Vérifier si des composants peuvent fonctionner ensemble;
* Reconnaître un goulot d’étranglement;
* Manipuler les composants d’un ordinateur de manière sécuritaire;
* Transformer les besoins d’un client en une liste d’équipement.

## 1. Le stockage moderne&#x20;

### 1.1. À quoi sert le stockage ?&#x20;

Le stockage conserve les fichiers même lorsque l’ordinateur est éteint. On y trouve notamment :

* le système d’exploitation;
* les logiciels;
* les documents;
* les photos et vidéos;
* les fichiers de configuration.

{% hint style="info" %}
La mémoire vive, ou RAM, est différente : elle conserve temporairement les données utilisées par les programmes en cours d’exécution.

RAM = Esapce de travail temporaire

SSD ou HDD = rangement permanent
{% endhint %}

### 1.2. Le disque dur mécanique&#x20;

Un **HDD**, ou disque dur, contient des plateaux qui tournent et une tête qui lit ou écrit les données. Son fonctionnement ressemble un peu à celui d’un tourne-disque extrêmement précis.

#### 1.2.1. Formats courant&#x20;

* **3.5 pouces :** principalement dans les ordinateurs de bureau et les serveurs;
* **2.5 pouces** : anciens portables, petits ordinateurs et disques externes.

<figure><img src=".gitbook/assets/image (32).png" alt=""><figcaption><p>Les deux formats d'un HDD. Source : Seagate</p></figcaption></figure>

#### 1.2.2. Avantages&#x20;

* Prix faible par gigaoctet;
* Grandes capacités disponibles;
* Utile pour les archives, les vidéos et les sauvegardes.

#### 1.2.3. Inconvénients&#x20;

* Plus lent qu’un SSD;
* Produit du bruit et des vibrations;
* Plus fragile en cas de choc;
* Contient des pièces mécaniques qui s’usent.

#### 1.2.4. Connexion

Un HDD interne utilise généralement :&#x20;

* un câble **SATA de données** vers la carte mère;
* un connecteur **SATA d’alimentation** venant du bloc d’alimentation.

<figure><img src=".gitbook/assets/image (33).png" alt=""><figcaption><p>HDD connecté avec des câbles SATA. Source : <a href="https://www.aomei.fr/">https://www.aomei.fr/</a></p></figcaption></figure>

{% hint style="info" %}
Le HDD reste intéressant pour conserver beaucoup de données à faible coût, mais il est moins recommandé comme disque principal d’un ordinateur moderne.
{% endhint %}

### 1.3. Le SSD SATA

Un **SSD** conserve les données dans de la mémoire électronique. Il ne contient pas de plateau ni de pièce mécanique mobile.

Le SSD SATA de 2,5 pouces ressemble à un petit disque dur, mais il est beaucoup plus rapide.

<figure><img src=".gitbook/assets/image (34).png" alt="" width="375"><figcaption><p>Disque SSD</p></figcaption></figure>

#### 1.3.1. Avantages

* Démarrage de Windows plus rapide;
* Logiciels plus rapides à ouvrir;
* Silencieux;
* Résiste mieux aux chocs;
* Consomme peu d’énergie.

#### 1.3.2. Limites

* Plus cher qu’un HDD pour une même capacité;
* Moins rapide qu’un SSD NVMe récent.

#### 1.3.3. Connexion

Comme un HDD SATA, il nécessite :

* Un câble SATA de données;
* Un câble SATA d’alimentation;
* Un emplacement de 2,5 pouces ou un adaptateur.

L’interface SATA offre un maximum théorique de 6 Gbit/s. Dans la pratique, les SSD SATA rapides atteignent généralement environ **500 à 550 Mo/s**.

{% hint style="info" %}
Le SSD SATA constitue une excellente mise à niveau pour un ordinateur un peu ancien.
{% endhint %}

### 1.4. Le SSD NVMe

Un **SSD NVMe** utilise généralement l’interface PCI Express pour communiquer directement avec le processeur ou le chipset. Il offre une latence plus faible et une vitesse supérieure à celle du SATA. NVMe est un protocole conçu spécialement pour les SSD modernes.&#x20;

Le format le plus courant dans les ordinateurs personnels est le **M.2 2280** :

* 22 mm de largeur;
* 80 mm de longueur;
* Installé directement sur la carte mère;
* Fixé avec une petite vis ou un système sans outil.

Il n’a généralement pas besoin d’un câble SATA ni d’un câble d’alimentation séparé.

<figure><img src=".gitbook/assets/image (35).png" alt="" width="375"><figcaption><p>Installation d'un SSD M.2. Source : <a href="https://fr.ifixit.com/">https://fr.ifixit.com/</a></p></figcaption></figure>

{% hint style="info" %}
**Attention : M.2 ne signifie pas automatiquement NVMe**

**M.2 décrit principalement la forme du composant.** Un SSD M.2 peut utiliser :

* l’interface SATA;
* l’interface PCIe avec le protocole NVMe.

Il faut donc vérifier la documentation de la carte mère.
{% endhint %}

Un SSD NVMe peut utiliser PCIe 3.0, 4.0 ou 5.0. Un SSD récent peut parfois fonctionner dans un emplacement plus ancien, mais sa vitesse sera limitée par l’ancienne génération.

**Exemple** : un SSD PCIe 4.0 placé dans un emplacement PCIe 3.0 compatible fonctionnera généralement, mais à la vitesse du PCIe 3.0.

### 1.5. Comparaison des technologies&#x20;

<table data-search="false"><thead><tr><th>Caractéristique</th><th>HDD</th><th>SSD SATA</th><th>SSD NVMe</th></tr></thead><tbody><tr><td>Technologie</td><td>Mécanique</td><td>Mémoire électronique</td><td>Mémoire électronique</td></tr><tr><td>Vitesse</td><td>Faible</td><td>Bonne</td><td>Très bonne</td></tr><tr><td>Bruit</td><td>Oui</td><td>Non</td><td>Non</td></tr><tr><td>Résistance aux chocs</td><td>Faible</td><td>Bonne</td><td>Bonne</td></tr><tr><td>Connexion habituelle</td><td>SATA</td><td>SATA</td><td>M.2/PCIe</td></tr><tr><td>Câbles internes</td><td>Données + alimentation</td><td>Données + alimentation</td><td>Généralement aucun</td></tr><tr><td>Utilisation conseillée</td><td>Archives et sauvegardes</td><td>Mise à niveau d’un ancien PC</td><td>Système et applications modernes</td></tr></tbody></table>

## 2. Les cartes d'extensions

### 2.1. Définition

Une **carte d’extension** ajoute une fonction à un ordinateur. Elle est généralement installée dans un emplacement PCI Express de la carte mère.

#### Exemples

* Carte graphique;
* Carte réseau Ethernet;
* Carte Wi-Fi et Bluetooth;
* Carte de son;
* Carte d’acquisition vidéo;
* Carte ajoutant des ports USB;

### 2.2. Les emplacements PCI Express

Les emplacements PCIe peuvent avoir différentes tailles :

* PCIe x1;
* PCIe x4;
* PCIe x8;
* PCIe x16.

Le nombre indique le nombre de **voies de communication**, appelées _lanes_. Plus il y a de voies, plus la connexion peut transporter de données.

Une carte graphique utilise généralement un emplacement x16. Une petite carte réseau ou une carte de son utilise souvent un emplacement x1.

Les cartes et emplacements PCIe peuvent fonctionner avec différentes générations. La connexion s’adapte généralement à la génération et au nombre de voies disponibles les plus faibles

### 2.3. Ce qu'il faut vérifier avant l'installation d'un carte d'extension&#x20;

#### 2.3.1. Compatibilité physique

* La carte rentre-t-elle dans l’emplacement?
* Le boîtier est-il assez long et assez large?
* La carte occupe-t-elle un, deux ou trois emplacements?
* Faut-il une équerre pleine hauteur ou _low profile_?

#### 2.3.2. Compatibilité électrique

* Le bloc d’alimentation est-il assez puissant?
* La carte demande-t-elle un connecteur d’alimentation supplémentaire?
* Le bon connecteur est-il disponible?

#### 2.3.3. Compatibilité technique

* La carte mère possède-t-elle le bon emplacement PCIe?
* Combien de voies sont réellement disponibles?
* Le BIOS et le système d’exploitation reconnaissent-ils la carte?
* Un pilote doit-il être installé?

## 3. Les connecteurs modernes&#x20;

### 3.1. Connecteur et norme&#x20;

Un **connecteur** correspond à la forme physique de la prise. Une **norme** précise ce que cette prise peut faire.

Par exemple :

* USB-C désigne principalement une forme de connecteur;
* USB 10 Gbit/s indique une vitesse;
* Power Delivery indique une capacité de recharge;
* DisplayPort Alt Mode indique une capacité de transmettre une image par USB-C.

C’est pourquoi deux ports USB-C qui semblent identiques peuvent avoir des capacités différentes.

### 3.2. USB-A

USB-A est le connecteur rectangulaire classique.

<figure><img src=".gitbook/assets/image (36).png" alt="" width="375"><figcaption><p>Connecteur USB-A</p></figcaption></figure>

Il peut servir à connecter :

* Clavier;
* Souris;
* Imprimante;
* Clé USB;
* Disque externe;
* Webcam;
* Adaptateur réseau.

Un port USB-A peut fonctionner à différentes vitesses. La couleur du port peut donner un indice, mais elle ne constitue pas une preuve suffisante. Il faut consulter les symboles ou la fiche technique.

### 3.3. USB-C

USB-C est plus petit et réversible : il peut être inséré dans les deux sens.

<figure><img src=".gitbook/assets/image (37).png" alt=""><figcaption><p>Connecteur USB-C</p></figcaption></figure>

Selon l’appareil, le port et le câble, il peut transporter :

* Des données;
* De l’électricité;
* Une image;
* Du son;
* Une connexion réseau par l’intermédiaire d’une station d’accueil.

### 3.4. Comprendre USB 2.0, USB 3 et USB4

Le nom **USB** peut décrire deux éléments différents :

* le **connecteur physique** : USB-A, USB-B, Micro-USB ou USB-C;
* la **norme de communication** : USB 2.0, USB 3.0, USB 3.2 ou USB4.

Un connecteur USB-C n’est donc pas nécessairement plus rapide qu’un connecteur USB-A. Il faut vérifier la norme prise en charge.

#### 3.4.1. Les principales versions&#x20;

| Norme USB        | Autres noms possibles          | Vitesse maximale théorique | Connecteurs possibles            |
| ---------------- | ------------------------------ | -------------------------- | -------------------------------- |
| USB 2.0          | High-Speed USB                 | 480 Mbit/s                 | USB-A, USB-B, Micro-USB et USB-C |
| USB 3.0          | USB 3.1 Gen 1, USB 3.2 Gen 1   | 5 Gbit/s                   | USB-A ou USB-C                   |
| USB 3.1 Gen 2    | USB 3.2 Gen 2                  | 10 Gbit/s                  | USB-A ou USB-C                   |
| USB 3.2 Gen 2x2  | USB 20 Gbit/s                  | 20 Gbit/s                  | USB-C seulement                  |
| USB4             | USB 20 Gbit/s ou USB 40 Gbit/s | 20 ou 40 Gbit/s            | USB-C seulement                  |
| USB4 Version 2.0 | USB 80 Gbit/s                  | Jusqu’à 80 Gbit/s          | USB-C seulement                  |

{% hint style="info" %}
La vitesse réelle correspond toujours au composant le plus lent parmi :

* le port de l’ordinateur;
* le câble;
* la station d’accueil;
* le périphérique.
{% endhint %}

### 3.5. DisplayPort&#x20;

DisplayPort transporte une image numérique et du son. On le trouve principalement sur :

* Les ordinateurs;
* Les cartes graphiques;
* Les moniteurs;
* Les stations d’accueil.

<figure><img src=".gitbook/assets/image (38).png" alt="" width="375"><figcaption><p>Connecteur DisplayPort.</p></figcaption></figure>

Il est bien adapté aux écrans à haute résolution ou à haute fréquence de rafraîchissement.&#x20;

### 3.6. HDMI&#x20;

HDMI transporte également l’image et le son. On le trouve couramment sur :

* Les téléviseurs;
* Les moniteurs;
* Les projecteurs;
* Les consoles;
* Les ordinateurs portables;
* Les cartes graphiques.

<figure><img src=".gitbook/assets/image (39).png" alt="" width="250"><figcaption><p>Connecteur HDMI</p></figcaption></figure>

### 3.7. Les stations d'accueil

Une station d’accueil, ou _dock_, permet de connecter plusieurs périphériques à un ordinateur portable à l’aide d’un seul câble.

Elle peut ajouter :

* Des ports USB;
* Un ou plusieurs écrans;
* Un port Ethernet;
* Une sortie audio;
* Un lecteur de carte mémoire;
* La recharge du portable.

<figure><img src=".gitbook/assets/image (40).png" alt="" width="375"><figcaption><p>Station d'accueil</p></figcaption></figure>

### 3.8. Connecteurs anciens ou en voie de disparition

<table data-search="false"><thead><tr><th>Connecteur</th><th>Ancienne utilisation</th><th>Remplacement courant</th></tr></thead><tbody><tr><td>VGA</td><td>Image analogique</td><td>HDMI ou DisplayPort</td></tr><tr><td>DVI</td><td>Image numérique</td><td>HDMI ou DisplayPort</td></tr><tr><td>PS/2</td><td>Clavier et souris</td><td>USB</td></tr><tr><td>Série DB9</td><td>Modems et équipements industriels</td><td>USB-série ou réseau</td></tr><tr><td>Port parallèle</td><td>Anciennes imprimantes</td><td>USB ou réseau</td></tr><tr><td>FireWire</td><td>Caméras et disques externes</td><td>USB ou Thunderbolt</td></tr><tr><td>eSATA</td><td>Disques externes</td><td>USB</td></tr><tr><td>IDE/PATA</td><td>Anciens disques internes</td><td>SATA ou NVMe</td></tr><tr><td>Micro-USB</td><td>Téléphones et petits appareils</td><td>USB-C</td></tr></tbody></table>

## 4. Les périphériques d’entrée et de sortie

### 4.1. Périphériques d’entrée

Ils permettent d’envoyer de l’information vers l’ordinateur.

Exemples :

* Clavier;
* Souris;
* Microphone;
* Webcam;
* Numériseur;
* Lecteur de codes-barres;
* Manette de jeu;
* Lecteur biométrique.

### 4.2. Périphériques de sortie

Ils permettent à l’ordinateur de présenter de l’information.

Exemples :

* Écran;
* Projecteur;
* Imprimante;
* Haut-parleurs;
* Écouteurs.

### 4.3. Périphériques mixtes

Certains périphériques reçoivent et envoient des données.

Exemples :

* Écran tactile;
* Casque avec microphone;
* Imprimante multifonction;
* Disque externe;
* Clé USB;
* Carte réseau;
* Station d’accueil.

## 5. Compatibilité et goulots d’étranglement

### 5.1. La compatibilité

Deux composants sont compatibles lorsqu’ils peuvent être connectés et fonctionner correctement ensemble.

Pour vérifier une compatibilité, on peut suivre cette méthode :

1. Déterminer le besoin.
2. Vérifier la forme et les dimensions.
3. Vérifier le connecteur.
4. Vérifier l’interface ou le protocole.
5. Vérifier l’alimentation électrique.
6. Vérifier les performances.
7. Vérifier le système d’exploitation et les pilotes.
8. Vérifier les câbles et adaptateurs nécessaires.

### 5.2. Le goulot d’étranglement

Un **goulot d’étranglement** apparaît lorsqu’un composant plus lent limite les performances de l’ensemble. L’ordinateur travaille à la vitesse que permet son élément limitant.

Examples :&#x20;

* Un SSD USB 10 Gbit/s branché sur un port USB 5 Gbit/s;
* Un SSD PCIe 4.0 installé dans un emplacement PCIe 3.0;
* Un ordinateur puissant qui démarre sur un ancien HDD;
* Une carte graphique très rapide associée à un processeur trop faible;
* Un écran 4K à haute fréquence branché avec un câble trop ancien;
* Un portable demandant 100 W branché sur une station qui fournit seulement 45 W.

### 5.3. Compatible ne signifie pas toujours optimal

| Situation                                                                     | Résultat                                               |
| ----------------------------------------------------------------------------- | ------------------------------------------------------ |
| SSD PCIe 4.0 dans un emplacement PCIe 3.0 NVMe                                | Compatible, mais vitesse réduite                       |
| SSD M.2 SATA dans un emplacement NVMe seulement                               | Incompatible                                           |
| SSD USB 10 Gbit/s sur un port USB 5 Gbit/s                                    | Compatible, mais limité à 5 Gbit/s                     |
| Station vidéo sur un USB-C sans sortie vidéo                                  | Les ports USB peuvent fonctionner, mais pas les écrans |
| Carte graphique trop longue pour le boîtier                                   | Incompatible physiquement                              |
| Carte graphique demandant deux connecteurs sur un bloc qui n’en possède qu’un | Incompatible électriquement                            |

### 6. Manipulation sécuritaire des composants

Les composants d’un ordinateur sont fragiles et peuvent être endommagés par l’électricité statique, une mauvaise manipulation ou un branchement incorrect. Avant d’ouvrir un ordinateur, il faut donc prendre quelques précautions pour protéger le matériel et éviter les blessures.

#### 6.1. Avant la manipulation&#x20;

* Sauvegarder les données importantes.
* Éteindre et débrancher complètement l’ordinateur.
* Appuyer quelques secondes sur le bouton d’alimentation.
* Travailler sur une surface propre et sèche.
* Utiliser un bracelet antistatique lorsque possible.

#### 6.2. Pendant la manipulation&#x20;

* Manipuler les composants par leurs côtés en évitant de toucher les connecteurs et les contacts métalliques.
* Vérifier les encoches et ne jamais forcer un composant.
* Retirer les câbles par leur connecteur, et non par les fils.
* Ranger les vis et les outils pour éviter de les oublier dans le boîtier.

#### 6.3.  Consignes importantes&#x20;

* Ne jamais ouvrir un bloc d’alimentation.
* Après l’installation, vérifier les connexions, refermer le boîtier et tester le fonctionnement du composant.
