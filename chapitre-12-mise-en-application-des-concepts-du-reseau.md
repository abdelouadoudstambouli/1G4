# Chapitre 12 - Mise en application des concepts du réseau

## Objectifs d’apprentissage :&#x20;

* Distinguer les adresses MAC et IPv4, reconnaître les classes A, B et C et différencier les adresses IP publiques et privées.
* Identifier les parties réseau et machine avec les masques /8, /16 et /24, puis déterminer l’adresse réseau, la première et la dernière adresse utilisable ainsi que l’adresse de diffusion.
* Configurer une connexion Ethernet ou Wi-Fi, en utilisant DHCP ou une configuration IPv4 manuelle avec le masque, la passerelle et le DNS appropriés.
* Accéder à l’interface d’administration d’un routeur et implémenter la configuration de base.
* Diagnostiquer des problèmes réseau simples à l’aide de ping, tracert et nslookup, et vérifier les paramètres du pare-feu Windows.
* Observer des échanges dans Wireshark pour repérer les adresses MAC et IP et reconnaître les principaux échanges ICMP, DHCP, DNS et TLS.

## Les éléments du réseau&#x20;

| **Élément**           | **Rôle**                                                                                                |
| --------------------- | ------------------------------------------------------------------------------------------------------- |
| Carte réseau          | Relie un appareil au réseau par câble Ethernet ou par Wi-Fi. Chaque connexion est une interface réseau. |
| Commutateur ou switch | Relie plusieurs appareils dans un même réseau local.                                                    |
| Point d’accès Wi-Fi   | Permet aux appareils sans fil de rejoindre le réseau local.                                             |
| Routeur               | Relie des réseaux différents. Dans un petit réseau, il sert généralement de passerelle vers Internet.   |

Une box ou un routeur Wi-Fi réunit souvent plusieurs de ces fonctions. Le réseau local peut fonctionner même si l’accès à Internet est interrompu.

<figure><img src=".gitbook/assets/image (186).png" alt=""><figcaption><p>Deux adresses complémentaires pour une même interface.</p></figcaption></figure>

## Comprendre les adresses MAC

MAC signifie Media Access Control. L’adresse MAC, aussi appelée adresse physique, identifie une interface sur une liaison Ethernet ou Wi-Fi. Un commutateur utilise les adresses MAC pour envoyer les trames vers les ports appropriés.

### Reconnaître une adresse MAC

Une adresse MAC classique contient six octets et s’écrit avec six groupes de deux caractères hexadécimaux. On y trouve les chiffres de 0 à 9 et les lettres de A à F. Les deux écritures ci-dessous désignent la même adresse.

```
00:1A:2B:3C:4D:5E
00-1A-2B-3C-4D-5E
```

<figure><img src=".gitbook/assets/image (187).png" alt=""><figcaption><p>Découpage classique d’une adresse MAC attribuée par un fabricant.</p></figcaption></figure>

Dans le découpage classique illustré, le préfixe OUI désigne une organisation, souvent le fabricant de la carte. Il ne désigne pas nécessairement la marque de l’ordinateur. Les trois autres octets distinguent l’interface dans le bloc de ce fabricant

### **Caractéristiques** d'une adresse MAC

* &#x20;La carte Ethernet et la carte Wi-Fi d’un même appareil ont chacune leur adresse MAC.
* Une MAC attribuée par le fabricant est normalement stable lorsque la même carte change de réseau.
* Une adresse MAC peut être modifiée ou rendue aléatoire, notamment en Wi-Fi. Elle ne constitue donc pas une preuve d’identité absolue.
* La MAC n’indique pas le réseau IPv4 auquel la machine appartient : c’est l’adresse IP, associée au masque, qui permet de le déterminer.

Pour repérer la MAC réelle, ouvrir les propriétés de la connexion dans Windows et rechercher Adresse physique ou Adresse physique (MAC).&#x20;

<figure><img src=".gitbook/assets/image (188).png" alt=""><figcaption><p>Vous pouvez trouver l'adresse MAC de votre carte réseau à cet emplacement. </p></figcaption></figure>

## Lire une adresse IPv4 et reconnaître sa classe

Une adresse IPv4 est composée de quatre nombres séparés par des points. Chaque nombre, appelé octet, va de 0 à 255. Un octet représente 8 bits ; l’ensemble d’une adresse IPv4 représente 32 bits.&#x20;

| Exemple        | Lecture                                                                   |
| -------------- | ------------------------------------------------------------------------- |
| 192.168.10.20  | Adresse IPv4 correctement écrite : quatre nombres compris entre 0 et 255. |
| 192.168.10.300 | Adresse incorrecte : 300 dépasse la valeur maximale d’un octet.           |

### Les classes A B et C

Dans le classement historique, le premier nombre permet de reconnaître la classe. Chaque classe est associée à un masque par défaut. Nous utilisons ces trois masques comme repères pour ce premier cours.

| Classe | Premier nombre | Masque par défaut | Notation courte | Octets réseau      |
| ------ | -------------- | ----------------- | --------------- | ------------------ |
| A      | 1 à 126        | 255.0.0.0         | /8              | Le premier         |
| B      | 128 à 191      | 255.255.0.0       | /16             | Les deux premiers  |
| C      | 192 à 223      | 255.255.255.0     | /24             | Les trois premiers |

{% hint style="info" %}
Les classes d’adresses IPv4 **A, B et C** correspondent à une méthode historique. L’adressage fondé sur ces classes est aujourd’hui **obsolète** et a été remplacé par l’adressage **sans classes, appelé CIDR.**
{% endhint %}

Les valeurs 0 et 127 du premier octet ont des usages particuliers. Par exemple, 127.0.0.1 désigne la machine elle-même. Les classes D, de 224 à 239, servent à la multidiffusion ; les valeurs de 240 à 255 relèvent d’usages réservés ou spéciaux. Elles ne servent pas à attribuer une adresse ordinaire à un poste dans ce cours.

### Trois exemples faciles à reconnaître

| Adresse       | Classe historique | Masque utilisé dans nos exemples |
| ------------- | ----------------- | -------------------------------- |
| 10.2.3.4      | A                 | 255.0.0.0                        |
| 172.16.5.8    | B                 | 255.255.0.0                      |
| 192.168.10.20 | C                 | 255.255.255.0                    |

Les réseaux actuels utilisent l’adressage sans classes. En pratique, lire toujours le masque configuré : le premier nombre ne suffit pas à connaître la séparation réseau/machine. Dans ce cours, nous conservons les masques par défaut ci-dessus.

## Séparer la partie réseau et la partie machine

La partie réseau est commune aux interfaces d’un même réseau IP. La partie machine, aussi appelée partie hôte, distingue les interfaces à l’intérieur de ce réseau. Le masque indique la séparation entre les deux.

Avec les trois masques étudiés, chaque 255 désigne un octet réseau et chaque 0 désigne un octet machine. Cette lecture simple s’applique aux trois masques de ce cours.

<figure><img src=".gitbook/assets/image (189).png" alt=""><figcaption><p>Les octets réseau sont bleus et les octets machine sont orange.</p></figcaption></figure>

### Que signifient les notations courtes

Le nombre après la barre indique combien de bits appartiennent à la partie réseau. /8 signifie 8 bits réseau, soit un octet ; /16 signifie 16 bits, soit deux octets ; /24 signifie 24 bits, soit trois octets. Il ne représente pas le nombre de machines.

| Même information             | Exemple complet                                            |
| ---------------------------- | ---------------------------------------------------------- |
| 255.0.0.0 équivaut à /8      | 10.2.3.4 avec 255.0.0.0 s’écrit 10.2.3.4/8.                |
| 255.255.0.0 équivaut à /16   | 172.16.5.8 avec 255.255.0.0 s’écrit 172.16.5.8/16.         |
| 255.255.255.0 équivaut à /24 | 192.168.10.20 avec 255.255.255.0 s’écrit 192.168.10.20/24. |

Dans 192.168.10.20/24, la partie machine est 20. L’adresse complète à donner pour identifier l’interface reste 192.168.10.20, accompagnée de son masque.

## Adresse réseau et adresses utilisables

Dans chaque réseau étudié, la première adresse désigne le réseau lui-même. La dernière adresse est l’adresse de diffusion, ou broadcast. Les adresses situées entre ces deux limites peuvent être attribuées aux interfaces, si elles sont libres.

| Notion                      | Signification                                                                                                         |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| Adresse réseau              | Première adresse du réseau. Elle désigne le réseau entier et ne s’attribue pas à un poste.                            |
| Première adresse utilisable | Première adresse que l’on peut attribuer à une interface. Elle vient juste après l’adresse réseau.                    |
| Dernière adresse utilisable | Dernière adresse attribuable à une interface. Elle précède l’adresse de diffusion.                                    |
| Adresse de diffusion        | Dernière adresse du réseau. Elle sert à la diffusion vers les hôtes de ce réseau ; elle ne s’attribue pas à un poste. |

### &#x20;Les trois exemples complets

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th><th></th><th></th></tr></thead><tbody><tr><td>Notion</td><td>Exemple en /24</td><td>Exemple en /16</td><td>Exemple en /8</td></tr><tr><td>Adresse du poste</td><td>192.168.10.20</td><td>172.16.5.8</td><td>10.2.3.4</td></tr><tr><td>Masque</td><td>255.255.255.0</td><td>255.255.0.0</td><td>255.0.0.0</td></tr><tr><td>Adresse réseau</td><td>192.168.10.0</td><td>172.16.0.0</td><td>10.0.0.0</td></tr><tr><td>Première utilisable</td><td>192.168.10.1</td><td>172.16.0.1</td><td>10.0.0.1</td></tr><tr><td>Dernière utilisable</td><td>192.168.10.254</td><td>172.16.255.254</td><td>10.255.255.254</td></tr><tr><td>Diffusion</td><td>192.168.10.255</td><td>172.16.255.255</td><td>10.255.255.255</td></tr></tbody></table>

Pour définir chaque partie, on utilise la méthode suivante:&#x20;

1\. Repérer les octets réseau grâce au masque et les conserver.

2\. Pour l’adresse réseau, remplacer tous les octets machine par 0.

3\. Pour la diffusion, remplacer tous les octets machine par 255.

4\. La première adresse utilisable suit l’adresse réseau ; la dernière utilisable précède la diffusion.

Exemple en /16 : 172.16 est conservé. La partie machine devient 0.0 pour le réseau et 255.255 pour la diffusion. La plage attribuable va donc de 172.16.0.1 à 172.16.255.254.

Ne pas confondre « première adresse » et « première adresse utilisable ». Une passerelle utilise souvent la première adresse utilisable, mais ce n’est pas une obligation. Une adresse déjà prise par le routeur n’est plus libre pour un poste.

{% hint style="info" %}
Cette méthode simplifiée est valable seulement pour les masques /8 , /16 et /24.&#x20;
{% endhint %}

## Reconnaître les machines du même réseau

Pour deux machines utilisant le même masque, comparer leur partie réseau. Si elle est identique, elles appartiennent au même réseau IP. Si elle diffère, un routeur est nécessaire pour passer d’un réseau à l’autre.

<figure><img src=".gitbook/assets/image (190).png" alt=""><figcaption><p>Deux machines dans le même réseau et une machine dans un autre réseau.</p></figcaption></figure>

| Masque commun | Deux adresses comparées        | Même réseau |
| ------------- | ------------------------------ | ----------- |
| 255.255.255.0 | 192.168.10.20 et 192.168.10.21 | Oui         |
| 255.255.255.0 | 192.168.10.20 et 192.168.11.20 | Non         |
| 255.255.0.0   | 172.16.5.8 et 172.16.9.30      | Oui         |
| 255.0.0.0     | 10.2.3.4 et 10.50.60.70        | Oui         |

Une même partie réseau ne garantit pas à elle seule la communication : la liaison doit fonctionner et les autorisations doivent permettre l’échange. Deux appareils d’un même réseau ne doivent pas utiliser la même adresse IPv4.

### Vérifier sa compréhension

1\. **Avec 192.168.10.45/24, quelle est l’adresse réseau ? Peut-on attribuer 192.168.10.255 à un poste ?**

Réponse : le réseau est 192.168.10.0. L’adresse 192.168.10.255 est la diffusion ; elle n’est pas attribuable.

**2. Avec 172.16.5.8/16, la première adresse utilisable est-elle 172.16.5.1 ?**

Réponse : non. Le réseau est 172.16.0.0 et sa première adresse utilisable est 172.16.0.1. Tous les octets machine doivent être pris en compte.

Une terminaison .0 ou .255 n’indique pas toujours une adresse réservée. Par exemple, 172.16.5.0 est utilisable dans 172.16.0.0/16 : ce n’est ni son adresse réseau ni sa diffusion.

## Distinguer IP privée et IP publique

Une adresse IPv4 privée est utilisée à l’intérieur d’un réseau local. Plusieurs maisons ou entreprises peuvent réutiliser les mêmes plages privées. Ces adresses ne sont pas directement routées sur Internet.&#x20;

| Plage privée complète         | Exemple privé |
| ----------------------------- | ------------- |
| 10.0.0.0 à 10.255.255.255     | 10.2.3.4      |
| 172.16.0.0 à 172.31.255.255   | 172.16.5.8    |
| 192.168.0.0 à 192.168.255.255 | 192.168.10.20 |

Ces plages ne donnent pas automatiquement le masque d’un réseau local : il faut lire le masque configuré. Toutes les adresses commençant par 172 ne sont pas privées ; seules celles de 172.16 à 172.31 appartiennent à la plage privée indiquée.

Une adresse IPv4 publique est destinée au routage sur Internet. Elle est attribuée par un fournisseur d’accès ou une organisation qui dispose d’un bloc d’adresses. Elle peut être fixe ou changer. « Publique » ne signifie pas que tous les services sont accessibles : un pare-feu peut les filtrer.

<figure><img src=".gitbook/assets/image (191).png" alt=""><figcaption><p>Exemple courant de partage d’un accès Internet par un routeur</p></figcaption></figure>

Dans cet exemple, le routeur traduit les adresses privées pour partager une adresse publique : c’est le NAT. Certains fournisseurs partagent aussi une adresse publique entre plusieurs abonnés ; l’adresse côté Internet du routeur n’est donc pas toujours publique.

### Ne pas mélanger les classifications

Classe A, B ou C décrit un classement historique. Privée ou publique décrit l’usage de l’adresse. Ainsi, 10.2.3.4 est de classe A et privée. Une adresse hors des trois plages privées n’est pas forcément publique : certaines adresses ont un usage réservé, comme 127.0.0.1.

Enfin, le profil réseau « Public » ou « Privé » de Windows règle surtout la découverte et le pare-feu. Il ne transforme pas une adresse IPv4 privée en adresse publique.

## Lire les paramètres et utiliser le DHCP

| Paramètre              | Ce qu’il faut reconnaître                                                                                |
| ---------------------- | -------------------------------------------------------------------------------------------------------- |
| Adresse IPv4 et masque | Identifient l’interface et son réseau. Le masque peut être écrit sous forme courte, par exemple /24.     |
| Passerelle par défaut  | Adresse du routeur utilisé pour rejoindre les autres réseaux.                                            |
| Serveur DNS            | Traduit un nom, comme www.microsoft.com, en une ou plusieurs adresses IP.                                |
| DHCP                   | Service qui fournit automatiquement les paramètres réseau. À la maison, le routeur joue souvent ce rôle. |

### Lire les propriétés dans Windows

1\. Ouvrir une fenêtre invite de commande cmd.&#x20;

2\. Utiliser la commande `ipconfig /all`  et choisir la connexion actuellement active.&#x20;

3\. Relever IPv4, masque ou longueur de préfixe, passerelle, DNS et adresse physique (MAC).

<figure><img src=".gitbook/assets/image (193).png" alt=""><figcaption><p><em>Propriétés de la connexion active</em></p></figcaption></figure>

### Choisir une attribution automatique

1\. Dans les paramètres du réseau, repérer Attribution d’adresse IP et choisir Modifier.

2\. Sélectionner Automatique (DHCP), puis Enregistrer. Mettre aussi l’attribution DNS en automatique si elle se règle séparément.

3\. Vérifier que l’appareil reçoit les paramètres attendus et que la liaison est connectée.

<figure><img src=".gitbook/assets/image (194).png" alt=""><figcaption><p><em>Attribution automatique par DHCP</em></p></figcaption></figure>

## Attribuer une adresse IPv4 manuellement

Une adresse manuelle, ou statique, est saisie dans les paramètres. Avant l’exercice, relever les anciens réglages. Utiliser une adresse libre indiquée par l’enseignant et compatible avec le réseau. Elle ne doit pas entrer en conflit avec une adresse distribuée par DHCP.

Pour cet exemple, le réseau est 192.168.10.0/24. Le routeur 192.168.10.1 sert de passerelle et de DNS. Le rôle DNS du routeur doit être confirmé sur le réseau réel.

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Champ</td><td>Valeur du poste 1</td></tr><tr><td>Adresse IPv4</td><td>192.168.10.20</td></tr><tr><td>Masque de sous-réseau</td><td>255.255.255.0</td></tr><tr><td>Longueur de préfixe si ce champ remplace le masque</td><td>24</td></tr><tr><td>Passerelle</td><td>192.168.10.1</td></tr><tr><td>DNS préféré</td><td>192.168.10.1</td></tr><tr><td>DNS auxiliaire</td><td>Laisser vide pour cet exemple.</td></tr></tbody></table>

### Saisir puis vérifier

1\. Ouvrir les propriétés du réseau dans Paramètres, puis Modifier à côté de l’attribution IP.

2\. Choisir Manuel, activer IPv4 et saisir les valeurs du tableau. Si le champ demande une longueur de préfixe, saisir 24, sans la barre ; si le champ demande un masque, saisir 255.255.255.0.

3\. Renseigner le DNS, dans le même formulaire ou dans l’attribution DNS séparée selon la version de Windows, puis enregistrer.&#x20;

4\. Relire les propriétés et tester la passerelle avec ping 192.168.10.1.

<figure><img src=".gitbook/assets/image (195).png" alt=""><figcaption><p><em>Configuration manuelle du poste</em></p></figcaption></figure>

Un deuxième poste peut utiliser 192.168.10.21 si cette adresse est libre. Dans cet exemple, son masque, sa passerelle et son DNS restent identiques. Après l’exercice, rétablir les paramètres initiaux ou le mode automatique demandé.

## Se connecter par câble ou par Wi Fi

### La connexion Ethernet

1\. Brancher le câble Ethernet sur la carte du poste et sur un port LAN du routeur ou du commutateur.

2\. Vérifier l’enclenchement des connecteurs, les voyants éventuels et l’état de la carte dans Windows.

3\. Utiliser DHCP ou les paramètres du laboratoire, puis tester une ressource locale.

Pour brancher un ordinateur au petit routeur, utiliser un port LAN. Le port WAN ou Internet sert généralement à la liaison vers le modem ou le fournisseur d’accès.

### La connexion Wi Fi

Le SSID est le nom du réseau Wi-Fi affiché dans la liste des réseaux disponibles. Le mot de passe Wi-Fi autorise la connexion à ce réseau.

1\. Activer le Wi-Fi et désactiver le mode Avion.

2\. Ouvrir la liste des réseaux, sélectionner le SSID du laboratoire et choisir Se connecter.

3\. Saisir le mot de passe Wi-Fi en respectant les caractères, puis vérifier l’état Connecté.

Être connecté au Wi-Fi confirme la liaison avec le point d’accès. Cela ne garantit pas que l’accès à Internet fonctionne.

## Accéder à la page de configuration du routeur

Le routeur possède une interface d’administration accessible depuis un navigateur sur le réseau local. Elle permet de modifier les réglages. Utiliser le routeur du laboratoire et les identifiants fournis par l’enseignant.

| Information                   | Utilité                                                                                       |
| ----------------------------- | --------------------------------------------------------------------------------------------- |
| SSID                          | Nom du réseau Wi-Fi que l’on choisit pour se connecter.                                       |
| Mot de passe Wi-Fi            | Permet à un appareil de rejoindre le réseau sans fil.                                         |
| Mot de passe d’administration | Permet de modifier la configuration du routeur. Il doit être différent du mot de passe Wi-Fi. |

### Connexion depuis le navigateur

1\. Relier le poste au routeur, de préférence par câble sur un port LAN pendant les changements Wi-Fi. Une liaison Wi-Fi existante convient aussi.

2\. Relever la passerelle dans les propriétés réseau de Windows. Dans notre exemple, elle est 192.168.10.1. Dans un petit réseau, il s’agit souvent de l’adresse de gestion du routeur ; sinon, consulter son étiquette ou sa documentation.

3\. Ouvrir le navigateur et saisir l’adresse de gestion dans la barre d’adresse. Exemple : https://192.168.10.1 si le modèle utilise HTTPS. Utiliser l’adresse et le protocole indiqués par le constructeur, pas une recherche Web.

4\. Saisir le compte administrateur et son mot de passe, ou créer ce mot de passe si l’assistant du premier démarrage le demande. Il n’existe pas de mot de passe universel pour tous les routeurs.

5\. Vérifier que le tableau de bord correspond au routeur attendu. Les menus peuvent s’appeler Wi-Fi, Sans fil, Wireless, Administration ou Système.

<figure><img src=".gitbook/assets/image (196).png" alt=""><figcaption><p>Connexion au routeur depuis le navigateur. Source : Cisco IT Essential</p></figcaption></figure>

Si la page ne s’ouvre pas, vérifier la connexion au bon réseau et l’adresse de gestion. Un réseau invité peut interdire l’administration. En cas d’avertissement de certificat ou de mot de passe oublié, faire confirmer la procédure par l’enseignant ou la documentation du modèle. Ne pas utiliser le bouton Reset pour une simple difficulté de connexion.

## Changer le SSID et le mot de passe Wi Fi

### Modifier le nom du réseau

1\. Dans la page du routeur, ouvrir Wi-Fi ou Sans fil, puis les réglages du réseau principal.

2\. Repérer Nom du réseau, Network Name ou SSID. Saisir un nom clair, par exemple Labo-Reseau-Groupe1.

3\. Si plusieurs bandes possèdent des noms séparés, modifier la ou les bandes prévues pour l’exercice. Avec un nom commun, une modification peut concerner plusieurs bandes.

4\. Choisir Enregistrer ou Appliquer, puis rechercher le nouveau nom sur le poste. Le changement peut couper la connexion Wi-Fi.

<figure><img src=".gitbook/assets/image (197).png" alt=""><figcaption><p> Changer le SSID sur un routeur Cisco. Source : Cisco IT Essential</p></figcaption></figure>

### Modifier le mot de passe du réseau sans fil

1\. Dans les réglages Wi-Fi, repérer Mot de passe, Password ou Clé de sécurité.

2\. Choisir une phrase secrète longue et propre à ce réseau. Garder WPA3-Personal si les appareils le prennent en charge, ou WPA2-Personal avec AES selon la compatibilité du laboratoire.

3\. Enregistrer. Reconnecter les appareils avec le nouveau mot de passe. Si Windows garde l’ancien, choisir Oublier pour ce réseau dans les réseaux connus, puis se reconnecter.

4\. Vérifier l’état Connecté et l’accès à la ressource prévue. Le mot de passe d’administration n’a pas changé

<figure><img src=".gitbook/assets/image (198).png" alt=""><figcaption><p>Modifier le mot de passe Wi-Fi sur un routeur Cisco. Source : Cisco IT Essential</p></figcaption></figure>

{% hint style="info" %}
Les menus dépendent du modèle. Sur plusieurs routeurs TP-Link, le chemin est Advanced > Wireless > Wireless Settings ; sur d’autres, Wi-Fi > Main Network. Utiliser ces noms comme exemples, puis suivre le menu réellement présent.
{% endhint %}

## Changer le mot de passe administrateur

Le mot de passe administrateur protège les réglages du routeur. Le connaître permet notamment de changer le Wi-Fi, le DHCP ou les autres paramètres. Il doit être réservé aux personnes responsables du réseau.

### Procédure de modification

1\. Se connecter à la page du routeur avec les identifiants administrateur actuels.

2\. Ouvrir Administration, Système, Compte ou Login Account. Sur certains routeurs TP-Link, le chemin est Advanced > System > Administration.&#x20;

3\. Saisir le mot de passe actuel, puis le nouveau mot de passe et sa confirmation. Choisir un secret long, unique et différent de celui du Wi-Fi.

4\. Enregistrer la modification. Si la session se ferme, se reconnecter avec le nouveau mot de passe. Une déconnexion après changement peut être normale.

5\. Conserver ce secret dans le gestionnaire de mots de passe prévu par l’établissement. Le transmettre seulement selon la consigne de l’enseignant.

### Vérifier le résultat

| Vérification                        | Résultat attendu                                                               |
| ----------------------------------- | ------------------------------------------------------------------------------ |
| Ouvrir à nouveau la page de gestion | Le nouveau mot de passe administrateur permet la connexion.                    |
| Reconnecter un appareil au Wi-Fi    | Il utilise le mot de passe Wi-Fi ; le secret administrateur n’est pas demandé. |
| Rechercher le réseau sans fil       | Le SSID est celui enregistré dans les réglages Wi-Fi.                          |

Changer le mot de passe administrateur ne change pas automatiquement le mot de passe Wi-Fi. Changer le SSID ne change pas automatiquement les deux mots de passe. Noter séparément le rôle de chaque réglage.

## Vérifier le pare feu Windows

Un pare-feu applique des règles pour autoriser ou bloquer les communications. Une communication entrante arrive vers le poste ; une communication sortante part du poste. Les réponses aux échanges autorisés peuvent revenir sans ouvrir toutes les connexions entrantes.

### Reconnaître le profil réseau

| Profil Windows | Utilisation                                                                                                 |
| -------------- | ----------------------------------------------------------------------------------------------------------- |
| Public         | Pour un réseau inconnu ou lorsque le partage local n’est pas nécessaire. À conserver en cas de doute.       |
| Privé          | Pour un réseau de confiance où la découverte et le partage sont prévus. Au laboratoire, suivre la consigne. |
| Domaine        | Profil géré par l’organisation sur certains postes. Il ne se choisit pas manuellement dans cet exercice.    |

Ces profils Windows n’indiquent pas si votre adresse IP est publique ou privée. Passer un profil Windows en Privé ne modifie pas l’adresse IPv4 et ne rend pas, à lui seul, le réseau sûr.

### Contrôler le profil actif

1\. Ouvrir Démarrer, rechercher Sécurité Windows et ouvrir l’application.

2\. Choisir Pare-feu et protection réseau, puis repérer le profil actif.

3\. Ouvrir ce profil et vérifier que le Pare-feu Microsoft Defender est activé.

<figure><img src=".gitbook/assets/image (199).png" alt=""><figcaption><p>État du pare-feu sur le profil actif</p></figcaption></figure>

## Créer une règle Pare-feu&#x20;

Un **pare-feu** fonctionne comme un gardien à l’entrée d’un bâtiment. Il contrôle les communications de ton ordinateur et décide lesquelles peuvent passer.

Une **règle de pare-feu** est une consigne donnée à ce gardien : « Autorise cette communication » ou « Bloque cette communication ».

**Pour comprendre le trafic entrant et sortant, placez vous du côté de votre ordinateur.**

| Type de trafic | Ce que cela signifie                     | Exemple                                                                |
| -------------- | ---------------------------------------- | ---------------------------------------------------------------------- |
| **Entrant**    | Des données arrivent sur ton ordinateur. | Un autre ordinateur demande à accéder à un dossier partagé sur ton PC. |
| **Sortant**    | Des données quittent ton ordinateur.     | Ton navigateur envoie une demande pour ouvrir un site web.             |

Ces échanges peuvent se faire avec Internet ou avec un autre ordinateur du même réseau.

**Une communication utilise souvent les deux sens.** Quand tu ouvres une page web :

1. Votre ordinateur demande la page : le trafic est **sortant**.
2. Le site envoie la page à ton ordinateur : le trafic est **entrant**.

Les pare-feu courants reconnaissent généralement la réponse à une demande autorisée. Vous n'avez donc habituellement pas besoin de créer une règle entrante pour recevoir cette réponse.

**Pour créer une règle, Vous devez préciser ce que vous voulez laisser passer ou bloquer.**

| Élément               | Question à se poser                                         |
| --------------------- | ----------------------------------------------------------- |
| **Sens**              | Le trafic entre-t-il ou sort-il de mon ordinateur ?         |
| **Source**            | De quel appareil vient-il ?                                 |
| **Destination**       | Vers quel appareil va-t-il ?                                |
| **Protocole et port** | Quel type de communication et quel service sont concernés ? |
| **Action**            | Faut-il autoriser ou bloquer ?                              |

<figure><img src=".gitbook/assets/image (201).png" alt=""><figcaption><p>Comment accéder au paramètres d'une règle Pare-feu.</p></figcaption></figure>

Une **adresse IP** sert à identifier un appareil sur le réseau. Un **port** est un numéro qui permet de joindre un service sur cet appareil. **TCP** et **UDP** sont deux protocoles, c’est-à-dire deux façons d’organiser les échanges.

Prenons un exemple : **Vous hébergezs un petit site web sur votre ordinateur**, et ce site utilise TCP avec le port 443. Vous voulez que les autres étudiants puissent le consulter.

Votre règle pourrait dire :

> Autoriser le trafic entrant venant des ordinateurs de la classe vers le port TCP 443 de mon ordinateur.

C’est une règle **entrante**, car les demandes arrivent sur ton ordinateur. Si c’est vous qui visitez le site d’un autre étudiant, votre demande est **sortante**.

Pour commencer, autorisez seulement les communications nécessaires. Vérifiez ensuite que l’accès souhaité fonctionne et que les accès qui doivent rester bloqués le sont bien.



## Commencer un dépannage et utiliser ping

Commencer par les vérifications simples. Modifier un seul élément à la fois, puis refaire le même test pour savoir ce qui a corrigé le problème.

1\. Décrire le problème : quelle ressource ne répond pas ? Un seul appareil est-il touché ou plusieurs ?

2\. Vérifier l’alimentation, le câble ou le Wi-Fi, le mode Avion et le bon SSID.

3\. Lire l’IPv4, le masque, la passerelle et le DNS dans les propriétés Windows, puis les comparer aux valeurs attendues.

4\. Tester la passerelle, une ressource locale, puis un nom de site. Garder le message exact obtenu.

### Ping pour vérifier une réponse

Ouvrir Démarrer et rechercher Invite de commandes. Ping envoie une demande de réponse à une adresse ou à un nom. Il permet de vérifier si la cible répond au test ICMP.&#x20;

```
ping  IP_Destination
```

Dans notre exemple, cette adresse est celle de la passerelle. Utiliser l’adresse réellement configurée si le laboratoire emploie un autre réseau.

| Résultat observé                 | Interprétation simple                                                                                    |
| -------------------------------- | -------------------------------------------------------------------------------------------------------- |
| Réponse de la cible              | Une réponse au test a été reçue. Cela ne garantit pas que toutes les applications fonctionnent.          |
| Délai d’attente dépassé          | Pas de réponse reçue : cible éteinte, liaison, routage ou filtrage possibles.                            |
| Hôte de destination inaccessible | Un équipement signale qu’il ne peut pas atteindre la destination. Relire la configuration et la liaison. |

<figure><img src=".gitbook/assets/image (200).png" alt=""><figcaption><p>Test de la passerelle avec ping</p></figcaption></figure>

Un routeur peut ignorer le ping tout en transmettant d’autres échanges. Si le test échoue, confirmer avec la liaison, les paramètres et la ressource recherchée avant de conclure à une panne du routeur.

## Utiliser tracert et nslookup

### Tracert pour observer les étapes du trajet

Tracert affiche les étapes qui répondent sur le chemin vers une destination. Chaque ligne représente un saut observé, généralement un routeur. Le trajet peut varier.&#x20;

```
tracert Destination
```

Lire le numéro de saut, puis le nom ou l’adresse à droite. Des astérisques indiquent l’absence de réponse au test pour cette étape ; ils ne prouvent pas automatiquement qu’un routeur est en panne. Si le nom ne se résout pas, vérifier d’abord le DNS.

<figure><img src=".gitbook/assets/image (202).png" alt=""><figcaption><p>Résultat d'un Trcaert vers www.omnivox.com</p></figcaption></figure>

### Nslookup pour interroger le DNS

Le DNS associe des noms à des adresses IP. Nslookup demande au serveur DNS des informations sur un nom ; ici, on cherche les adresses associées à un site.&#x20;

```
nslookup Destination 
```

Les premières lignes identifient le serveur DNS interrogé. Les lignes de réponse donnent le nom demandé et une ou plusieurs adresses. Ne pas confondre l’adresse du serveur DNS avec celle du site. Une réponse « ne faisant pas autorité » peut être normale : elle n’indique pas une panne.

<figure><img src=".gitbook/assets/image (203).png" alt=""><figcaption><p>Mon DNS me répond que www.omnivox.com est équivalent à 208.77.80.13</p></figcaption></figure>

Si le délai d’attente est dépassé, vérifier le DNS configuré et sa joignabilité. Si le nom est indiqué comme inexistant, vérifier l’orthographe. Une réponse DNS correcte ne garantit pas que le site Web est disponible.

## Associer les symptômes aux vérifications

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td>Symptôme</td><td>Cause possible</td><td>Première vérification</td></tr><tr><td>Aucune connexion filaire</td><td>Câble, port ou carte désactivée.</td><td>Contrôler le branchement, les voyants et la carte ; essayer un câble fonctionnel.</td></tr><tr><td>SSID absent</td><td>Wi-Fi désactivé, mode Avion ou réseau renommé.</td><td>Activer le Wi-Fi et rechercher le nom actuellement configuré sur le routeur.</td></tr><tr><td>Mot de passe Wi-Fi refusé</td><td>Mauvais SSID, erreur de saisie ou ancienne clé mémorisée.</td><td>Vérifier le nom et le secret du laboratoire ; oublier le réseau puis se reconnecter si nécessaire.</td></tr><tr><td>Adresse 169.254.x.x en automatique</td><td>Le poste n’a généralement pas obtenu de réponse DHCP.</td><td>Vérifier la liaison et le mode automatique ; faire vérifier le service DHCP.</td></tr><tr><td>Deux postes ont la même IPv4</td><td>Conflit d’adresses.</td><td>Revenir au DHCP ou utiliser une adresse libre validée par l’enseignant.</td></tr><tr><td>Un poste ne joint pas ses voisins</td><td>Adresse, masque ou autorisation incorrects.</td><td>Comparer les parties réseau ; tester avec ping puis vérifier la ressource et le pare-feu.</td></tr><tr><td>Le local fonctionne mais pas Internet</td><td>Passerelle incorrecte ou accès Internet indisponible.</td><td>Relire la passerelle et comparer avec un autre appareil du réseau.</td></tr><tr><td>Les noms ne sont pas résolus</td><td>DNS incorrect ou inaccessible.</td><td>Lire le DNS dans les propriétés Windows puis essayer nslookup.</td></tr><tr><td>Une seule application échoue</td><td>Application arrêtée, mauvaise adresse ou filtrage.</td><td>Vérifier l’application cible et son autorisation pour le profil actif.</td></tr></tbody></table>

### La passerelle et le chemin de retour

La passerelle permet de sortir du réseau local. Dans notre laboratoire, le poste 192.168.10.20/24 utilise 192.168.10.1. Une réponse de cette passerelle confirme un échange local avec elle, mais ne prouve pas que sa connexion Internet fonctionne.

Pour joindre un autre réseau, les routeurs doivent disposer d’un chemin vers la destination et d’un chemin de retour. Tracert aide à observer les étapes qui répondent ; il ne remplace pas la vérification de la configuration.

Avant de redémarrer un routeur partagé, prévenir l’enseignant : les autres utilisateurs seront également déconnectés. Noter la cause trouvée, la modification effectuée et le résultat du nouveau test.

## Références&#x20;

[IEEE — Composition des adresses MAC et préfixes OUI](https://standards-support.ieee.org/hc/en-us/articles/4888705676564-Guidelines-for-Use-of-Extended-Unique-Identifier-EUI-Organizationally-Unique-Identifier-OUI-and-Company-ID-CID)

&#x20;[IETF RFC 9724 — Adresses MAC aléatoires](https://datatracker.ietf.org/doc/rfc9724/)

&#x20;[Microsoft Learn — Principes des adresses et masques IPv4](https://learn.microsoft.com/fr-fr/troubleshoot/windows-client/networking/tcpip-addressing-and-subnetting)

[Cisco — Adresses IPv4 et classes historiques](https://www.cisco.com/c/en/us/support/docs/ip/routing-information-protocol-rip/13788-3.html)

&#x20;[IANA — Plages IPv4 privées](https://www.iana.org/help/private-addresses)

[Microsoft Support — Paramètres réseau et attribution IP](https://support.microsoft.com/fr-fr/windows/experience/connectivity-networking/essential-network-settings-and-tasks-in-windows)

&#x20;[Microsoft Support — Connexion à un réseau Wi-Fi](https://support.microsoft.com/fr-fr/windows/experience/connectivity-networking/connect-to-a-wi-fi-network-in-windows)

&#x20;[TP-Link — Accès et configuration depuis un navigateur](https://www.tp-link.com/ca/support/faq/3841/)

&#x20;[TP-Link — Réglages du nom et du mot de passe Wi-Fi](https://www.tp-link.com/us/support/faq/3085/)

&#x20;[TP-Link — Modification du mot de passe administrateur](https://www.tp-link.com/us/support/faq/73/)

[Microsoft Support — Pare-feu et protection réseau](https://support.microsoft.com/fr-fr/windows/security/windows-security/firewall-and-network-protection-in-the-windows-security-app)

&#x20;[Microsoft Learn — ping](https://learn.microsoft.com/fr-fr/windows-server/administration/windows-commands/ping)

&#x20;[Microsoft Learn — tracert](https://learn.microsoft.com/fr-fr/windows-server/administration/windows-commands/tracert)

[Microsoft Learn — nslookup](https://learn.microsoft.com/fr-fr/windows-server/administration/windows-commands/nslookup)

