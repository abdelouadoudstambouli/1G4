---
hidden: true
---

# Chapitre 11 -Concepts de réseaux informatiques

## Objectifs d’apprentissage :&#x20;

* Expliquer ce qu’est un réseau et distinguer les rôles de client, de serveur et d’équipement intermédiaire.
* Reconnaître les équipements, choisir un support de transmission et vérifier une liaison câblée.
* Distinguer les réseaux LAN, WLAN, MAN et WAN à partir de situations concrètes.
* Situer les adresses, les protocoles et les ports dans les modèles OSI et TCP/IP.
* Expliquer le rôle des services réseau et des mécanismes de protection.
* Comparer les moyens d’accès à Internet et effectuer des vérifications simples sous Windows et Linux.
* Expliquer le fonctionnement et les usages des principales technologies sans fil.

## Les concepts de base&#x20;

### Les appareils et les liaisons

Un réseau informatique relie des appareils pour leur permettre d’échanger des données et de partager des ressources. Ces ressources peuvent être des fichiers, une imprimante, une application ou une connexion Internet.

Les équipements terminaux, aussi appelés hôtes, sont à l’origine ou à la destination des échanges. On y trouve les ordinateurs, serveurs, téléphones, tablettes, imprimantes, caméras et téléphones IP. Les équipements intermédiaires, comme les commutateurs et les routeurs, assurent le passage des données. Le support de transmission est le moyen utilisé pour transporter le signal, par exemple un câble de cuivre, une fibre optique ou des ondes radio.

Un réseau local peut fonctionner sans accès à Internet. Dans une salle de cours, deux postes peuvent continuer à échanger un fichier même si la connexion du fournisseur est coupée.

### Les rôles de client et de serveur

Un client demande un service. Un serveur reçoit la demande et fournit une réponse. Lorsque vous ouvrez une page, le navigateur joue le rôle de client et le logiciel qui héberge le site joue le rôle de serveur web.

Ces mots désignent des rôles. Une machine Ubuntu peut héberger un site pour les autres postes, puis agir comme cliente lorsqu’elle télécharge ses mises à jour. Un serveur peut être installé sur une machine physique, dans une machine virtuelle ou chez un fournisseur infonuagique.

Dans une organisation client-serveur, certains services sont centralisés sur des serveurs. Cela facilite la gestion des comptes, des autorisations et des sauvegardes. Dans une organisation pair à pair, les postes peuvent partager directement des ressources entre eux. Cette approche convient à de petits besoins, mais devient plus difficile à administrer lorsque le nombre de postes augmente.

<figure><img src=".gitbook/assets/image (159).png" alt="" width="563"><figcaption><p>Modèle client-serveur. Source : Calimo, d’après des icônes de David Vignoni, Wikimedia Commons (2011).</p></figcaption></figure>

### Lire les icônes d’un schéma

Les icônes permettent de reconnaître les fonctions des équipements. Un rectangle avec plusieurs prises ou flèches représente souvent un commutateur. Un cercle avec des flèches représente souvent un routeur. Un symbole avec des antennes évoque un point d’accès. Un nuage représente un réseau dont les détails ne sont pas dessinés, souvent Internet ou le réseau d’un fournisseur.

Les traits représentent les liaisons. Selon la légende, un trait plein peut désigner un câble et un trait ondulé ou pointillé une liaison sans fil. Les conventions varient selon les logiciels. La légende du schéma reste donc nécessaire.

<figure><img src=".gitbook/assets/image (160).png" alt="" width="482"><figcaption><p>Icônes d'un schéma réseau.</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (161).png" alt=""><figcaption><p>Exemple de réseau de laboratoire. Les postes et l’imprimante communiquent sur le réseau local. Le routeur permet de rejoindre les autres réseaux.</p></figcaption></figure>

### Quelques mesures utiles

Le **débit** correspond à une quantité de données transmise par seconde. Il s’exprime souvent en kbit/s, Mbit/s ou Gbit/s. Un débit de 1 Gbit/s correspond à 1 000 Mbit/s. Le débit descendant concerne les données reçues, tandis que le débit montant concerne les données envoyées.

Un **octet** contient 8 bits. Un fichier de 500 Mo représente donc environ 4 000 mégabits. À 100 Mbit/s réellement disponibles, son transfert demanderait au minimum 40 secondes. Les échanges de contrôle, les autres utilisateurs et la vitesse du serveur peuvent allonger cette durée.

La **latence** est un délai de transmission. Le temps d’un aller-retour est souvent mesuré en millisecondes. La gigue est la variation de ce délai. Les pertes correspondent aux données qui n’arrivent pas à destination. Une visioconférence peut être mauvaise malgré un débit élevé si le délai varie fortement ou si trop de données se perdent.

En réseau, le mot **bande passante** est souvent employé pour parler de capacité de transmission. Dans une fiche de câble ou de radio, une valeur en MHz décrit une plage ou une caractéristique fréquentielle. Il faut lire l’unité avant de comparer deux chiffres.

## Les équipements réseau et le câblage

Les équipements n’ont pas tous le même rôle. Certains raccordent les appareils à un réseau local, d’autres permettent de rejoindre un autre réseau. Le câblage et les connecteurs doivent être adaptés aux distances et aux débits recherchés.

### La carte réseau

La carte réseau, ou NIC pour Network Interface Card, permet à une machine d’émettre et de recevoir des données. Elle peut être intégrée à la carte mère, ajoutée dans un port d’extension ou branchée en USB. Il existe des interfaces Ethernet filaires et des interfaces sans fil.

Une machine peut posséder plusieurs interfaces. Un portable peut, par exemple, utiliser une carte Wi-Fi et un adaptateur Ethernet USB. Dans une machine virtuelle, le système voit une carte réseau virtuelle reliée à un réseau fourni par l’hyperviseur.

<figure><img src=".gitbook/assets/image (162).png" alt="" width="563"><figcaption><p>Carte Ethernet, carte sans fil et adaptateur réseau USB</p></figcaption></figure>

### Le pont et le commutateur

Un pont, ou bridge, relie des segments de réseau local. Il observe les adresses des interfaces pour décider de transmettre ou de filtrer une trame. Une trame est l’unité de données échangée sur une liaison, par exemple Ethernet. Une adresse MAC identifie une interface sur cette liaison.

Le commutateur, ou switch, applique ce principe sur plusieurs ports. Il apprend les adresses MAC sources des trames reçues et associe ces adresses aux ports d’entrée. Lorsque la destination est connue, il transmet la trame sur le port approprié. Pour une destination inconnue ou certaines diffusions, il peut transmettre sur plusieurs ports du même réseau logique.

<figure><img src=".gitbook/assets/image (163).png" alt="" width="563"><figcaption><p>Commutateur réseau Ethernet à 8 ports</p></figcaption></figure>

Un commutateur non administrable offre surtout un raccordement immédiat. Un commutateur administrable permet de configurer des fonctions comme les VLAN, la surveillance des ports ou certaines règles d’accès. Le choix dépend du besoin de gestion, même dans une petite entreprise.

### &#x20;Le routeur

Le routeur relie des réseaux IP différents. Il consulte l’adresse IP de destination et sa table de routage pour choisir la prochaine étape du trajet. Une adresse IP sert à identifier une interface dans un réseau IP et à acheminer les données entre réseaux.

Dans une petite installation, le routeur relie le réseau local au fournisseur Internet. Le poste l’utilise comme passerelle par défaut pour les destinations auxquelles aucune route plus précise ne correspond. Dans une grande organisation, plusieurs routeurs relient les sites et les sous-réseaux.

<figure><img src=".gitbook/assets/image (164).png" alt="" width="563"><figcaption></figcaption></figure>

Un boîtier résidentiel peut regrouper routeur, commutateur, point d’accès Wi-Fi, pare-feu et serveur DHCP. Il faut distinguer les fonctions, même lorsqu’elles sont réunies dans un seul appareil.

### &#x20;Le modem et le terminal optique

Le modem adapte les signaux à la technologie d’accès du fournisseur, par exemple le câble coaxial ou la ligne téléphonique DSL. Sur une connexion par fibre, un terminal optique, souvent appelé ONT, termine la liaison optique et présente une connexion utilisable par le réseau du client.

Selon l’installation, le modem ou l’ONT est séparé du routeur ou intégré au même boîtier. Le modem concerne la liaison d’accès. Le routeur organise le passage entre les réseaux.

### Le point d’accès sans fil

Le point d’accès, ou AP pour Access Point, permet aux appareils Wi-Fi de rejoindre le réseau local. Son propre raccordement au réseau est souvent filaire. Il peut aussi être relié par radio dans une installation maillée.

La couverture dépend de son emplacement, des murs, des interférences et des appareils clients. Plusieurs points d’accès peuvent être nécessaires dans un bâtiment. Leur présence permet d’étendre la couverture, mais leur positionnement et leurs canaux doivent être planifiés.

<figure><img src=".gitbook/assets/image (165).png" alt="" width="563"><figcaption><p>Point d’accès sans fil (Wi-Fi). Source : Zyxel, Wikimedia Commons, licence CC BY-SA 4.0</p></figcaption></figure>

### Le répéteur et le concentrateur

Un répéteur reçoit un signal affaibli et le régénère pour prolonger une liaison dans les limites de la technologie utilisée. Il ne choisit pas la destination à partir d’une adresse.

Un concentrateur, ou hub, est un répéteur à plusieurs ports. Il reproduit le signal reçu vers les autres ports. Les appareils partagent le même domaine de collision et la capacité du support. Les hubs Ethernet sont surtout utiles pour comprendre les anciens réseaux. Dans les installations actuelles, les commutateurs remplissent généralement la fonction de raccordement des postes.

### Le panneau de brassage

Le panneau de brassage, aussi appelé tableau de connexions ou patch panel, rassemble les câbles provenant des prises murales. Les conducteurs du câblage permanent sont terminés à l’arrière. Des cordons courts relient les prises avant aux ports du commutateur.

Le panneau facilite le repérage, les déplacements et le remplacement des connexions. Il est passif. C’est le commutateur qui traite et transmet les trames. Chaque prise murale et chaque position du panneau devraient porter une identification cohérente. Des liaisons peuvent aussi passer entre les panneaux de deux armoires de câblage.

Un trajet courant part du poste, passe par un cordon, une prise murale, un câble permanent, le panneau de brassage, puis un second cordon jusqu’au commutateur.

<figure><img src=".gitbook/assets/image (166).png" alt="" width="563"><figcaption><p>Panneau de brassage Ethernet (Patch Panel). Source : Robert Harker, Wikimedia Commons, CC BY-SA 3.0.</p></figcaption></figure>

### Les supports de transmission

Le cuivre transporte des signaux électriques. La fibre optique transporte des signaux lumineux. Une liaison sans fil utilise des ondes radio. Le choix dépend de la distance, du débit, des perturbations, du coût et des équipements à raccorder.

#### Les paires torsadées

Un câble Ethernet en cuivre courant contient quatre paires de fils, soit huit conducteurs. Chaque paire comporte un fil de couleur et un fil blanc marqué de cette couleur. Les quatre couleurs sont orange, vert, bleu et brun.

Les torsades réduisent les effets des perturbations et les interactions entre paires, appelées diaphonie. Il faut les conserver le plus près possible de la terminaison lors du raccordement.

Le câble UTP n’a pas de blindage. Le câble STP désigne couramment une construction blindée. Les fiches détaillées peuvent employer des désignations plus précises, comme U/UTP ou F/UTP, qui décrivent le blindage général et celui des paires.

<figure><img src=".gitbook/assets/image (167).png" alt=""><figcaption><p>Câble réseau à quatre paires torsadées (Cat 6). Source : Agott, Wikimedia Commons, CC BY-SA 3.0.</p></figcaption></figure>

Les perturbations électromagnétiques sont souvent désignées par EMI. Les perturbations radioélectriques sont désignées par RFI. Un blindage correctement installé aide à les limiter. Il impose des connecteurs adaptés et le respect des exigences de liaison à la terre. Le blindage et ses accessoires peuvent augmenter le coût et rendre la pose plus exigeante. Le blindage seul ne garantit pas une bonne installation.

#### Le câble coaxial

Le câble coaxial possède un conducteur central, un isolant, un blindage métallique et une gaine extérieure. Selon le produit, les conducteurs et blindages peuvent employer du cuivre, de l’aluminium ou des structures composites.

On le rencontre dans la télévision, la réception satellite et l’accès Internet par câble. Les anciens réseaux Ethernet utilisaient aussi du coaxial. Le connecteur de type F est courant en télévision et sur les modems câble. Les connecteurs BNC et N sont utilisés dans d’autres installations, notamment vidéo ou radio. Leur choix dépend du câble, de l’impédance et de l’application. Dans un réseau de postes, le coaxial demande une connectique et des méthodes de pose différentes de celles des paires torsadées. Le coût et la difficulté du dépannage dépendent de l’installation.

<figure><img src=".gitbook/assets/image (168).png" alt="" width="563"><figcaption><p>Câble coaxial utilisé pour la transmission de données. Source : Raysonho, Wikimedia Commons, CC0 1.0.</p></figcaption></figure>

#### La fibre optique

Une fibre comporte un cœur, une enveloppe optique, un revêtement protecteur parfois appelé tampon, puis les protections et la gaine du câble. La lumière se propage dans le cœur. Le câble peut également contenir des éléments de renforcement pour résister aux contraintes mécaniques.

La fibre résiste aux perturbations électromagnétiques et permet de fortes capacités sur des distances importantes. Elle convient aux liaisons entre bâtiments, aux réseaux de fournisseurs et aux centres de données. Elle est fréquente dans les liaisons principales d’un réseau, aussi appelées réseau fédérateur ou backbone. Son installation exige des outils adaptés, le respect du rayon de courbure et une grande propreté des connecteurs.

La fibre monomode, ou SMF, possède un cœur plus petit et convient notamment aux longues distances. La fibre multimode, ou MMF, possède un cœur plus large et est courante sur des liaisons plus courtes, par exemple dans un bâtiment ou un centre de données. La portée exacte dépend du type de fibre, du débit, de la longueur d’onde et des modules optiques.

<figure><img src=".gitbook/assets/image (169).png" alt="" width="563"><figcaption><p>Câble fibre optique. </p></figcaption></figure>

#### Le PoE et le CPL

Le PoE, Power over Ethernet, transporte l’alimentation électrique et les données sur un câble Ethernet compatible. Un commutateur PoE ou un injecteur peut alimenter un point d’accès, une caméra ou un téléphone IP. Il faut vérifier la norme prise en charge et la puissance disponible par port ainsi que le budget total du commutateur.

<figure><img src=".gitbook/assets/image (170).png" alt="" width="563"><figcaption><p>Injecteur PoE (Power over Ethernet). Source : Deavmi, Wikimedia Commons, CC BY-SA 4.0.</p></figcaption></figure>

Le CPL permet de transmettre des données informatiques par les câbles électriques d’un bâtiment. Généralement utilisés par deux, les adaptateurs CPL permettent d’étendre un réseau local sans installer de nouveaux câbles Ethernet entre les pièces.

<figure><img src=".gitbook/assets/image (171).png" alt="" width="563"><figcaption><p>Adaptateur CPL (courant porteur en ligne). Source : Boltasu, Wikimedia Commons, CC BY-SA 4.0.</p></figcaption></figure>

### Le raccordement et le test des câbles Ethernet

La qualité d’une liaison dépend autant des terminaisons que du câble. Un cordon mal préparé peut provoquer des coupures ou limiter le débit.

#### Les connecteurs et les outils

La fiche Ethernet à huit contacts est couramment appelée RJ45. Le terme technique 8P8C décrit ses huit positions et ses huit contacts. Les fiches doivent être compatibles avec la catégorie du câble, son blindage, son diamètre et ses conducteurs monobrins ou multibrins.

Le coupe-câble donne une coupe propre. La pince à dénuder retire la gaine extérieure sans blesser les fils. La pince à sertir fixe les contacts et le maintien mécanique d’une fiche compatible. L’outil d’insertion, ou punch-down, sert à terminer les conducteurs dans les contacts des prises et des panneaux de brassage.

Sur une prise à contacts autodénudants, l’outil enfonce le conducteur isolé dans le contact prévu. Il faut suivre le code de couleur de la prise et les instructions du fabricant.

#### Les conventions T568A et T568B

Les conventions T568A et T568B indiquent la disposition des paires sur les huit broches. Elles ont des performances équivalentes lorsqu’elles sont correctement appliquées. Seules les positions des paires verte et orange changent.

| Broche | T568A           | T568B           |
| ------ | --------------- | --------------- |
| 1      | Blanc et vert   | Blanc et orange |
| 2      | Vert            | Orange          |
| 3      | Blanc et orange | Blanc et vert   |
| 4      | Bleu            | Bleu            |
| 5      | Blanc et bleu   | Blanc et bleu   |
| 6      | Orange          | Vert            |
| 7      | Blanc et brun   | Blanc et brun   |
| 8      | Brun            | Brun            |

Pour lire une fiche mâle, placez les contacts dorés face à vous, la languette derrière et le câble vers le bas. Les broches se lisent de 1 à 8, de gauche à droite. Sur une prise murale, suivez le repérage imprimé par le fabricant, car la disposition des contacts arrière peut être différente.

Un câble droit emploie la même convention aux deux extrémités, A-A ou B-B. La broche 1 rejoint la broche 1, puis 2 rejoint 2, jusqu’à 8. Il sert couramment à relier un poste à un commutateur.

Un câblage A-B croise les paires utilisées par les anciens liens Ethernet à 10 ou 100 Mbit/s. De nombreux équipements actuels disposent de l’auto-MDI/MDIX et adaptent automatiquement les paires. Pour les exercices de fabrication, respectez la convention demandée et réalisez un câble droit.

<figure><img src=".gitbook/assets/image (172).png" alt="" width="563"><figcaption><p>Comparaison des conventions de câblage Ethernet T568A et T568B. Source : charner1963, Wikimedia Commons, CC0 1.0.</p></figcaption></figure>

#### Les étapes de fabrication

1\. Mesurer la longueur nécessaire et couper le câble proprement.

2\. Retirer seulement la longueur de gaine nécessaire, sans entailler les conducteurs.

3\. Préparer les paires. Retirer le fil de déchirement ou une partie du séparateur si le connecteur l’exige. Limiter le détorsadage.

4\. Placer les fils dans l’ordre T568A ou T568B et couper les extrémités à la longueur prévue pour la fiche.

5\. Insérer les conducteurs dans la fiche compatible. Vérifier visuellement leur ordre et leur position jusqu’aux contacts.

6\. Vérifier que la gaine entre dans la zone de maintien mécanique du connecteur.

7\. Sertir avec l’outil adapté, puis préparer la seconde extrémité selon la même convention.

8\. Tester le câble, repérer les défauts et identifier le cordon avant utilisation.

Pour le câblage permanent d’un bâtiment, on termine généralement les câbles sur des prises et des panneaux de brassage. Les cordons sont souvent achetés déjà fabriqués et testés.

#### Les outils de test

| Outil                           | Ce qu’il permet de vérifier                                                   | Limite à connaître                                                                                             |
| ------------------------------- | ----------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| Testeur de câble simple         | Continuité, ordre des fils, coupure ou court-circuit selon le modèle.         | Un test de continuité ne certifie pas le débit maximal. Certains modèles ne détectent pas les paires séparées. |
| Certificateur de câblage        | Conformité aux performances d’une catégorie et aux limites de mesure prévues. | L’appareil, les adaptateurs et le profil de test doivent correspondre à la liaison.                            |
| Générateur de tonalité et sonde | Repérage d’un câble ou d’une prise dans un faisceau.                          | Utiliser un modèle adapté aux circuits concernés et respecter les consignes pour les liens actifs.             |
| Multimètre                      | Tension, résistance ou continuité électrique selon le mode.                   | Il ne mesure pas à lui seul les performances Ethernet.                                                         |
| Adaptateur de bouclage          | Retour local d’un signal pour certaines fonctions de diagnostic.              | Le test dépend du port, du matériel et du logiciel utilisés.                                                   |

## Les types de réseaux

Les noms LAN, MAN et WAN indiquent surtout l’étendue et le contexte d’utilisation d’un réseau. Le nom WLAN précise qu’un réseau local utilise des liaisons sans fil. Ces catégories ne fixent pas, à elles seules, un débit ou une distance maximale.&#x20;

### Le LAN ou réseau local

LAN signifie Local Area Network, c’est-à-dire réseau local. Il relie des appareils dans un espace limité, comme un logement, une salle de cours, un bureau ou un bâtiment. Une même organisation en assure généralement la gestion.

<figure><img src=".gitbook/assets/image (173).png" alt="" width="563"><figcaption><p>Schéma d’un réseau local (LAN) connecté à Internet. Source : Bruno Voisin, Wikimedia Commons, CC BY-SA 3.0.</p></figcaption></figure>

Dans le laboratoire, les postes Windows et Linux, le serveur et l’imprimante peuvent appartenir au LAN du cégep. Les postes se raccordent souvent à des commutateurs par des câbles Ethernet. Des appareils sans fil peuvent aussi rejoindre ce réseau par des points d’accès.

Le LAN permet de partager des fichiers, d’utiliser une imprimante ou de consulter une application interne. Ces échanges peuvent rester locaux. Une coupure de la connexion Internet n’empêche donc pas nécessairement l’impression ou le partage de fichiers entre les appareils du LAN.

Exemple. Un poste Windows envoie un document à une imprimante située dans la même salle et sur le même sous-réseau. Le document circule dans le réseau local.

### Le WLAN ou réseau local sans fil

WLAN signifie Wireless Local Area Network, c’est-à-dire réseau local sans fil. Il assure la connexion locale d’appareils par ondes radio. Le Wi-Fi est la technologie habituellement utilisée pour ce type de réseau.

Dans une salle de cours, les portables et les tablettes se connectent à un point d’accès Wi-Fi. Ce point d’accès est généralement relié au reste du réseau par un câble. Le WLAN et les connexions Ethernet peuvent ainsi donner accès aux mêmes services, selon la configuration et les autorisations.

Le WLAN facilite les déplacements et le raccordement d’appareils sans prise réseau. Sa qualité dépend toutefois de la couverture, des interférences et du nombre d’utilisateurs. Le fonctionnement radio et les normes Wi-Fi sont étudiés dans la dernière partie du cours.

Exemple. Un portable connecté au Wi-Fi du cégep imprime sur une imprimante reliée par Ethernet. La première liaison est sans fil, mais une partie du trajet est câblée. Le symbole Wi-Fi sur le portable confirme une connexion locale; il ne garantit pas que l’accès Internet fonctionne.

### Le MAN ou réseau métropolitain

MAN signifie Metropolitan Area Network, c’est-à-dire réseau métropolitain. Il relie plusieurs réseaux locaux à l’échelle d’une ville ou d’une agglomération.

Une municipalité peut, par exemple, relier l’hôtel de ville, plusieurs bibliothèques et des centres de services par un réseau métropolitain. Chaque bâtiment possède son propre réseau local. Les liaisons entre les bâtiments permettent de partager des services à l’échelle de la ville.

Le MAN peut être exploité par une organisation ou fourni par un opérateur. La fibre optique convient à de nombreuses liaisons de ce type. On ne détermine pas qu’un réseau est un MAN à partir d’un nombre fixe de kilomètres; on examine surtout l’échelle et l’usage du réseau.

Exemple. Des bibliothèques réparties dans Gatineau accèdent à un système de gestion commun par des liaisons métropolitaines.

### Le WAN ou réseau étendu

WAN signifie Wide Area Network, c’est-à-dire réseau étendu. Il relie des réseaux ou des sites sur une vaste zone, par exemple plusieurs villes, provinces ou pays.

Une entreprise qui possède un bureau à Gatineau et un autre à Montréal peut utiliser un WAN pour permettre aux deux sites d’accéder à des services communs. Chaque bureau conserve son LAN. Des routeurs et des services de télécommunication assurent les échanges entre les sites.

Un WAN peut utiliser des liaisons privées fournies par un opérateur ou s’appuyer sur Internet avec une connexion protégée, par exemple un VPN. Sa capacité, son délai et son coût dépendent des services et des distances concernés. WAN ne signifie donc pas automatiquement « réseau lent ».

<figure><img src=".gitbook/assets/image (174).png" alt="" width="563"><figcaption><p>Réseau étendu WAN (Wide Area Network). Source : Haider.ali54148, Wikimedia Commons, CC0 1.0.</p></figcaption></figure>

Exemple. Une employée de Gatineau ouvre un dossier hébergé sur un serveur du bureau de Montréal. La communication traverse le réseau local de départ, la liaison entre les sites, puis le réseau local d’arrivée.

Internet est une interconnexion mondiale de réseaux. Il permet de joindre des destinations à grande distance, mais tous les WAN ne donnent pas un accès public à leurs ressources.

### Le PAN et le WWAN

Un PAN, Personal Area Network, est un réseau personnel autour d’une personne. Un téléphone relié à des écouteurs Bluetooth en est un exemple. Il répond à un besoin de proximité.

Un WWAN, Wireless Wide Area Network, est un réseau étendu utilisant des liaisons sans fil. Le réseau cellulaire d’un opérateur en est un exemple courant. Un téléphone peut utiliser ce réseau en 4G ou en 5G pour communiquer lorsqu’il se trouve hors d’un réseau Wi-Fi.

Il faut distinguer WLAN et WWAN. Un portable connecté au Wi-Fi d’un téléphone utilise un WLAN pour cette liaison. Le téléphone peut ensuite utiliser le WWAN de son opérateur pour rejoindre Internet.

### Comparer les types de réseaux

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td>Type</td><td>Ce que le terme décrit</td><td>Exemple</td></tr><tr><td>LAN</td><td>Un réseau local dans un espace limité.</td><td>Postes, serveur et imprimante d’un bureau.</td></tr><tr><td>WLAN</td><td>Un réseau local dont l’accès utilise des liaisons sans fil.</td><td>Portables connectés au Wi-Fi du cégep.</td></tr><tr><td>MAN</td><td>Des réseaux reliés à l’échelle d’une ville.</td><td>Bibliothèques municipales interconnectées.</td></tr><tr><td>WAN</td><td>Des réseaux reliés sur une vaste zone.</td><td>Sites de Gatineau et de Montréal reliés.</td></tr><tr><td>PAN</td><td>Des appareils reliés autour d’une personne.</td><td>Téléphone et écouteurs Bluetooth.</td></tr><tr><td>WWAN</td><td>Un réseau étendu utilisant un accès radio.</td><td>Téléphone connecté au réseau cellulaire.</td></tr></tbody></table>

Dans un cégep, les ordinateurs câblés et les appareils Wi-Fi peuvent faire partie de l’infrastructure locale. Une liaison vers un campus d’une autre ville relève du WAN. Pour décrire correctement une situation, il faut préciser quelle partie de la communication on observe

## Les modèles de référence et les protocoles

Les types de réseaux décrivent le contexte de la communication. Les modèles permettent maintenant de comprendre les fonctions nécessaires pour que les appareils échangent des données.

### Les services les protocoles et les normes

Un service est une fonction offerte à l’utilisateur ou à un autre système, comme afficher une page ou distribuer une configuration réseau. Un protocole définit les règles de l’échange. Une norme précise des caractéristiques communes permettant à des produits différents de fonctionner ensemble.

Par exemple, un serveur offre un service web. Le navigateur lui adresse des demandes au moyen du protocole HTTP. Les informations sont transportées sur un réseau qui peut employer la norme Ethernet IEEE 802.3 ou les normes sans fil IEEE 802.11.

L’IEEE publie notamment des normes pour Ethernet et les réseaux sans fil. L’IETF développe des protocoles Internet décrits dans des documents appelés RFC. L’ISO et l’UIT-T ont participé à la normalisation du modèle OSI. La TIA publie notamment des normes de câblage. Les organisations et les documents ont donc des rôles complémentaires.

### Le modèle OSI

Le modèle OSI, Open Systems Interconnection, répartit les fonctions réseau en sept couches. Il aide à expliquer une communication et à organiser le dépannage. Les couches 1 à 3 concernent surtout le support, le réseau local et le passage entre réseaux. La couche 4 concerne le transport entre applications. Les couches supérieures décrivent le dialogue et le traitement des données.

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td>Couche OSI</td><td>Fonction principale</td><td>Exemple ou repère</td></tr><tr><td>7 Application</td><td>Fournir les fonctions réseau utilisées par les applications.</td><td>HTTP, DNS et SMTP.</td></tr><tr><td>6 Présentation</td><td>Représenter ou transformer les données.</td><td>Encodage, format, compression et fonctions de chiffrement.</td></tr><tr><td>5 Session</td><td>Organiser et maintenir un dialogue.</td><td>Ouverture, suivi ou reprise d’une session de communication.</td></tr><tr><td>4 Transport</td><td>Acheminer les données entre processus.</td><td>TCP, UDP et numéros de port.</td></tr><tr><td>3 Réseau</td><td>Acheminer les paquets entre réseaux.</td><td>IP, adresses IP et routage.</td></tr><tr><td>2 Liaison de données</td><td>Transmettre des trames sur la liaison locale.</td><td>Ethernet, adresses MAC et commutation.</td></tr><tr><td>1 Physique</td><td>Transmettre les bits sous forme de signaux.</td><td>Câble, fibre, radio et connecteurs.</td></tr></tbody></table>

Il s’agit d’un modèle de fonctions. Une application réelle peut remplir plusieurs de ces fonctions, et certains protocoles ne se placent pas parfaitement dans une seule case. Un routeur domestique peut aussi réunir plusieurs fonctions matérielles et logicielles.&#x20;

### Le modèle TCP IP

Le modèle TCP/IP décrit l’architecture courante des communications Internet. Dans sa présentation en quatre couches, l’application regroupe approximativement les couches 5 à 7 d’OSI. Le transport correspond à la couche 4. La couche Internet correspond à la couche 3. L’accès réseau, aussi appelé liaison, regroupe les couches 1 et 2.

<figure><img src=".gitbook/assets/image (176).png" alt="" width="563"><figcaption><p>Comparaison des modèles TCP/IP (4 couches) et OSI (7 couches). Source : tomsgued, Wikimedia Commons, CC BY-SA 3.0.</p></figcaption></figure>

Certains manuels présentent un modèle Internet en cinq couches en séparant liaison et physique. La différence vient du découpage utilisé pour expliquer les fonctions. Dans ces notes, nous retenons les quatre couches TCP/IP.&#x20;

### L’encapsulation

Lorsqu’un navigateur envoie une requête HTTP sur TCP, les données de l’application sont placées dans un segment TCP. Le segment est placé dans un paquet IP. Le paquet est ensuite placé dans une trame Ethernet ou Wi-Fi, puis transmis sous forme de signaux.

Chaque couche ajoute les informations nécessaires à son travail. TCP ajoute notamment des numéros de port. IP ajoute des adresses IP. Ethernet ajoute notamment les adresses MAC du prochain trajet local. À l’arrivée, la machine traite ces informations en sens inverse. C’est la désencapsulation.

Pour UDP, on parle généralement de datagramme UDP. Le mot paquet est aussi employé de manière générale dans les conversations, mais il faut reconnaître le niveau observé lorsqu’on analyse un échange.

## L’acheminement des données dans un réseau

Lorsqu’un poste envoie un document à une imprimante ou consulte un serveur, les données peuvent traverser plusieurs équipements. Le trajet dépend d’abord d’une question : la destination se trouve-t-elle dans le même réseau local ou dans un autre réseau?

### Le rôle du commutateur

Un commutateur (_switch_) relie des appareils à l’intérieur d’un réseau local. Il peut notamment relier les postes d’un laboratoire, une imprimante et un serveur. Lorsqu’il sait sur quel port se trouve la destination, il transmet les données sur ce port.

### &#x20;La communication dans le même réseau local

Prenons un poste étudiant et une imprimante qui appartiennent au même réseau local. Lorsque l’étudiant lance une impression, le commutateur achemine les données vers l’imprimante. Les deux appareils peuvent être branchés sur des commutateurs différents, pourvu que ces commutateurs soient reliés et configurés pour prolonger le même réseau local.

Cet échange peut fonctionner même si l’accès à Internet est interrompu. Le document et l’imprimante se trouvent déjà dans le réseau du laboratoire.

### La communication entre deux réseaux

Lorsqu’un poste doit joindre un autre réseau, les données passent par un équipement qui assure le routage. Le routage consiste à choisir vers quel réseau transmettre les données pour les rapprocher de leur destination. Un routeur ou un commutateur de couche 3 peut remplir ce rôle.

Par exemple, si le serveur pédagogique se trouve dans un réseau distinct de celui du laboratoire, le poste étudiant utilise une passerelle pour le joindre. Si cette passerelle devient indisponible, le poste peut encore communiquer avec l’imprimante locale, même si le serveur pédagogique est devenu inaccessible.

### 5.4 La séparation logique avec les VLAN

Un VLAN (_Virtual LAN_, ou réseau local virtuel) permet de créer des réseaux locaux distincts sur une même infrastructure. Un cégep peut ainsi brancher des postes étudiants et des postes administratifs sur le même commutateur tout en les plaçant dans deux VLAN différents.

Un même VLAN peut aussi s’étendre sur plusieurs commutateurs. Par exemple, deux laboratoires situés à des étages différents peuvent appartenir au même VLAN étudiant. Une liaison configurée pour transporter plusieurs VLAN entre des commutateurs est souvent appelée un trunk.

Les communications entre deux VLAN passent normalement par un équipement qui assure le routage. On peut alors appliquer des règles pour déterminer les échanges permis. Par exemple, les étudiants pourraient être autorisés à utiliser une imprimante partagée, tandis que l’accès au serveur administratif serait réservé au personnel.

## Le transport des données et les ports

Après l’acheminement vers la bonne machine, les données doivent être remises à la bonne application. TCP, UDP et les numéros de port remplissent une partie de ce rôle.

### Le protocole TCP

TCP, Transmission Control Protocol, fournit à l’application un flux d’octets fiable et ordonné. L’établissement habituel d’une connexion utilise trois messages de contrôle, SYN, SYN-ACK et ACK.

TCP numérote les octets du flux. Les accusés de réception permettent de suivre la progression et de détecter les données à retransmettre. Si une partie manque, elle peut être renvoyée, notamment après l’expiration d’un délai de retransmission. Le récepteur remet les données dans l’ordre avant de les fournir à l’application. Une interruption durable peut toutefois faire échouer la connexion.

Ces mécanismes ajoutent des échanges et de l’attente. Ils conviennent notamment au transfert de fichiers, à l’administration distante et à plusieurs protocoles de messagerie. TCP gère aussi le flux et la congestion. Il ne chiffre pas les données par lui-même. Le chiffrement peut être apporté par un protocole comme TLS ou SSH.&#x20;

### Le protocole UDP

UDP, User Datagram Protocol, transmet des messages appelés datagrammes sans établir une connexion comme TCP. Il ne fournit lui-même ni accusé de réception, ni retransmission, ni remise en ordre. On parle d’un transport sans garantie de livraison, ou best effort.

Un datagramme peut se perdre, arriver en double ou arriver après un autre. L’application ou un protocole supérieur décide comment gérer ces situations. UDP comporte notamment des ports et un champ de somme de contrôle. Il serait donc incorrect de le décrire comme dépourvu de tout contrôle.

UDP convient à de petits échanges et à certaines communications sensibles au délai. Une application audio peut préférer compenser une perte plutôt qu’attendre un son devenu trop tardif. Cela dépend du protocole applicatif. Le choix d’UDP ne garantit pas à lui seul un meilleur débit.&#x20;

<figure><img src=".gitbook/assets/image (178).png" alt=""><figcaption><p>Comparaison des protocoles de transport TCP (Transmission Control Protocol) et UDP (User Datagram Protocol). Source : CP0218, Wikimedia Commons, CC0 1.0.</p></figcaption></figure>

### La comparaison de TCP et UDP

| Point observé            | TCP                                                                           | UDP                                                                |
| ------------------------ | ----------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| Organisation             | Connexion et flux d’octets.                                                   | Datagrammes distincts.                                             |
| Ordre et pertes          | Gestion intégrée de l’ordre, des accusés de réception et des retransmissions. | Aucune garantie équivalente fournie par UDP lui-même.              |
| Échanges supplémentaires | Établissement, suivi et contrôles.                                            | En-tête plus simple et pas d’établissement équivalent.             |
| Exemples                 | SSH, SMTP, HTTP/1.1 et HTTP/2.                                                | DNS classique, DHCP, TFTP et certaines applications en temps réel. |

### Les ports source et destination

Une adresse IP permet d’atteindre une interface. Un port de transport aide le système à remettre les données à la bonne application. Il faut distinguer ce numéro d’un port physique de commutateur, qui est une prise ou une interface de l’équipement.

Un serveur écoute généralement sur un port connu. Le client utilise souvent un port temporaire choisi par son système. Dans un échange TCP entre un navigateur au port 53014 et un serveur au port 8080, la demande part de 53014 vers 8080. La réponse part de 8080 vers 53014.

<figure><img src=".gitbook/assets/image (177).png" alt="" width="563"><figcaption><p>Ports source et destination d’une communication TCP. Schéma du cours</p></figcaption></figure>

Une communication se décrit notamment avec le protocole de transport, l’adresse et le port de chaque extrémité. TCP 53 et UDP 53 sont deux points d’écoute distincts. Un numéro de port donne un indice sur le service, mais un logiciel peut être configuré sur un autre port.

### Les plages de ports

Les numéros vont de 0 à 65535. L’IANA distingue les ports système de 0 à 1023, les ports utilisateur ou enregistrés de 1024 à 49151, puis les ports dynamiques ou privés de 49152 à 65535. Le port 0 est réservé.

La plage réellement utilisée par un système pour ses ports temporaires dépend de sa configuration. Elle peut différer de la plage dynamique définie dans le registre.&#x20;

### Les ports des principaux services

Les valeurs ci-dessous correspondent aux usages courants. Le tableau distingue les fonctions lorsque plusieurs ports interviennent.

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td>Service ou protocole</td><td>Transport et port habituels</td><td>Fonction</td></tr><tr><td>DNS</td><td>UDP 53 et TCP 53</td><td>Résolution des noms. Les deux transports sont nécessaires selon les échanges.</td></tr><tr><td>DHCP pour IPv4</td><td>UDP 67 serveur, UDP 68 client</td><td>Distribution d’une configuration IP.</td></tr><tr><td>HTTP</td><td>TCP 80</td><td>Échanges web en clair.</td></tr><tr><td>HTTPS</td><td>TCP 443, ou UDP 443 pour HTTP/3</td><td>Échanges web protégés par TLS ou par QUIC avec TLS.</td></tr><tr><td>SMTP entre serveurs</td><td>TCP 25</td><td>Acheminement du courrier entre serveurs.</td></tr><tr><td>Soumission du courrier</td><td>TCP 587 avec STARTTLS, ou TCP 465 avec TLS implicite</td><td>Envoi d’un message par le logiciel de l’utilisateur.</td></tr><tr><td>POP3</td><td>TCP 110, ou TCP 995 avec TLS implicite</td><td>Relève des messages.</td></tr><tr><td>IMAP</td><td>TCP 143, ou TCP 993 avec TLS implicite</td><td>Consultation et synchronisation des boîtes de courrier.</td></tr><tr><td>LDAP</td><td>TCP 389, ou TCP 636 avec TLS implicite</td><td>Accès à un annuaire. Certains usages particuliers emploient UDP 389.</td></tr><tr><td>SSH et SFTP</td><td>TCP 22</td><td>Administration distante chiffrée et transfert de fichiers par SFTP.</td></tr><tr><td>Telnet</td><td>TCP 23</td><td>Ancien accès distant en ligne de commande, sans protection du contenu.</td></tr><tr><td>RDP</td><td>TCP et UDP 3389</td><td>Accès distant au bureau graphique.</td></tr><tr><td>FTP</td><td>TCP 21 pour le contrôle. TCP 20 comme port source de données en mode actif classique.</td><td>Transfert de fichiers avec une connexion de données séparée. En mode passif, le serveur annonce un autre port.</td></tr><tr><td>TFTP</td><td>UDP 69 pour la requête initiale</td><td>Transfert simple. Le transfert se poursuit avec des ports choisis pour cet échange.</td></tr><tr><td>SMB</td><td>TCP 445</td><td>Partage de fichiers, d’imprimantes et d’autres ressources.</td></tr><tr><td>NetBIOS sur TCP/IP</td><td>UDP 137 pour les noms, UDP 138 pour les datagrammes, TCP 139 pour les sessions</td><td>Compatibilité avec des fonctions et applications anciennes.</td></tr><tr><td>AFP</td><td>TCP 548 pour AFP sur TCP/IP</td><td>Ancien protocole de partage de fichiers Apple.</td></tr><tr><td>SNMP</td><td>Généralement UDP 161 pour les requêtes et UDP 162 pour les notifications</td><td>Surveillance des équipements.</td></tr><tr><td>SLP</td><td>UDP et TCP 427</td><td>Découverte de services sur le réseau.</td></tr><tr><td>NTP</td><td>UDP 123</td><td>Synchronisation des horloges.</td></tr><tr><td>Syslog</td><td>Souvent UDP 514. TCP 6514 pour Syslog sur TLS.</td><td>Centralisation des messages de journalisation.</td></tr></tbody></table>

Dans l’adresse http://192.168.77.20:8080/, le serveur HTTP a été configuré sur le port 8080. Il faut utiliser ce port pour le tester ou pour écrire la règle de pare-feu correspondante.

## Les services réseau

Un service répond à un besoin concret, comme distribuer une configuration IP, trouver une adresse, afficher une page ou acheminer un courriel. Plusieurs services peuvent être hébergés sur la même machine.

### Le serveur DHCP

Le service DHCP, Dynamic Host Configuration Protocol, distribue automatiquement une configuration IP. En IPv4, il peut fournir une adresse, un masque, une passerelle par défaut et les adresses des résolveurs DNS.

Une attribution initiale courante comprend quatre étapes. Le client cherche un serveur avec DHCP Discover. Le serveur propose une configuration avec DHCP Offer. Le client demande l’offre retenue avec DHCP Request. Le serveur confirme avec DHCP ACK. On résume souvent cette séquence par DORA.

L’adresse est attribuée pour une durée appelée bail, que le client peut renouveler. Une réservation permet d’attribuer régulièrement la même adresse à un client identifié. Une configuration statique est définie directement dans le système ou dans son outil de gestion.

<figure><img src=".gitbook/assets/image (179).png" alt=""><figcaption><p>Les quatre messages du protocole DHCP lors de l'attribution d'une adresse IP</p></figcaption></figure>

Un serveur DHCP peut se trouver sur le routeur d’un logement ou sur un serveur de l’organisation. Un relais DHCP peut transmettre les demandes à un serveur situé dans un autre sous-réseau.&#x20;

### Le serveur DNS

Le DNS, Domain Name System, permet notamment de trouver une adresse à partir d’un nom. Pour joindre portail.exemple.test, le poste interroge un résolveur DNS. Celui-ci peut répondre à partir de son cache ou rechercher la réponse auprès d’autres serveurs.

Un serveur faisant autorité publie les informations d’une zone DNS. Le résolveur conserve les réponses pendant une durée indiquée, appelée TTL. Le cache réduit les recherches répétées.

Un enregistrement A associe un nom à une adresse IPv4. Un AAAA l’associe à une adresse IPv6. Un MX indique un serveur chargé de recevoir le courrier d’un domaine.

Le DNS classique emploie UDP et TCP. Les transferts de zone et certaines réponses volumineuses peuvent nécessiter TCP. Le DNS traite le nom d’hôte. Dans une adresse web, le chemin qui suit le nom est traité par le service web.&#x20;

<figure><img src=".gitbook/assets/image (180).png" alt="" width="563"><figcaption><p>Fonctionnement du protocole DNS : résolution d’un nom de domaine en adresse IP. Source : Aaron Filbert, Wikimedia Commons, CC BY-SA 4.0.</p></figcaption></figure>

### Le serveur web

Un serveur web reçoit des requêtes HTTP et retourne des ressources, par exemple une page, une image ou une réponse d’application. Une requête GET demande généralement une ressource.

Avec HTTPS, la communication est protégée. Le navigateur vérifie notamment le certificat présenté pour le nom demandé. Les échanges modernes utilisent TLS. Le terme SSL apparaît encore dans certaines interfaces, mais les anciennes versions SSL sont dépassées.

Le code 200 indique une réussite. Le code 404 indique que le service déclare la ressource introuvable. Le code 403 indique un refus de satisfaire la demande. Une erreur HTTP montre qu’un service HTTP a répondu. Une réussite DNS montre seulement qu’une réponse à la recherche de nom a été obtenue.&#x20;

<figure><img src=".gitbook/assets/image (182).png" alt="" width="563"><figcaption><p>Fonctionnement d’un serveur Web et communication avec les clients. Source : Ade56facc, Wikimedia Commons, CC BY-SA 4.0.</p></figcaption></figure>

### Le serveur de fichiers

Un serveur de fichiers permet de stocker et de partager des documents. Les comptes et les autorisations déterminent qui peut lire, modifier ou supprimer les ressources.

SMB est courant pour les partages Windows. Sous Linux, Samba fournit notamment des services compatibles SMB. CIFS désigne une ancienne variante de SMB, souvent utilisée comme terme historique. Les versions anciennes, comme SMB1, présentent des limites et ne doivent pas être confondues avec les versions récentes de SMB.

FTP utilise une connexion de contrôle et une connexion de données séparée. Dans sa forme de base, il ne protège pas les identifiants et le contenu par chiffrement. FTPS ajoute TLS à FTP. SFTP est un protocole de transfert de fichiers utilisant SSH. FTPS et SFTP exigent donc des configurations différentes.

SCP désigne une commande de copie distante associée à SSH ainsi qu’un ancien protocole de copie. Les versions récentes d’OpenSSH utilisent SFTP par défaut pour la commande scp. TFTP est plus simple et peut servir au chargement d’images ou de configurations dans un environnement contrôlé. AFP, Apple Filing Protocol, est un protocole historique de partage de fichiers Apple.&#x20;

Le choix du protocole dépend du besoin. Pour un dossier partagé utilisé quotidiennement depuis Windows, SMB est courant. Pour déposer des fichiers sur un serveur administré à distance, SFTP est souvent adapté.

### Le serveur d’impression

Un serveur d’impression centralise les imprimantes, les files d’attente et certains paramètres. Il reçoit les travaux, les organise et les transmet aux imprimantes concernées. Il peut aussi fournir l’état des travaux et signaler certains problèmes.

La centralisation facilite la gestion d’un ensemble d’imprimantes. En cas de problème, il faut distinguer le poste, la file du serveur, le trajet réseau et l’imprimante elle-même. Une imprimante peut également offrir directement son propre service réseau sans serveur d’impression séparé.

### Le serveur de messagerie

Un serveur de messagerie reçoit, conserve et transmet les courriels. Il gère les boîtes et les files de messages selon son logiciel. Les messages ne sont pas nécessairement stockés dans une base de données au sens classique, leur organisation dépend du produit.

SMTP sert à envoyer et à relayer les messages. IMAP permet de consulter et synchroniser les messages, les dossiers et leur état. POP3 permet de relever les messages. La conservation d’une copie sur le serveur dépend notamment des réglages du client.

<figure><img src=".gitbook/assets/image (183).png" alt=""><figcaption><p>Envoi, transfert entre serveurs et consultation d’un courriel.</p></figcaption></figure>

1\. Léa soumet son message à son serveur d’envoi, par exemple sur TCP 587 avec STARTTLS ou sur TCP 465 avec TLS implicite.

2\. Le serveur recherche normalement le MX du domaine destinataire, puis relaie le message vers le serveur de Sam par SMTP sur TCP 25.

3\. Le serveur destinataire conserve le message dans la boîte de Sam. Si une remise rencontre un problème temporaire, une file d’attente peut permettre une nouvelle tentative.

4\. Sam consulte ses messages, par exemple avec IMAP sur TCP 993. Son ordinateur pouvait être éteint au moment de l’envoi.

Avec une messagerie web, le navigateur utilise HTTPS pour communiquer avec le site. Les services internes se chargent ensuite de l’accès à la boîte. Une réception qui fonctionne alors que l’envoi échoue invite à vérifier séparément les paramètres SMTP, l’authentification et le mode TLS

### Le serveur proxy

Un proxy, ou serveur mandataire, reçoit et relaie des demandes. Il peut appliquer des politiques d’accès, conserver certains contenus en cache et produire des journaux, selon sa configuration.

Un proxy direct agit pour les clients. Un poste de bibliothèque peut adresser ses demandes web au proxy du cégep. Celui-ci applique les règles puis contacte les sites autorisés.

Un proxy inverse reçoit les demandes destinées à un service. Il peut présenter le site public, gérer TLS et répartir les demandes entre plusieurs serveurs internes.

<figure><img src=".gitbook/assets/image (184).png" alt="" width="563"><figcaption><p>Fonctionnement d’un serveur proxy servant d’intermédiaire entre un client et un serveur distant. Source : H2g2bob, Wikimedia Commons, CC0 1.0.</p></figcaption></figure>

Dans un tunnel HTTPS classique, le contenu peut rester chiffré entre le navigateur et le site. Une inspection HTTPS exige une configuration particulière qui établit des connexions TLS distinctes. La présence d’un proxy ne signifie donc pas automatiquement qu’il voit tout le contenu chiffré.

Un proxy inverse qui renvoie 502 indique qu’il a obtenu une réponse invalide d’un serveur en amont. L’enquête porte alors notamment sur la communication entre ces deux services.

### Le serveur d’authentification et l’annuaire

Un serveur d’authentification vérifie une identité et participe au contrôle d’accès. Il permet, par exemple, d’utiliser des comptes individuels pour se connecter au réseau Wi-Fi d’une organisation.

Un annuaire rassemble des informations sur les comptes, groupes et ressources. Le protocole LDAP, Lightweight Directory Access Protocol, sert à accéder à ces informations. Des solutions comme Active Directory combinent plusieurs services et protocoles. Selon l’usage, l’authentification peut aussi employer Kerberos, RADIUS ou d’autres mécanismes.

L’authentification répond à la question de l’identité. L’autorisation détermine les ressources et les actions permises. Un compte reconnu peut disposer du droit de lire un dossier sans pouvoir le modifier.

### Les services de journalisation et de surveillance

Un serveur Syslog reçoit les messages de journalisation envoyés par des équipements ou des systèmes. La centralisation facilite les recherches par date, machine ou événement. Le transport utilisé influence la confidentialité et les garanties de livraison.

SNMP, Simple Network Management Protocol, permet de consulter des informations de gestion, comme l’état d’une interface ou des compteurs. Un outil de supervision interroge les agents des équipements et peut recevoir des notifications. Les mécanismes de sécurité varient selon la version et la configuration.

NTP synchronise les horloges. Une heure cohérente facilite la comparaison des journaux de plusieurs machines. SLP, Service Location Protocol, permet à des appareils de découvrir des services, notamment dans certains environnements existants.

## Les connexions Internet

Le réseau local rejoint Internet par une liaison fournie par un opérateur. Le moyen d’accès dépend des infrastructures disponibles à l’adresse et des besoins des utilisateurs.

### Le fournisseur d’accès à Internet

Le fournisseur d’accès à Internet, ou FAI, relie le réseau de l’abonné à son infrastructure. La liaison entre un portable et son point d’accès peut être en Wi-Fi, tandis que la liaison du logement au fournisseur utilise de la fibre. Ces deux étapes emploient des technologies différentes.

Le terme haut débit décrit une capacité d’accès importante dans un contexte donné. Dans les techniques de transmission, broadband désigne aussi l’utilisation d’une bande de fréquences permettant de transporter plusieurs canaux. Plusieurs accès modernes utilisent différentes porteuses ou sous-porteuses pour transmettre les données.

### Les anciens accès téléphoniques

L’accès commuté, ou dial-up, utilisait un modem qui composait un numéro pour joindre un autre modem par le réseau téléphonique. Il occupait la ligne pendant la connexion et offrait un débit faible.

Le RNIS, réseau numérique à intégration de services, appelé ISDN en anglais, transportait des communications numériques et permettait de combiner plusieurs canaux. Il pouvait prendre en charge la voix, les données et certaines applications vidéo. Ces technologies servent aujourd’hui surtout de repères historiques ou apparaissent dans des installations anciennes.

### Les principaux moyens d’accès

Dans une liaison radio en visibilité directe, le trajet entre les antennes doit être suffisamment dégagé. Les bâtiments, la végétation et les conditions météorologiques peuvent avoir un effet qui dépend notamment de la fréquence utilisée.

Les satellites géostationnaires sont très éloignés de la Terre et introduisent un délai important. Les constellations en orbite basse réduisent ce délai. Les possibilités de jeu en ligne, de téléphonie ou de visioconférence dépendent donc de l’offre et de l’orbite, ainsi que des conditions d’utilisation.&#x20;

### Les critères de choix

Pour choisir une connexion, on vérifie d’abord sa disponibilité à l’adresse, puis les débits montant et descendant, la latence, les limites de données, la fiabilité et le coût total. Une entreprise qui envoie ses sauvegardes à l’extérieur a besoin d’un débit montant suffisant. Une activité avec des appels vidéo dépend aussi de la stabilité du délai.

La capacité annoncée concerne une liaison précise. Un accès Internet rapide ne corrige pas un câble défectueux, une mauvaise couverture Wi-Fi ou un serveur lent.

## La sécurité et l’administration du réseau

La disponibilité d’une connexion ne suffit pas. Il faut aussi contrôler les accès, protéger les échanges et administrer les équipements.

### Le pare-feu et les listes de contrôle d’accès

Un pare-feu autorise ou bloque les communications selon une politique. Les règles peuvent tenir compte des adresses, du protocole, des ports, du sens et de l’état d’une connexion. Le pare-feu peut être installé sur un poste ou placé entre des réseaux.

Une ACL, Access Control List, est une liste de règles de contrôle d’accès. Des ACL peuvent notamment être appliquées sur des routeurs et des commutateurs. Leurs capacités dépendent du matériel et du contexte.

Pour autoriser l’accès au serveur web du laboratoire, une règle doit viser le bon serveur, le bon transport et le bon port. Une règle sur TCP 8080 ne couvre pas automatiquement UDP 8080.

### Les IDS et IPS

Un IDS, Intrusion Detection System, observe les activités ou le trafic et produit des alertes lorsqu’il reconnaît des comportements suspects. Un IDS réseau peut recevoir une copie du trafic, ce qui lui permet d’observer sans être directement dans le chemin des paquets.

Un IPS, Intrusion Prevention System, peut prendre des mesures de blocage. Un IPS réseau est souvent placé en ligne pour examiner et arrêter certains échanges. Une règle trop sensible peut également bloquer du trafic légitime. Les alertes et les décisions doivent être surveillées.

| Élément  | Rôle principal                                | Exemple                                                                         |
| -------- | --------------------------------------------- | ------------------------------------------------------------------------------- |
| Pare-feu | Appliquer les règles de communication.        | Autoriser HTTPS vers un serveur et bloquer un autre port.                       |
| IDS      | Détecter et signaler des activités suspectes. | Alerter sur une suite de requêtes correspondant à une tentative d’exploitation. |
| IPS      | Détecter et agir sur les échanges.            | Bloquer un trafic correspondant à une règle de prévention.                      |

Un UTM, Unified Threat Management, regroupe plusieurs fonctions de sécurité, par exemple pare-feu, prévention d’intrusion, filtrage web, VPN et analyse de certains contenus. Les fonctions exactes dépendent du produit et des licences. Le regroupement facilite l’administration, mais la capacité de traitement doit correspondre au trafic.

### Le VPN

Un VPN, Virtual Private Network, crée une liaison logique privée au-dessus d’un autre réseau. Un VPN de sécurité utilise des mécanismes d’authentification et de chiffrement pour protéger le tunnel.

Un VPN d’accès distant permet à une personne de rejoindre des ressources de l’organisation depuis l’extérieur. Un VPN site à site relie deux réseaux, par exemple deux succursales, au moyen de passerelles.

Le VPN dépend de la connexion sous-jacente. Une connexion Internet coupée peut interrompre le tunnel. Les permissions restent nécessaires pour déterminer ce que l’utilisateur peut atteindre après la connexion.

### L’accès distant et les équipements particuliers

SSH fournit un accès distant chiffré en ligne de commande. Telnet est un protocole ancien qui transporte les échanges sans protection comparable. RDP, Remote Desktop Protocol, permet de travailler sur un bureau graphique distant. L’utilisation de ces services exige des comptes autorisés et un contrôle de leur exposition.

Un système ancien, ou legacy system, reste parfois utilisé parce qu’une application ou un équipement en dépend. Il peut être difficile à mettre à jour. Un système embarqué, ou embedded system, est intégré à un appareil pour une fonction particulière, comme une caméra, un automate ou un terminal.

Ces appareils doivent être inventoriés, configurés et surveillés. Selon leurs limites, on peut les placer dans un réseau séparé et restreindre leurs échanges aux services nécessaires. Le fait qu’un appareil soit petit ou spécialisé ne le dispense pas d’une configuration réseau et de règles d’accès.

### La gestion des terminaux et le contrôleur infonuagique

Un serveur de gestion des terminaux centralise des opérations comme l’inventaire, le déploiement de paramètres, l’installation d’applications ou le suivi des mises à jour. Les termes MDM et UEM apparaissent selon les appareils et les fonctions prises en charge.

Un contrôleur réseau basé sur le cloud permet d’administrer des équipements à partir d’une console hébergée à distance. Il peut centraliser les paramètres des points d’accès, les mises à jour et la surveillance. Le trafic des utilisateurs peut continuer à circuler localement, selon l’architecture. La dépendance à Internet et le comportement en cas de coupure doivent être vérifiés pour la solution choisie.

## Les technologies sans fil

Les notions précédentes s’appliquent aussi aux réseaux sans fil. Les principales différences concernent la liaison radio, sa portée et son partage. Le Wi-Fi dessert habituellement le réseau local; le cellulaire permet un accès étendu. D’autres technologies répondent aux besoins des périphériques et des objets connectés.

### Le Wi-Fi

Le Wi-Fi permet généralement de joindre un réseau local. Il repose sur la famille de normes IEEE 802.11. Le SSID est le nom du réseau affiché sur le poste, par exemple « Cegep-Etudiants ». Plusieurs points d’accès peuvent diffuser le même SSID.

Le client s’associe à un point d’accès et utilise le mécanisme d’authentification configuré. Selon le réseau, l’accès peut reposer sur une clé partagée ou sur des identifiants individuels. Le chiffrement radio est assuré par des mécanismes comme WPA2 ou WPA3, selon les capacités et la configuration.

La bande 2,4 GHz traverse souvent mieux les obstacles, mais elle est fréquemment encombrée. Les bandes 5 GHz et 6 GHz offrent d’autres canaux. Leur disponibilité dépend du matériel et de la réglementation. Les murs, les antennes et le placement influencent la couverture.

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th><th></th><th></th></tr></thead><tbody><tr><td>Norme</td><td>Nom commercial courant</td><td>Bande ou bandes</td><td>Repère de débit radio</td></tr><tr><td>802.11a</td><td>Ancienne génération</td><td>5 GHz</td><td>Jusqu’à 54 Mbit/s.</td></tr><tr><td>802.11b</td><td>Ancienne génération</td><td>2,4 GHz</td><td>Jusqu’à 11 Mbit/s.</td></tr><tr><td>802.11g</td><td>Ancienne génération</td><td>2,4 GHz</td><td>Jusqu’à 54 Mbit/s.</td></tr><tr><td>802.11n</td><td>Wi-Fi 4</td><td>2,4 et 5 GHz</td><td>Jusqu’à 600 Mbit/s dans la configuration maximale prévue.</td></tr><tr><td>802.11ac</td><td>Wi-Fi 5</td><td>5 GHz</td><td>De nombreux débits selon la configuration. 1,3 Gbit/s est un exemple, pas le maximum de toute la norme.</td></tr><tr><td>802.11ax</td><td>Wi-Fi 6 et Wi-Fi 6E</td><td>2,4 et 5 GHz, extension au 6 GHz avec 6E</td><td>Débits variables et meilleure utilisation d’un réseau chargé.</td></tr><tr><td>802.11be</td><td>Wi-Fi 7</td><td>2,4, 5 et 6 GHz selon l’équipement</td><td>Capacités accrues, notamment par des canaux plus larges et des liens multiples.</td></tr></tbody></table>

&#x20;

Les débits annoncés sont des débits radio théoriques. Le débit utile d’une application est inférieur et dépend des deux appareils. La largeur du canal et le nombre de flux radio influencent fortement le résultat.&#x20;

La rétrocompatibilité dépend des bandes et des modes activés. Un appareil 802.11g peut généralement communiquer avec un point d’accès qui accepte 802.11b/g. Un équipement 802.11n peut accepter a, b ou g sur les bandes compatibles. Un équipement 802.11ac peut généralement communiquer avec des clients 802.11a ou 802.11n compatibles en 5 GHz, selon les modes activés. Un réseau uniquement en 6 GHz exige des clients capables de fonctionner dans cette bande.

Les portées intérieures de 35 m, 38 m ou 70 m parfois données dans les tableaux d’introduction sont des estimations. Elles ne sont pas des portées maximales garanties par la norme. Dans un bâtiment, on vérifie la couverture réelle avec des mesures.

### Les réseaux cellulaires et leurs générations

Un réseau cellulaire répartit la couverture en cellules desservies par des stations radio. Le réseau peut transférer une communication d’une cellule à une autre lorsque l’utilisateur se déplace.

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td>Génération</td><td>Évolution principale</td><td>Usages associés</td></tr><tr><td>1G</td><td>Téléphonie mobile analogique.</td><td>Appels vocaux.</td></tr><tr><td>2G</td><td>Téléphonie numérique et premières données mobiles. Le GSM initial proposait notamment des données à 9,6 kbit/s.</td><td>Appels, identification de l’appelant, conférences téléphoniques et SMS.</td></tr><tr><td>2,5G et évolutions EDGE</td><td>GPRS puis EDGE améliorent les échanges de données par paquets.</td><td>Courriels, navigation simple, courts contenus audio et vidéo.</td></tr><tr><td>3G</td><td>Développement de l’accès Internet mobile avec UMTS et d’autres systèmes 3G.</td><td>Navigation, musique et vidéo, avec des débits dépendant de l’évolution du réseau.</td></tr><tr><td>3,5G</td><td>Appellation courante pour des améliorations comme HSPA et HSPA+.</td><td>Débits améliorés par rapport aux premières versions 3G.</td></tr><tr><td>4G et LTE</td><td>Évolution vers un réseau de données fondé sur IP, avec IPv4 ou IPv6 selon le déploiement. LTE-Advanced fait partie des technologies IMT-Advanced.</td><td>Vidéo, appels sur IP avec les services adaptés, jeux et accès mobile à haut débit.</td></tr><tr><td>5G</td><td>Évolution des capacités radio et du réseau, selon les bandes et les déploiements.</td><td>Accès mobile ou fixe, maisons et objets connectés, réalité augmentée, réalité virtuelle ou certains véhicules connectés.</td></tr></tbody></table>

&#x20;

LTE signifie Long Term Evolution. Les désignations commerciales et les critères techniques des générations ne correspondent pas toujours exactement. Les objectifs historiques de 100 Mbit/s en forte mobilité et de 1 Gbit/s en faible mobilité appartiennent au cadre IMT-Advanced. Ils ne sont pas une promesse de débit pour tout abonnement LTE.&#x20;

### Le partage de connexion

Le point d’accès mobile, ou hotspot, permet à un téléphone ou à un boîtier cellulaire de partager sa connexion Internet. Le partage peut utiliser le Wi-Fi, l’USB ou le Bluetooth, selon l’appareil.

Quand un portable rejoint le hotspot d’un téléphone en Wi-Fi, il participe à un WLAN. Le téléphone rejoint ensuite le WWAN de l’opérateur en 4G ou 5G. La consommation du portable compte alors dans les données du forfait mobile

<figure><img src=".gitbook/assets/image (185).png" alt=""><figcaption><p>Différence entre l’accès Wi-Fi au réseau local et l’accès cellulaire au réseau de l’opérateur</p></figcaption></figure>

### Le Bluetooth

Le Bluetooth relie des appareils personnels, comme un téléphone, des écouteurs, une souris ou un clavier. Il fonctionne dans la bande de 2,4 GHz, approximativement entre 2,400 et 2,4835 GHz. Sa portée dépend de la version, de la puissance et de l’environnement.

Le Bluetooth classique peut former un piconet avec un appareil central et jusqu’à sept périphériques actifs. Cette limite ne s’applique pas de façon générale à toutes les formes de Bluetooth, notamment Bluetooth Low Energy. La référence IEEE 802.15.1 correspond à une normalisation historique du Bluetooth. Les spécifications actuelles sont maintenues par le Bluetooth SIG.

### Le RFID et le NFC

Le RFID, Radio Frequency Identification, permet de reconnaître un objet à l’aide d’une étiquette radio et d’un lecteur. Une étiquette passive tire son énergie du champ du lecteur. Une étiquette active possède une source d’énergie, souvent une pile, qui permet des usages à plus grande portée.

On rencontre plusieurs familles de fréquences, notamment 125 ou 134 kHz en basse fréquence, 13,56 MHz en haute fréquence et des bandes UHF dont les allocations varient selon les pays, dans l’ensemble 860 à 960 MHz. La portée dépend de la technologie, de l’antenne et de l’environnement. Certaines solutions actives peuvent atteindre une centaine de mètres ou davantage. Ce chiffre ne décrit pas tous les systèmes RFID.

Le NFC, Near Field Communication, utilise 13,56 MHz sur une très courte distance, généralement quelques centimètres. Il sert notamment aux paiements, y compris au stationnement, aux titres de transport, aux badges et au lancement d’un appairage ou d’une impression. Pour imprimer, le contact NFC peut seulement établir les paramètres de connexion, puis une autre liaison transfère le document.

### Le Zigbee et le Z-Wave

Zigbee est utilisé pour des capteurs, ampoules et équipements de domotique. Il s’appuie sur IEEE 802.15.4 et permet des réseaux maillés. Un coordinateur crée le réseau. Certains appareils relaient les données, tandis que des appareils sur pile peuvent rester en veille entre deux échanges.

La bande 2,4 GHz est très courante, avec un débit radio de 250 kbit/s. D’autres bandes existent selon les versions et les régions, notamment autour de 868 ou 915 MHz. Ce sont des bandes distinctes. La capacité d’adressage peut atteindre environ 65 000 appareils, mais la capacité pratique d’un produit est généralement bien plus faible. Une portée d’une vingtaine de mètres constitue seulement un ordre de grandeur pour certains environnements.

Z-Wave est également destiné à la domotique et utilise généralement des fréquences inférieures à 1 GHz, adaptées à la région. Le réseau maillé Z-Wave classique peut compter jusqu’à 232 nœuds, avec des débits allant jusqu’à 100 kbit/s. Les extensions Z-Wave Long Range ont d’autres caractéristiques. Il faut donc identifier la version avant de comparer les limites. L’écosystème est maintenu par la Z-Wave Alliance, qui publie des spécifications et organise la certification

### Le choix d’une technologie sans fil

Le Wi-Fi convient à un portable qui consulte des sites et transfère des fichiers. Le Bluetooth convient à un casque ou un clavier. Le NFC convient à une interaction très proche et volontaire. Le RFID convient à l’identification d’objets. Zigbee et Z-Wave répondent aux besoins de nombreux capteurs et dispositifs de commande qui échangent peu de données.

## Références

Cisco. Bases des réseaux et conventions de représentation.

[https://www.cisco.com/site/us/en/learn/topics/small-business/networking-basics.html](https://www.cisco.com/site/us/en/learn/topics/small-business/networking-basics.html)

[https://www.cisco.com/c/en/us/about/brand-center/network-topology-icons.html](https://www.cisco.com/c/en/us/about/brand-center/network-topology-icons.html)

Fiber Optic Association. Structure et types de fibres.

[https://www.thefoa.org/tech/ref/basic/fiber.html](https://www.thefoa.org/tech/ref/basic/fiber.html)

Fluke Networks. Catégories de câblage et conditions de prise en charge de 10GBASE-T.

[https://www.flukenetworks.com/knowledge-base/applicationstandards-articles-copper/10gbase-t-field-testing-requirements](https://www.flukenetworks.com/knowledge-base/applicationstandards-articles-copper/10gbase-t-field-testing-requirements)

[https://www.flukenetworks.com/expertise/role/network-engineers](https://www.flukenetworks.com/expertise/role/network-engineers)

Cisco et IEEE. Normes Wi-Fi, bandes et caractéristiques radio.

[https://www.cisco.com/c/en/us/td/docs/wireless/controller/9800/technical-reference/wireless-rf-reference-guide.html](https://www.cisco.com/c/en/us/td/docs/wireless/controller/9800/technical-reference/wireless-rf-reference-guide.html)

[https://www.ieee802.org/11/](https://www.ieee802.org/11/)

Bluetooth SIG et IEEE. Présentation de Bluetooth, piconets Bluetooth classique et référence historique IEEE 802.15.1.

[https://www.bluetooth.com/learn-about-bluetooth/tech-overview/](https://www.bluetooth.com/learn-about-bluetooth/tech-overview/)

[https://www.ieee802.org/15/pub/TG1.html](https://www.ieee802.org/15/pub/TG1.html)

[https://www.bluetooth.com/wp-content/uploads/Files/Specification/HTML/Core-61/out/en/br-edr-controller/baseband-specification.html](https://www.bluetooth.com/wp-content/uploads/Files/Specification/HTML/Core-61/out/en/br-edr-controller/baseband-specification.html)

GS1. Familles de fréquences RFID et allocations UHF selon les pays.

[https://support.gs1.org/support/solutions/articles/43000734278-what-is-the-difference-between-low-high-and-ultra-high-frequencies-/](https://support.gs1.org/support/solutions/articles/43000734278-what-is-the-difference-between-low-high-and-ultra-high-frequencies-/)

[https://www.gs1.org/sites/gs1/files/uhf\_regulations.pdf](https://www.gs1.org/sites/gs1/files/uhf_regulations.pdf)

NFC Forum. Fonctionnement et usages du NFC.

[https://nfc-forum.org/learn/nfc-technology/](https://nfc-forum.org/learn/nfc-technology/)

Connectivity Standards Alliance et Silicon Labs. Zigbee, bandes et fonctionnement du réseau.

[https://csa-iot.org/all-solutions/zigbee/zigbee-faq/](https://csa-iot.org/all-solutions/zigbee/zigbee-faq/)

[https://docs.silabs.com/zigbee/latest/zigbee-fundamentals/01-overview](https://docs.silabs.com/zigbee/latest/zigbee-fundamentals/01-overview)

Z-Wave Alliance et Silicon Labs. Z-Wave classique, spécifications et différences avec Long Range.

[https://z-wavealliance.org/technology-overview/](https://z-wavealliance.org/technology-overview/)

[https://z-wavealliance.org/development-resources-overview/specification-for-developers/](https://z-wavealliance.org/development-resources-overview/specification-for-developers/)

[https://docs.silabs.com/z-wave/7.24.3/z-wave-performance-report/overview](https://docs.silabs.com/z-wave/7.24.3/z-wave-performance-report/overview)

CRTC. Rendement des connexions Internet et différences entre les orbites des satellites.

[https://crtc.gc.ca/fra/internet/performance.htm](https://crtc.gc.ca/fra/internet/performance.htm)

[https://crtc.gc.ca/fra/archive/2022/2022-147.htm](https://crtc.gc.ca/fra/archive/2022/2022-147.htm)

GSMA et UIT. Évolution des réseaux mobiles et objectifs IMT-Advanced.

[https://www.gsma.com/about-us/gsm-technology/](https://www.gsma.com/about-us/gsm-technology/)

[https://www.itu.int/en/ITU-R/study-groups/rsg5/rwp5d/imt-adv/Pages/default.aspx](https://www.itu.int/en/ITU-R/study-groups/rsg5/rwp5d/imt-adv/Pages/default.aspx)

UIT-T et IETF. Modèle OSI X.200 et architecture Internet RFC 1122.

[https://www.itu.int/rec/T-REC-X.200/fr](https://www.itu.int/rec/T-REC-X.200/fr)

[https://www.rfc-editor.org/rfc/rfc1122](https://www.rfc-editor.org/rfc/rfc1122)

IETF. ARP et découverte des voisins IPv6.

[https://www.rfc-editor.org/rfc/rfc826](https://www.rfc-editor.org/rfc/rfc826)

[https://www.rfc-editor.org/rfc/rfc4861](https://www.rfc-editor.org/rfc/rfc4861)

IETF. RFC 9293, Transmission Control Protocol.

[https://www.rfc-editor.org/rfc/rfc9293](https://www.rfc-editor.org/rfc/rfc9293)

IETF. RFC 768, User Datagram Protocol.

[https://www.rfc-editor.org/rfc/rfc768](https://www.rfc-editor.org/rfc/rfc768)

IETF. RFC 9000, QUIC, et RFC 9114, HTTP/3.

[https://www.rfc-editor.org/rfc/rfc9000](https://www.rfc-editor.org/rfc/rfc9000)

[https://www.rfc-editor.org/rfc/rfc9114](https://www.rfc-editor.org/rfc/rfc9114)

IANA. Registre des noms de services et des numéros de port.

[https://www.iana.org/assignments/service-names-port-numbers/](https://www.iana.org/assignments/service-names-port-numbers/)

IETF. RFC 2131, DHCP.

[https://www.rfc-editor.org/rfc/rfc2131](https://www.rfc-editor.org/rfc/rfc2131)

IETF. RFC 1034, DNS, et RFC 7766, utilisation de TCP par DNS.

[https://www.rfc-editor.org/rfc/rfc1034](https://www.rfc-editor.org/rfc/rfc1034)

[https://www.rfc-editor.org/rfc/rfc7766](https://www.rfc-editor.org/rfc/rfc7766)

IETF. RFC 9110, sémantique HTTP et intermédiaires.

[https://www.rfc-editor.org/rfc/rfc9110](https://www.rfc-editor.org/rfc/rfc9110)

OpenSSH. Documentation de la commande scp et utilisation de SFTP par défaut depuis OpenSSH 9.0.

[https://www.openssh.com/txt/release-9.0](https://www.openssh.com/txt/release-9.0)

IETF. SMTP, soumission du courrier, IMAP et protection TLS de la messagerie.

[https://www.rfc-editor.org/rfc/rfc5321](https://www.rfc-editor.org/rfc/rfc5321)

[https://www.rfc-editor.org/rfc/rfc6409](https://www.rfc-editor.org/rfc/rfc6409)

[https://www.rfc-editor.org/rfc/rfc9051](https://www.rfc-editor.org/rfc/rfc9051)

[https://www.rfc-editor.org/rfc/rfc8314](https://www.rfc-editor.org/rfc/rfc8314)
