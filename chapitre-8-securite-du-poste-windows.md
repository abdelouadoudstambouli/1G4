---
hidden: true
---

# Chapitre 8 - Sécurité du poste Windows

## Objectifs d'apprentissage

* Expliquer le rôle de l’UEFI, de Secure Boot et du TPM pendant le démarrage.
* Décrire la protection offerte par BitLocker et l’importance de la clé de récupération.
* Distinguer les rôles de l’antivirus, de SmartScreen et de Smart App Control.
* Expliquer comment Windows Hello et les passkeys permettent de s’authentifier.
* Reconnaître les usages et les limites de Windows Sandbox.
* Lire une stratégie de sécurité locale et expliquer l’effet de quelques règles courantes.

## Pourquoi plusieurs protections sont nécessaires

Un ordinateur peut être exposé à des problèmes très différents : le vol du portable, un fichier malveillant, une fausse page de connexion ou un compte mal protégé. Une seule fonction ne peut pas répondre à toutes ces situations. Windows combine donc plusieurs mécanismes, chacun avec un rôle précis.

Prenons un portable oublié dans un autobus. L’antivirus peut être parfaitement à jour et pourtant ne pas empêcher une personne de tenter de lire le disque. Dans cette situation, le chiffrement du disque est essentiel. Si le propriétaire retrouve son portable mais ouvre ensuite une pièce jointe malveillante, d’autres protections entrent en jeu.

Pour comprendre une fonction de sécurité, posez-vous trois questions : que protège-t-elle, à quel moment intervient-elle et quelles sont ses limites? Ces questions vous aideront aussi à choisir la bonne vérification lors d’un dépannage.

## Quelques repères avant de commencer&#x20;

### Protéger les données et contrôler les accès

La confidentialité consiste à empêcher la lecture d’informations par des personnes non autorisées. L’intégrité consiste à éviter les modifications non autorisées. La disponibilité consiste à conserver l’accès aux données et aux services quand on en a besoin. Par exemple, chiffrer un disque protège sa confidentialité, mais ne remplace pas une sauvegarde en cas de panne.

L’authentification vérifie l’identité de la personne qui se connecte. L’autorisation détermine ensuite ce que son compte a le droit de faire. Un étudiant peut réussir sa connexion à Windows et ne pas avoir l’autorisation d’installer un logiciel. Il ne s’agit pas d’un échec de connexion, mais d’une limite de ses droits.

Un compte standard suffit pour la plupart des tâches courantes. Un compte administrateur peut modifier des réglages qui touchent le système ou les autres utilisateurs. Utiliser les droits nécessaires au travail, sans en ajouter inutilement, correspond au principe du moindre privilège.

### Trois états à distinguer

| **État du poste**   | **Ce que cela signifie**                                                                                                                           |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Éteint              | Windows ne fonctionne plus. Le chiffrement du disque aide à protéger les données contre une lecture hors du système.                               |
| Session verrouillée | Il faut s’authentifier pour reprendre le travail. Windows et certaines applications continuent de fonctionner. Le volume peut rester déverrouillé. |
| Session ouverte     | Les applications travaillent avec les droits du compte. Elles peuvent accéder aux fichiers autorisés, même si le disque est chiffré.               |

&#x20;

### Vérifier l’édition avant de chercher une fonction

L’édition apparaît dans `Paramètres > Système > Informations système`, dans les spécifications de Windows. La commande `winver` affiche aussi la version et le numéro de build. Deux postes Windows 11 peuvent donc présenter des options différentes.

| Fonction                               | Disponibilité à connaître                                                                                                                     |
| -------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Defender Antivirus et Windows Hello    | Fonctions intégrées aux éditions courantes. La reconnaissance du visage ou des empreintes demande du matériel compatible.                     |
| BitLocker et chiffrement de l’appareil | Gestion complète de BitLocker sur Pro, Entreprise et Éducation. Le chiffrement de l’appareil existe aussi sur des postes Famille compatibles. |
| Windows Sandbox                        | Éditions Pro, Entreprise et Éducation compatibles; pas Windows Famille.                                                                       |
| Console secpol.msc                     | Éditions Pro, Entreprise et Éducation. Son absence sur Famille ne signifie pas que ce poste n’a aucune règle de sécurité.                     |
| Smart App Control                      | Dépend aussi de la version, des mises à jour et de la configuration du poste. Sa présence ne se déduit pas du seul nom de l’édition.          |

## &#x20;Le démarrage sécurisé&#x20;

### Le rôle de l’UEFI

Avant de pouvoir afficher le bureau, l’ordinateur doit préparer son matériel et trouver le programme qui lancera Windows. Ce travail commence dans le microprogramme. Sur les ordinateurs modernes, ce microprogramme utilise généralement l’UEFI.

### Le problème des programmes chargés avant Windows

Un programme malveillant qui s’exécute très tôt peut tenter de modifier le fonctionnement du système avant que les protections habituelles soient disponibles. Un bootkit, par exemple, s’attaque à la chaîne de démarrage. Il faut donc vérifier les éléments chargés dès le début, et pas seulement analyser les fichiers une fois le bureau affiché.

### Secure Boot vérifie les composants de démarrage

Secure Boot, ou démarrage sécurisé, est une fonction de l’UEFI. Elle vérifie les signatures numériques des logiciels de démarrage à l’aide de références de confiance et de listes de révocation. Un composant qui n’est pas autorisé peut être empêché de se charger.

Une signature numérique permet de vérifier l’origine annoncée d’un programme et de détecter une modification de son contenu après la signature. Elle ne signifie pas que le programme est parfait ou qu’il ne contient aucune faille. Les mises à jour du système et du microprogramme restent nécessaires.

| **Étape simplifiée**      | **Ce qui se passe**                                                                                               |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Mise sous tension         | L’UEFI initialise le matériel et sélectionne l’entrée de démarrage.                                               |
| Vérification du démarrage | Secure Boot contrôle les composants de démarrage selon les éléments approuvés ou révoqués.                        |
| Chargement de Windows     | Les mécanismes de démarrage approuvé de Windows poursuivent les vérifications du noyau et des composants chargés. |
| Ouverture de la session   | Les services de sécurité fonctionnent et l’utilisateur s’authentifie.                                             |

### Ce que Secure Boot ne fait pas

Secure Boot ne chiffre pas les documents et ne décide pas qui peut ouvrir une session. Il ne bloque pas non plus tous les logiciels malveillants exécutés après le démarrage. Sa fonction est de renforcer la confiance dans les composants qui permettent au système de démarrer.

Secure Boot n’interdit pas automatiquement Linux. Un autre système peut démarrer si sa chaîne de démarrage respecte les signatures et les règles acceptées par le microprogramme. On vérifie donc la compatibilité avant de modifier un réglage.

## Le TPM et les mesures de démarrage

### Un composant spécialisé dans la protection des clés

TPM signifie Trusted Platform Module, ou module de plateforme sécurisée. Il réalise des opérations cryptographiques et aide à protéger des clés. Il peut prendre la forme d’un composant dédié ou d’une fonction intégrée à la plateforme. Les noms Intel PTT et AMD fTPM désignent des mises en œuvre que l’on peut rencontrer dans les réglages du microprogramme.

Une clé cryptographique est une valeur utilisée pour chiffrer, déchiffrer ou signer des données. Certaines clés protégées par le TPM peuvent être utilisées sans être rendues directement accessibles aux applications. Le TPM peut aussi limiter les essais répétés d’une valeur d’autorisation, comme un code PIN.

### Vérifier et mesurer sont deux opérations différentes

Secure Boot vérifie si un composant est autorisé à se charger. Le démarrage mesuré enregistre des empreintes de certains éléments de démarrage dans le TPM. Une empreinte est une valeur calculée à partir d’un contenu; une modification de ce contenu produit normalement une autre valeur.

Ces mesures peuvent servir à conditionner l’utilisation d’une clé. Avec BitLocker, le système peut ainsi remarquer que l’environnement de démarrage a changé et demander une récupération au lieu de déverrouiller automatiquement le volume. Cela ne veut pas dire que le TPM a découvert un virus.

Le TPM ne chiffre pas lui-même chaque document du disque. Windows réalise le chiffrement des données; le TPM participe à la protection et à l’utilisation des clés. Il joue aussi un rôle dans des mécanismes d’authentification comme Windows Hello.

| **Élément** | **Rôle principal**                                      |
| ----------- | ------------------------------------------------------- |
| UEFI        | Préparer le matériel et lancer le démarrage.            |
| Secure Boot | Contrôler l’autorisation des composants de démarrage.   |
| TPM         | Protéger des clés et conserver des mesures de sécurité. |
| BitLocker   | Chiffrer les volumes et protéger les données stockées.  |

### Lire l’état du poste

Avec `Windows + R`, entrez `msinfo32`. Dans Résumé système, repérez Mode BIOS et État du démarrage sécurisé. « UEFI » indique le mode utilisé; « Activé » indique l’état de Secure Boot. Un mode UEFI ne prouve pas, à lui seul, que Secure Boot est activé.

La commande `tpm.msc` ouvre la gestion du TPM. Elle permet de consulter son état et la version de spécification. Windows 11 demande normalement TPM 2.0 dans ses exigences matérielles prises en charge. Dans une VM, l’UEFI et le TPM peuvent être virtuels et dépendent de la configuration de cette VM.

Ne choisissez pas Effacer le TPM pour effectuer une simple vérification. Cette opération peut rendre des clés inutilisables et déclencher une récupération BitLocker ou une reconfiguration de Windows Hello. Avant une intervention sur le microprogramme ou le TPM, on vérifie l’accès à la clé de récupération.

{% hint style="info" %}
Exemple : après le remplacement d’une carte mère, le disque contient toujours les mêmes fichiers, mais le TPM a changé. BitLocker peut alors demander la clé de récupération. Le chiffrement fonctionne comme prévu : le matériel habituel n’est plus présent.
{% endhint %}

## Le chiffrement avec BitLocker

### Pourquoi le mot de passe Windows ne suffit pas

Le mot de passe Windows contrôle l’ouverture de la session. Il ne rend pas automatiquement les fichiers illisibles sur le disque. Une personne qui possède physiquement un ordinateur peut essayer de retirer son disque ou de démarrer un autre système pour lire son contenu. Les permissions du Windows installé ne constituent pas, à elles seules, une protection contre cette lecture hors ligne.

BitLocker chiffre un volume, par exemple le lecteur C:. Les données enregistrées deviennent illisibles sans les éléments nécessaires au déchiffrement. Cette protection vise notamment la perte, le vol et l’accès physique non autorisé.

### Ce qui se passe pendant une utilisation normale

Une fois le volume déverrouillé, Windows déchiffre les données nécessaires lorsqu’il les lit et chiffre celles qu’il écrit. L’utilisateur n’a pas à déchiffrer manuellement chaque fichier. Le disque reste chiffré; c’est l’accès à son contenu qui est autorisé.

Dans une configuration avec TPM, le déverrouillage peut être automatique lorsque les conditions attendues de démarrage sont respectées. Une organisation peut demander un code PIN BitLocker avant le démarrage de Windows. Ce PIN de démarrage est différent du PIN Windows Hello utilisé pour ouvrir la session.

BitLocker peut aussi protéger un volume de données. La fonction BitLocker To Go concerne les supports amovibles compatibles, par exemple une clé USB. Selon le type de volume et la configuration, le déverrouillage peut utiliser un mot de passe, une clé ou un autre mécanisme autorisé.

### Comprendre les limites de la protection

| **Situation**                                       | **Effet de BitLocker**                                                                                        |
| --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| Un disque chiffré est retiré du PC                  | Son contenu n’est pas directement lisible sans un moyen de déverrouillage.                                    |
| L’utilisateur ouvre son document                    | Windows lui donne accès au fichier si le volume est déverrouillé et si ses permissions le permettent.         |
| Un logiciel malveillant agit dans la session        | Il peut tenter d’accéder aux fichiers avec les droits dont il dispose. BitLocker ne remplace pas l’antivirus. |
| Un fichier est supprimé ou le disque tombe en panne | Le chiffrement ne fournit pas une copie de secours. Une sauvegarde reste nécessaire.                          |
| Un fichier est envoyé par courriel                  | La protection BitLocker du disque ne suit pas automatiquement la copie envoyée.                               |

Le verrouillage de la session et l’arrêt du poste ne sont pas équivalents. Sur un poste déjà démarré, le volume peut rester déverrouillé même si l’écran demande un PIN. Pour évaluer le risque de vol, il faut donc tenir compte de l’état du poste, des clés en mémoire et de sa configuration.

{% hint style="info" %}
Exemple : une technicienne transporte un portable contenant des dossiers confidentiels. BitLocker limite le risque de lecture du disque en cas de perte. Les permissions, le verrouillage de session, l’antivirus et les sauvegardes restent utiles pour les autres situations.
{% endhint %}

## BitLocker et la récupération des données

### La clé de récupération

La clé de récupération BitLocker présentée à l’utilisateur est habituellement un code de 48 chiffres. Elle permet de déverrouiller un volume lorsque le mécanisme habituel ne fonctionne plus. L’identifiant affiché sur l’écran de récupération aide à choisir la bonne clé lorsqu’on en possède plusieurs.

Une demande de récupération peut suivre un changement de carte mère, une modification de réglages de démarrage ou un problème lié au TPM. Elle ne signifie pas automatiquement qu’une attaque a eu lieu. Il faut d’abord comprendre ce qui a changé.

La clé peut avoir été sauvegardée dans un compte Microsoft, dans le compte professionnel ou scolaire, ou dans un emplacement protégé prévu par l’organisation. Une copie papier conservée en lieu sûr est également possible. La seule copie ne doit pas se trouver sur le volume qu’elle doit déverrouiller.

Vérifiez l’emplacement de la clé avant une intervention, pas après une panne. Toute personne disposant de cette clé et du volume peut potentiellement accéder aux données. Elle ne doit donc pas apparaître dans une capture remise avec un travail ni rester dans un dossier partagé. Si aucun moyen de récupération utilisable ne subsiste, les fichiers peuvent devenir irrécupérables.

### BitLocker complet et chiffrement de l’appareil

Sur Windows Pro, Entreprise et Éducation, la gestion BitLocker offre les options de configuration des lecteurs. Sur certains postes Windows Famille, le Chiffrement de l’appareil utilise aussi la technologie BitLocker, avec une présentation plus simple et une configuration liée aux possibilités du matériel.

Sur un appareil compatible, le chiffrement peut s’activer lors de la configuration avec un compte Microsoft ou un compte professionnel ou scolaire, avec sauvegarde de la récupération dans ce compte. Avec un compte local, cette activation automatique ne se produit pas de la même manière. Il faut toujours consulter l’état réel du poste.

### Suspendre la protection et déchiffrer

| **Opération**           | **Conséquence**                                                                                                                                                     |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Suspendre la protection | Les données restent chiffrées, mais une possibilité temporaire de déverrouillage non protégée est conservée. Le poste est donc moins protégé pendant cette période. |
| Reprendre la protection | Les protecteurs sont remis en service après l’intervention prévue.                                                                                                  |
| Désactiver BitLocker    | Le volume est progressivement déchiffré. La confidentialité apportée par son chiffrement disparaît.                                                                 |

Une suspension peut être demandée par une procédure de maintenance. On suit cette procédure et on vérifie ensuite la reprise de la protection. Il n’est pas nécessaire de suspendre manuellement BitLocker pour chaque mise à jour habituelle de Windows.

### Vérifier sans modifier

Recherchez Gérer BitLocker dans Démarrer, ou ouvrez `Paramètres > Confidentialité et sécurité > Chiffrement de l’appareil` si cette page existe. Dans une console administrateur, la commande suivante affiche l’état du volume sans changer sa configuration.

```
manage-bde -status C:
```

Lisez le pourcentage de chiffrement, l’état de protection et l’état de verrouillage. Un volume à 100 % chiffré avec une protection suspendue ne présente pas le même niveau de protection qu’un volume dont les protecteurs sont actifs.

## Microsoft Defender Antivirus

### Ce que recherche un antivirus

Un logiciel malveillant, ou malware, est conçu pour nuire à un système, voler des données ou réaliser une action non autorisée. Le mot virus est souvent utilisé pour tous ces logiciels, mais un virus n’est qu’une catégorie parmi d’autres.

| **Type de menace**                      | **Exemple de comportement**                                                                                                         |
| --------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Virus                                   | Se propage en infectant d’autres fichiers.                                                                                          |
| Cheval de Troie                         | Se présente comme un programme utile pour faire exécuter une action malveillante.                                                   |
| Rançongiciel                            | Bloque l’accès aux données, souvent en les chiffrant, et réclame un paiement.                                                       |
| Logiciel espion                         | Collecte des informations à l’insu de l’utilisateur.                                                                                |
| Application potentiellement indésirable | Ajoute de la publicité, des composants inutiles ou des comportements gênants; elle n’est pas nécessairement classée comme un virus. |

Microsoft Defender Antivirus est l’antivirus intégré à Windows. Il peut surveiller des fichiers et des programmes, signaler une détection et prendre une mesure comme la mise en quarantaine. Il travaille avec plusieurs méthodes, car les menaces changent régulièrement.

### Plusieurs méthodes de détection

La détection par signatures reconnaît des caractéristiques déjà associées à des menaces. Le terme signature désigne ici un indice de détection; il ne s’agit pas de la signature numérique de l’éditeur d’un logiciel. Les renseignements de sécurité doivent être mis à jour pour prendre en compte les nouvelles menaces connues.

L’analyse du comportement observe ce que fait un programme. Un programme qui tente de modifier de nombreux fichiers ou des réglages sensibles peut nécessiter une vérification. Les analyses heuristiques cherchent aussi des caractéristiques suspectes sans dépendre uniquement d’une correspondance exacte avec une menace connue.

La protection fournie par le cloud consulte des informations actualisées de Microsoft. Elle complète les capacités présentes sur le poste. L’envoi d’échantillons peut permettre l’analyse de fichiers suspects; dans une organisation, ces options doivent respecter les règles de traitement des données.

### Protection en temps réel et analyse demandée

La protection en temps réel agit pendant l’utilisation du poste, notamment lorsque des fichiers sont ouverts ou exécutés. Une analyse à la demande est lancée à un moment choisi. Les deux se complètent : lancer une analyse aujourd’hui ne justifie pas de laisser la protection en temps réel désactivée demain.

Un antivirus peut manquer une menace ou signaler un fichier légitime. Ce dernier cas s’appelle un faux positif. L’absence de détection n’est donc pas une preuve absolue d’innocuité, et une alerte demande une vérification du contexte.

Le nom Microsoft Defender désigne plusieurs produits. Sécurité Windows est l’application qui regroupe les réglages du poste. Microsoft Defender Antivirus est le moteur antivirus intégré. Microsoft Defender for Endpoint ajoute des fonctions de surveillance et de réponse pour les organisations; il ne faut pas confondre tous ces produits.

## Lire les analyses et les alertes de Defender

### Choisir un type d’analyse

Ouvrez Sécurité Windows depuis Démarrer, puis Protection contre les virus et menaces. Cette page permet notamment de consulter l’état de protection, les mises à jour et les options d’analyse.

| **Analyse**                   | **Usage principal**                                                                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Rapide                        | Examine les zones où les menaces se trouvent fréquemment, notamment celles liées au démarrage. Elle sert à une vérification courante. |
| Complète                      | Parcourt plus largement les fichiers et programmes accessibles à l’analyse. Sa durée dépend du contenu et des exclusions configurées. |
| Personnalisée                 | Cible un dossier, un fichier ou un emplacement choisi.                                                                                |
| Microsoft Defender hors ligne | Redémarre le poste et effectue une analyse depuis l’environnement de récupération, avant le chargement normal de Windows.             |

« Hors ligne » ne veut pas simplement dire débrancher Internet. Le point essentiel est que l’analyse s’exécute en dehors de la session Windows habituelle. Avant de la lancer, on enregistre le travail ouvert. Le résultat peut ensuite être consulté dans l’Historique de protection.

### Comprendre les actions proposées

La quarantaine isole un élément détecté pour empêcher son utilisation normale. La suppression retire l’élément. Restaurer remet un élément en circulation; autoriser demande à la protection de tolérer une menace identifiée. Ces dernières actions exigent donc une vérification sérieuse de la provenance et du besoin.

Pour lire une alerte, relevez son heure, le nom de la détection, le chemin du fichier et l’action prise. Une alerte ancienne suivie d’une mise en quarantaine ne signifie pas nécessairement qu’une menace est encore active. À l’inverse, une action en attente ne doit pas être confondue avec une correction terminée.

### Des réglages qui changent réellement la protection

La protection contre les falsifications limite les modifications non autorisées de paramètres importants de Defender. Elle aide notamment à empêcher qu’un logiciel malveillant désactive certaines défenses. Les administrateurs d’une organisation peuvent en contrôler la configuration.

Une exclusion demande à Defender d’ignorer certains éléments pour les analyses concernées. Une exclusion trop large, comme tout un dossier de téléchargements, crée une zone moins surveillée. Elle ne doit pas être utilisée simplement pour faire disparaître une alerte.

L’accès contrôlé aux dossiers limite les modifications de dossiers protégés par des applications non approuvées. Il peut aider contre les rançongiciels, mais aussi bloquer une application légitime. Il faut alors identifier précisément le programme et vérifier la règle, sans désactiver la protection de tous les dossiers.

### Antivirus et pare-feu

L’antivirus recherche des menaces dans les fichiers, les programmes et leurs comportements. Le pare-feu contrôle des communications réseau selon des règles. Un programme autorisé à communiquer peut être malveillant, et un programme sain peut être bloqué par une règle réseau. Les deux protections répondent à des questions différentes.

Lorsqu’un antivirus tiers compatible devient le produit principal, le comportement de Defender change selon la configuration du poste. On vérifie le fournisseur actif dans Sécurité Windows. Installer deux antivirus résidents en espérant doubler la protection peut provoquer des conflits.

## SmartScreen et Smart App Control

### SmartScreen et la réputation

SmartScreen aide à repérer des sites dangereux et des applications téléchargées qui présentent un risque. Il s’appuie notamment sur des renseignements de réputation. La réputation correspond ici aux informations accumulées sur une adresse, un fichier ou un éditeur; elle ne se limite pas à la présence d’une signature.

Dans Microsoft Edge, SmartScreen peut avertir qu’une page ressemble à un site d’hameçonnage ou qu’elle distribue du contenu dangereux. L’hameçonnage consiste à tromper une personne pour lui faire révéler une information, approuver une connexion ou réaliser une action au profit d’un attaquant.

Dans Windows, les vérifications de réputation peuvent aussi intervenir lorsqu’on tente de lancer une application provenant d’Internet. Un programme peu connu peut déclencher un avertissement même si l’antivirus ne l’a pas identifié comme malveillant. Les deux outils n’utilisent pas exactement les mêmes critères.

### Une application inconnue n’est pas nécessairement infectée

Une petite application créée par un développeur peut être récente, peu téléchargée et sans réputation établie. SmartScreen peut donc manquer d’informations pour la considérer comme fiable. Cela explique l’avertissement, sans constituer une autorisation de l’ignorer.

Inversement, une apparence professionnelle, un certificat HTTPS ou un nom familier ne prouvent pas qu’un téléchargement est sûr. Un attaquant peut utiliser un nom proche de celui d’un vrai logiciel. Il faut regarder le domaine, le parcours de téléchargement, l’éditeur et le fichier concerné.

### Comment réagir à un avertissement

1\.  Lisez le message et identifiez ce qui est bloqué : la page, le téléchargement ou l’exécution du programme.

2\.  Vérifiez si vous attendiez réellement ce fichier et si vous avez utilisé le site officiel de l’éditeur.

3\.  Comparez le nom du fichier, l’éditeur affiché et, lorsque c’est pertinent, sa signature numérique.

4\.  Sur un poste de cours ou d’entreprise, transmettez ces renseignements à la personne responsable avant de poursuivre.

La présence éventuelle d’un bouton permettant de continuer n’est pas une garantie de sécurité. Certaines règles d’entreprise peuvent d’ailleurs interdire ce choix. On ne désactive pas toute la protection pour régler un seul téléchargement.

### Où consulter les réglages

Dans Sécurité Windows, ouvrez Contrôle des applications et du navigateur, puis les paramètres de protection fondée sur la réputation. Dans Edge, les réglages de sécurité du navigateur complètent cette protection. Les noms exacts peuvent varier légèrement selon la langue et la version.

SmartScreen n’analyse pas automatiquement toute l’activité de tous les navigateurs et de tous les fichiers partagés. Un fichier obtenu sur un partage interne ne bénéficie pas nécessairement des mêmes contrôles qu’un fichier téléchargé sur Internet. L’antivirus et la vérification des sources restent donc nécessaires.

{% hint style="info" %}
Exemple : une page prétend installer une mise à jour urgente du navigateur. SmartScreen affiche une alerte. Le bon réflexe est de fermer cette page et de vérifier la mise à jour depuis le navigateur ou la source officielle, plutôt que d’exécuter le fichier proposé.
{% endhint %}

## Smart App Control et le lancement des applications

### Le contrôle intelligent des applications

Smart App Control, souvent abrégé SAC, cherche à empêcher l’exécution d’applications malveillantes, potentiellement indésirables ou insuffisamment fiables. Il intervient au niveau du contrôle des applications. Il complète l’antivirus au lieu de le remplacer.

Lorsqu’une application doit s’exécuter, le service de sécurité peut utiliser des renseignements dans le cloud pour estimer sa fiabilité. Si ces renseignements ne permettent pas de décider, la validité de sa signature peut être prise en compte. Une application sans signature valable et sans niveau de confiance suffisant peut être bloquée.

### Les états que l’on peut rencontrer

| **État**   | **Signification**                                                                                                                                             |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Évaluation | Windows observe l’usage des applications pour déterminer si cette protection convient au poste. Pendant cette évaluation, SAC ne bloque pas les applications. |
| Activé     | Smart App Control applique ses contrôles et peut empêcher certaines applications de s’exécuter.                                                               |
| Désactivé  | Smart App Control n’applique plus cette protection. Les autres mécanismes, dont l’antivirus, ont leur propre état.                                            |

Certaines applications de développement ou certains outils internes peuvent manquer de réputation ou de signature. Le blocage peut alors gêner un usage légitime. La solution se prépare avec l’éditeur ou l’administrateur : obtenir une version correctement distribuée, vérifier sa signature ou utiliser un environnement de test approprié.

Smart App Control ne propose pas actuellement une simple exception permettant à l’utilisateur d’autoriser individuellement n’importe quelle application bloquée. Une exclusion antivirus n’est donc pas une exception Smart App Control.

### Activation et version de Windows

Consultez Sécurité Windows > Contrôle des applications et du navigateur > Paramètres du contrôle intelligent des applications. L’état disponible dépend du poste, de son usage et de ses règles de gestion.

Les conditions d’activation ont évolué. La documentation Microsoft indique que des mises à jour récentes permettent, sur les appareils admissibles, l’activation ou la réactivation sans installation propre. Certaines configurations ou versions plus anciennes restent soumises à d’autres conditions. Il faut vérifier la version et les options affichées avant de conclure qu’une réinstallation est nécessaire.

### Comparer les trois protections

| **Protection**     | **Question principale**                                                                  | **Action possible**                                         |
| ------------------ | ---------------------------------------------------------------------------------------- | ----------------------------------------------------------- |
| Defender Antivirus | Ce fichier ou ce comportement ressemble-t-il à une menace?                               | Détecter, bloquer, mettre en quarantaine ou supprimer.      |
| SmartScreen        | Cette page ou cette application téléchargée présente-t-elle une réputation préoccupante? | Avertir ou bloquer selon le contexte et les règles.         |
| Smart App Control  | Cette application présente-t-elle un niveau de confiance suffisant pour s’exécuter?      | Empêcher l’exécution si les critères ne sont pas respectés. |

Un message de blocage doit être attribué au bon composant. Si un étudiant appelle toute alerte « l’antivirus », il risque de chercher le réglage au mauvais endroit et de désactiver une protection qui n’est pas responsable du blocage.

## Windows Hello et la connexion au poste

### Prouver son identité sans retaper le mot de passe

Windows Hello permet de se connecter avec un code PIN, une empreinte digitale ou la reconnaissance du visage. L’objectif est de vérifier localement que la personne est autorisée à utiliser le compte sur cet appareil. Windows Hello peut aussi autoriser l’utilisation d’une clé de connexion pour un service compatible.

Le visage demande une caméra compatible Windows Hello, généralement avec des capacités infrarouges. Une webcam ordinaire ne suffit pas automatiquement. L’empreinte demande un lecteur compatible. Si le matériel n’est pas présent, le code PIN reste une méthode disponible selon la configuration.

### Pourquoi le code PIN est différent d’un mot de passe en ligne

Le PIN Windows Hello est lié à l’utilisateur sur un appareil donné. Il sert à autoriser localement l’utilisation des éléments d’authentification. Il n’est pas transmis au site Web comme le mot de passe du compte. Un attaquant qui apprend ce PIN ne peut donc pas simplement le saisir sur le site du fournisseur pour ouvrir le compte depuis n’importe quel ordinateur.

Cela ne rend pas le PIN sans importance. Une personne qui possède à la fois l’appareil et son PIN dispose d’un avantage important. On choisit donc un PIN difficile à deviner et on ne le partage pas. La protection dépend aussi du TPM, des limites de tentatives et de l’état du poste.

Le mot de passe du compte peut encore servir à d’autres opérations ou à la récupération. Activer Windows Hello ne supprime pas automatiquement tous les mots de passe associés à l’utilisateur. Le PIN de connexion Windows Hello ne doit pas non plus être confondu avec un PIN demandé par BitLocker avant le chargement de Windows.

### Ce que devient la biométrie

Windows Hello enregistre des données de référence permettant de reconnaître le visage ou l’empreinte sur l’appareil. Ces données biométriques restent locales au mécanisme Windows Hello; elles ne sont pas envoyées au site Web pour chaque connexion. Le site reçoit une preuve d’authentification adaptée au protocole utilisé, pas une photographie du visage.

Une vérification biométrique ne fonctionne pas toujours du premier coup : capteur sale, position du visage ou doigt mal placé peuvent gêner la reconnaissance. Une méthode de secours doit donc être prévue. Un échec de lecture n’indique pas nécessairement une panne du compte.

### Les facteurs d’authentification

| **Facteur**         | **Exemple**                                                              |
| ------------------- | ------------------------------------------------------------------------ |
| Ce que l’on connaît | Un mot de passe ou un code PIN.                                          |
| Ce que l’on possède | Un appareil ou une clé de sécurité contenant un élément cryptographique. |
| Ce que l’on est     | Une caractéristique biométrique, comme une empreinte.                    |

Deux secrets à mémoriser ne représentent pas forcément deux facteurs différents. En revanche, une clé liée à un appareil et déverrouillée par un PIN ou une empreinte peut combiner possession et vérification de l’utilisateur. Windows Hello for Business utilise ce principe dans un cadre géré par l’organisation.

Les options se trouvent dans `Paramètres > Comptes > Options de connexion`. Après configuration, le raccourci Windows + L permet de verrouiller la session. Windows Hello protège la reprise de session; il ne remplace pas les permissions sur les fichiers.

## Les passkeys et la connexion aux services

### Une clé d’accès propre au service

Une passkey, appelée aussi clé d’accès, permet de s’authentifier auprès d’un site ou d’une application compatible sans lui fournir un mot de passe réutilisable. Elle repose sur une paire de clés : une clé publique enregistrée par le service et une clé privée conservée par le dispositif ou le gestionnaire de passkeys.

La clé publique peut vérifier une preuve produite avec la clé privée. Elle ne permet pas, à elle seule, de fabriquer cette preuve. Le fonctionnement exact utilise des opérations cryptographiques; pour commencer, retenez surtout que le service n’a pas besoin de recevoir la clé privée.

### Le déroulement simplifié d’une connexion

1. L’utilisateur choisit la connexion par passkey sur le véritable site du service.
2. Le service envoie un défi, c’est-à-dire une donnée à utiliser pour cette tentative de connexion.
3. Le dispositif demande une vérification locale, par exemple le PIN Windows Hello, le visage ou l’empreinte.
4. La clé privée sert à signer une réponse adaptée au défi et au service. La réponse est transmise au site.
5. Le service vérifie cette réponse avec la clé publique enregistrée et accepte la connexion si les contrôles réussissent.

Le PIN ou la biométrie autorise l’utilisation de la passkey; ce n’est pas la passkey elle-même. De même, Windows Hello est une méthode locale de vérification, tandis qu’une passkey est un moyen d’authentification auprès d’un service. Les deux peuvent fonctionner ensemble.

### Pourquoi cette méthode résiste à l’hameçonnage

Une passkey est liée au service pour lequel elle a été créée. Une fausse page hébergée sur un autre domaine ne peut pas simplement réutiliser cette passkey comme un mot de passe saisi dans un formulaire. Le défi change également d’une connexion à l’autre, ce qui évite de réutiliser une ancienne réponse comme un secret permanent.

Cette résistance ne supprime pas tous les risques. Un poste déjà compromis, une session détournée ou une procédure de récupération mal protégée peuvent encore poser problème. Il faut aussi vérifier les demandes de connexion que l’on approuve.

### Où la passkey peut être conservée

| **Emplacement**                           | **Conséquence pratique**                                                                                 |
| ----------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| Windows Hello sur le poste                | La passkey liée à l’appareil reste sur celui-ci. Elle n’est pas automatiquement copiée vers un autre PC. |
| Clé de sécurité physique                  | La clé conserve l’élément privé. Il faut disposer de ce matériel pour l’utiliser.                        |
| Gestionnaire qui synchronise les passkeys | La disponibilité sur plusieurs appareils dépend du fournisseur, de sa protection et de sa récupération.  |
| Téléphone compatible                      | Il peut autoriser une connexion sur un autre appareil, selon le service et le parcours proposé.          |

Avant de changer d’ordinateur, vérifiez où vos passkeys sont enregistrées et prévoyez un autre moyen d’accès autorisé. Perdre l’unique appareil qui conserve une passkey peut compliquer la récupération. Sous Windows 11 compatible, les clés gérées par Windows se consultent dans `Paramètres > Comptes > Clés d’accès`; d’autres sont gérées chez leur fournisseur.

## La stratégie de sécurité locale

### Des règles appliquées par le poste

Une stratégie de sécurité regroupe des règles que Windows applique. Elle définit notamment les exigences de mot de passe, le verrouillage des comptes, les événements à enregistrer et les droits des utilisateurs.

Le mot « locale » indique que l’on travaille avec les règles du poste. Cela ne signifie pas que ces règles contrôlent tous les comptes et tous les services accessibles depuis cet ordinateur. Le mot de passe d’un site Web, par exemple, dépend des règles de ce site.

### Ouvrir la console

La commande `secpol.msc` ouvre la console Stratégie de sécurité locale sur les éditions qui la proposent, notamment Windows 11 Pro, Entreprise et Éducation. La modification des règles demande des droits administratifs. L’édition Famille ne fournit pas cette console; certaines protections existent quand même avec leurs paramètres par défaut ou d’autres interfaces.

La commande gpedit.msc ouvre un éditeur plus large, avec des réglages de Windows et de ses composants. secpol.msc se concentre sur la sécurité. Ces deux consoles ne présentent donc pas exactement les mêmes paramètres.

### Les principales rubriques

| **Rubrique**                                | **À quoi elle sert**                                                                                             |
| ------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Stratégies de comptes — mots de passe       | Définir les exigences des mots de passe des comptes locaux.                                                      |
| Stratégies de comptes — verrouillage        | Limiter les échecs de connexion répétés.                                                                         |
| Stratégies locales — audit                  | Choisir les catégories d’événements de sécurité à enregistrer. Des sous-catégories existent dans l’audit avancé. |
| Stratégies locales — attribution des droits | Définir qui peut effectuer certaines opérations, par exemple ouvrir une session à distance.                      |
| Stratégies locales — options de sécurité    | Régler certains comportements de connexion, de contrôle de compte et de sécurité du système.                     |

### Un poste personnel et un poste géré ne réagissent pas toujours pareil

Dans une organisation, des règles peuvent arriver d’un domaine Active Directory ou d’un service de gestion des appareils. Un domaine regroupe notamment des comptes et des ordinateurs sous une administration commune. Une règle imposée par l’organisation peut prendre le dessus sur un réglage local ou empêcher sa modification.

Un paramètre grisé ou une mention « géré par votre organisation » demande donc une vérification du contexte. Modifier une stratégie locale ne permet pas de contourner une règle centrale. Les règles de mot de passe d’un compte de domaine sont aussi administrées au niveau approprié du domaine.

### Éviter une confusion fréquente

Le droit d’ouvrir une session et la permission de lire un fichier sont deux choses différentes. Le premier concerne une opération du système. La seconde dépend des permissions sur le fichier ou le dossier, souvent appelées permissions NTFS. Une personne peut réussir sa connexion et se voir refuser l’accès à un dossier.

Effectuez les modifications sur la machine prévue pour le cours : une règle incorrecte peut empêcher une connexion ou gêner un service.

## Les mots de passe et le verrouillage des comptes

### Des mots de passe longs et difficiles à deviner

Une phrase de passe utilise plusieurs mots pour créer un secret long, plus facile à retenir qu’une suite aléatoire très courte. Elle doit rester difficile à deviner : le nom de l’école, une date connue ou une citation populaire ne deviennent pas solides simplement parce qu’ils sont longs. Chaque compte important doit avoir un secret différent.

Les stratégies imposent des exigences minimales. Elles ne garantissent pas la qualité des choix : un mot de passe conforme peut rester prévisible.

| **Paramètre**                     | **Sens et limite**                                                                                           |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| Longueur minimale                 | Nombre minimal de caractères. La valeur 14 sert ici d’exemple pour le cours, pas de règle universelle.       |
| Historique des mots de passe      | Empêche de réutiliser certains mots de passe précédents.                                                     |
| Exigences de complexité           | Contraintes de composition et de nom. Elles complètent la longueur sans éliminer tous les choix prévisibles. |
| Durée de vie minimale ou maximale | Encadre la fréquence des changements selon la politique de l’organisation.                                   |

Une nouvelle règle de composition est normalement vérifiée lors de la création ou du changement du mot de passe. Elle ne transforme pas automatiquement les mots de passe déjà enregistrés. Ces paramètres ne sont pas les règles du PIN Windows Hello et ne changent pas les mots de passe de vos sites Web.

### Limiter les essais répétés

Une attaque par force brute essaie un grand nombre de possibilités. Le verrouillage de compte ralentit ce type d’essai en refusant temporairement de nouvelles tentatives sur le compte visé. Il faut distinguer ce verrouillage du raccourci Windows + L, qui verrouille seulement la session ouverte.

| **Paramètre**                | **Exemple pédagogique**                                                                                |
| ---------------------------- | ------------------------------------------------------------------------------------------------------ |
| Seuil de verrouillage        | 10 échecs de connexion déclenchent le verrouillage du compte concerné.                                 |
| Réinitialisation du compteur | Après 15 minutes sans nouvel échec, le compteur peut repartir de zéro si le seuil n’a pas été atteint. |
| Durée du verrouillage        | Le compte reste verrouillé pendant 15 minutes une fois le seuil atteint.                               |

&#x20;

Ces valeurs illustrent le fonctionnement; elles ne constituent pas une règle universelle à appliquer partout. La durée du verrouillage doit être cohérente avec la remise à zéro du compteur. Windows vérifie certaines dépendances entre les paramètres.

### Un exemple pour interpréter la situation

Avec les valeurs du tableau, trois mots de passe incorrects ne verrouillent pas encore le compte. Si dix échecs surviennent avant la remise à zéro du compteur, le compte atteint le seuil. La personne peut ensuite connaître le bon mot de passe et devoir quand même attendre la fin du verrouillage ou l’intervention autorisée d’un administrateur.

Un seuil trop bas provoque des blocages après de simples erreurs de frappe. Un attaquant peut aussi provoquer des échecs pour bloquer volontairement un compte. Il faut donc limiter les attaques tout en conservant un accès raisonnable pour les utilisateurs. Ne testez pas ce mécanisme avec votre seul compte administrateur.

## Les mots de passe et le verrouillage des comptes

### Des mots de passe longs et difficiles à deviner

Une phrase de passe utilise plusieurs mots pour créer un secret long, plus facile à retenir qu’une suite aléatoire très courte. Elle doit rester difficile à deviner : le nom de l’école, une date connue ou une citation populaire ne deviennent pas solides simplement parce qu’ils sont longs. Chaque compte important doit avoir un secret différent.

Les stratégies imposent des exigences minimales. Elles ne garantissent pas la qualité des choix : un mot de passe conforme peut rester prévisible.

| Paramètre                         | Sens et limite                                                                                               |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| Longueur minimale                 | Nombre minimal de caractères. La valeur 14 sert ici d’exemple pour le cours, pas de règle universelle.       |
| Historique des mots de passe      | Empêche de réutiliser certains mots de passe précédents.                                                     |
| Exigences de complexité           | Contraintes de composition et de nom. Elles complètent la longueur sans éliminer tous les choix prévisibles. |
| Durée de vie minimale ou maximale | Encadre la fréquence des changements selon la politique de l’organisation.                                   |

&#x20;

Une nouvelle règle de composition est normalement vérifiée lors de la création ou du changement du mot de passe. Elle ne transforme pas automatiquement les mots de passe déjà enregistrés. Ces paramètres ne sont pas les règles du PIN Windows Hello et ne changent pas les mots de passe de vos sites Web.

### Limiter les essais répétés

Une attaque par force brute essaie un grand nombre de possibilités. Le verrouillage de compte ralentit ce type d’essai en refusant temporairement de nouvelles tentatives sur le compte visé. Il faut distinguer ce verrouillage du raccourci Windows + L, qui verrouille seulement la session ouverte.

| **Paramètre**                | Exemple pédagogique                                                                                    |
| ---------------------------- | ------------------------------------------------------------------------------------------------------ |
| Seuil de verrouillage        | 10 échecs de connexion déclenchent le verrouillage du compte concerné.                                 |
| Réinitialisation du compteur | Après 15 minutes sans nouvel échec, le compteur peut repartir de zéro si le seuil n’a pas été atteint. |
| Durée du verrouillage        | Le compte reste verrouillé pendant 15 minutes une fois le seuil atteint.                               |

Ces valeurs illustrent le fonctionnement; elles ne constituent pas une règle universelle à appliquer partout. La durée du verrouillage doit être cohérente avec la remise à zéro du compteur. Windows vérifie certaines dépendances entre les paramètres.

### Un exemple pour interpréter la situation

Avec les valeurs du tableau, trois mots de passe incorrects ne verrouillent pas encore le compte. Si dix échecs surviennent avant la remise à zéro du compteur, le compte atteint le seuil. La personne peut ensuite connaître le bon mot de passe et devoir quand même attendre la fin du verrouillage ou l’intervention autorisée d’un administrateur.

Un seuil trop bas provoque des blocages après de simples erreurs de frappe. Un attaquant peut aussi provoquer des échecs pour bloquer volontairement un compte. Il faut donc limiter les attaques tout en conservant un accès raisonnable pour les utilisateurs. Ne testez pas ce mécanisme avec votre seul compte administrateur.

## Comprendre les droits et consulter les journaux

### Le contrôle de compte d’utilisateur

Le contrôle de compte d’utilisateur, ou UAC, intervient lorsqu’une opération demande une élévation des droits. Par exemple, un installateur qui doit modifier des parties protégées du système peut déclencher une demande. Avec un compte standard, des identifiants administratifs peuvent être nécessaires; avec un compte administrateur, une confirmation peut être demandée, selon les règles du poste.

La fenêtre UAC indique notamment quel programme demande l’élévation et peut afficher son éditeur. Accepter donne des droits supplémentaires à cette opération. Cela ne prouve pas que le programme est sûr. Si la demande arrive sans action de votre part, vérifiez sa cause avant de l’approuver.

### Attribuer seulement les droits nécessaires

Un droit utilisateur autorise une opération du système, par exemple une ouverture de session locale ou à distance. Ajouter une personne au groupe Administrateurs lui donne un ensemble de pouvoirs beaucoup plus large que l’accès à un seul dossier. Ce n’est donc pas une solution à utiliser pour chaque problème de permission.

Certaines règles de refus ont priorité sur une autorisation correspondante. Une modification mal préparée peut exclure les personnes qui doivent administrer le poste. Avant un essai, relevez la valeur actuelle, conservez un moyen de récupération et changez un seul élément à la fois.

### L’audit laisse des traces

L’audit enregistre des événements utiles pour comprendre ce qui s’est produit. Une règle d’audit peut viser les réussites, les échecs ou les deux. Elle n’empêche pas directement l’action : elle produit des traces lorsque les conditions prévues sont réunies.

L’Observateur d’événements, ouvert avec eventvwr.msc, regroupe ces journaux. Les événements de sécurité se trouvent dans Journaux Windows > Sécurité. Leur consultation peut nécessiter des droits supplémentaires. Le nombre et le type d’événements présents dépendent des stratégies d’audit actives.

| **Événement** | **Ce qu’il peut indiquer**                                                                     |
| ------------- | ---------------------------------------------------------------------------------------------- |
| 4624          | Une ouverture de session réussie. Elle peut être locale, réseau ou d’un autre type.            |
| 4625          | Un échec d’ouverture de session. Il faut consulter le compte, la source et la raison indiquée. |
| 4740          | Le verrouillage d’un compte, sur le système qui traite l’événement concerné.                   |

Un numéro ne suffit pas pour conclure à une intrusion. Relevez l’heure, le compte concerné, le type de connexion et, lorsqu’elle est disponible, l’origine de la demande. Un ancien mot de passe enregistré dans une application peut produire plusieurs échecs sans qu’une personne soit en train de deviner le mot de passe.

L’audit avancé permet un choix plus précis des événements. On évite de mélanger des réglages d’audit de base et avancés sans comprendre leurs interactions. Dans un cours d’introduction, observez d’abord la configuration fournie et les événements qu’elle produit.

### Le verrouillage après une période d’inactivité

Une stratégie peut aussi verrouiller la session après une période d’inactivité. Par exemple, une limite de 900 secondes correspond à 15 minutes. La valeur adaptée dépend de l’usage du poste. Cette mesure réduit l’exposition d’une session oubliée, mais ne ferme pas les applications. Le volume BitLocker déjà accessible à Windows reste déverrouillé.

## Choisir la protection selon la situation

### Une même situation demande souvent plusieurs mesures

Léa prépare des postes portables pour une salle de cours. Les étudiants devront ouvrir une session, télécharger des outils et travailler sur des documents. Aucun réglage ne couvre tous les problèmes possibles. Il faut relier chaque protection au problème qu’elle traite.

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Situation</strong></td><td><strong>Protection utile et raisonnement</strong></td></tr><tr><td>Un portable éteint est perdu dans le transport.</td><td>BitLocker protège les données du volume contre une lecture hors ligne. La clé de récupération doit être conservée séparément.</td></tr><tr><td>Un composant de démarrage a été remplacé.</td><td>Secure Boot contrôle les signatures de démarrage; les mesures associées au TPM peuvent modifier les conditions de déverrouillage de BitLocker.</td></tr><tr><td>Un site annonce une fausse mise à jour urgente.</td><td>SmartScreen peut signaler le site ou le téléchargement. L’utilisateur vérifie aussi la source et passe par le site officiel ou le mécanisme de mise à jour prévu.</td></tr><tr><td>Une application tente de chiffrer les documents ouverts.</td><td>Defender et les autres protections contre les applications malveillantes peuvent intervenir. Les sauvegardes restent nécessaires pour récupérer les données.</td></tr><tr><td>Une fausse page imite le service de messagerie.</td><td>Une passkey liée au véritable service résiste à la récupération d’un secret réutilisable sur un autre domaine.</td></tr><tr><td>On veut observer un nouvel installateur officiel.</td><td>Sandbox fournit un environnement temporaire. On limite les échanges et on vérifie ce qui pourrait sortir de cet environnement.</td></tr><tr><td>Des échecs de connexion se répètent.</td><td>Les règles de verrouillage peuvent limiter les essais. L’audit aide à rechercher l’heure, le compte et l’origine des échecs.</td></tr></tbody></table>

### Les habitudes qui restent nécessaires

Installez les mises à jour prévues, utilisez un compte standard pour le travail courant et verrouillez la session quand vous quittez le poste. Téléchargez les applications depuis des sources reconnues et prenez le temps de lire les demandes de droits.

Conservez des sauvegardes adaptées aux documents importants et vérifiez qu’une restauration est possible. Une sauvegarde constamment accessible en écriture peut elle aussi être endommagée par un logiciel malveillant. Le chiffrement et la sauvegarde répondent à des besoins différents : empêcher une lecture non autorisée et retrouver une copie utilisable.

## Références&#x20;

### Démarrage sécurisé

[Protection du démarrage de Windows](https://learn.microsoft.com/en-us/windows/security/operating-system-security/system-security/secure-the-windows-10-boot-process)

[Présentation du module de plateforme sécurisée TPM](https://learn.microsoft.com/en-us/windows/security/hardware-security/tpm/trusted-platform-module-overview)

### BitLocker et récupération

[Présentation de BitLocker](https://learn.microsoft.com/en-us/windows/security/operating-system-security/data-protection/bitlocker/)

[Questions fréquentes sur BitLocker](https://learn.microsoft.com/en-us/windows/security/operating-system-security/data-protection/bitlocker/faq)

[Chiffrement de l’appareil dans Windows](https://support.microsoft.com/en-us/windows/security/encryption/device-encryption-in-windows)

[Retrouver une clé de récupération BitLocker](https://support.microsoft.com/en-us/windows/security/encryption/find-your-bitlocker-recovery-key)

### Antivirus et contrôle des applications

[Protection contre les virus et les menaces dans Sécurité Windows](https://support.microsoft.com/en-us/windows/security/threat-malware-protection/virus-and-threat-protection-in-the-windows-security-app)

[Choisir une analyse Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/run-scan-microsoft-defender-antivirus)

[Présentation de Microsoft Defender SmartScreen](https://learn.microsoft.com/en-us/windows/security/operating-system-security/virus-and-threat-protection/microsoft-defender-smartscreen/)

[Smart App Control — fonctionnement et conditions d’activation](https://support.microsoft.com/en-us/windows/security/threat-malware-protection/smart-app-control-frequently-asked-questions)

### Windows Hello et passkeys

[Questions fréquentes sur Windows Hello for Business](https://learn.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/faq)

[Fonctionnement de Windows Hello for Business](https://learn.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/how-it-works)

[Présentation des passkeys sous Windows](https://learn.microsoft.com/en-us/windows/security/identity-protection/passkeys/)

### Stratégies locales et journaux

[Configurer les paramètres de stratégie de sécurité](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/security-policy-settings/how-to-configure-security-policy-settings)

[Seuil de verrouillage d’un compte](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/security-policy-settings/account-lockout-threshold)

[Présentation du contrôle de compte d’utilisateur UAC](https://learn.microsoft.com/en-us/windows/security/application-security/application-control/user-account-control/)

[Événement 4624 — ouverture de session réussie](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/auditing/event-4624)

[Événement 4625 — échec de connexion](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/auditing/event-4625)

[Événement 4740 — verrouillage d’un compte](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/auditing/event-4740)
