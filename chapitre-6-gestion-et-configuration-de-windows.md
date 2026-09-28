---
description: Windows 11 • Interface graphique
---

# Chapitre 6 - Gestion et configuration de Windows

## Objectifs d'apprentissage&#x20;

* Repérer les éléments du Bureau, organiser les fichiers et relever les caractéristiques du poste.
* Comprendre les comptes, les groupes, les privilèges et les autorisations d’accès.
* Partager un dossier et y accéder à partir d’un autre ordinateur.
* Consulter les événements de Windows et créer une tâche planifiée simple.
* Choisir une source d’installation fiable, installer ou retirer une application

## Interface graphique et généralités

### Le rôle de Windows

Windows est un système d’exploitation. Il permet aux applications d’utiliser le processeur, la mémoire, les disques et les autres composants de l’ordinateur. Il gère aussi les utilisateurs et l’accès aux ressources.

Lorsque vous ouvrez un document, plusieurs éléments travaillent ensemble. Windows trouve le fichier, lance l’application associée et lui donne accès aux ressources nécessaires. Vous voyez une fenêtre à l’écran, mais le système effectue plusieurs opérations en arrière-plan.

L’interface graphique regroupe les fenêtres, les menus, les boutons et les icônes que vous utilisez avec la souris et le clavier. Elle donne accès aux fonctions de Windows sans devoir connaître des commandes.

### Le Bureau et les applications

#### Les principaux éléments de la session

Le Bureau est l’espace de travail affiché après l’ouverture de session. Il peut contenir des fichiers, des dossiers et des raccourcis. Un Bureau chargé n’est pas un système de classement : mieux vaut ranger les documents de cours dans des dossiers faciles à retrouver.

Le menu Démarrer sert à chercher et à ouvrir des applications. Vous pouvez aussi y retrouver les options du compte et les commandes d’alimentation. La barre des tâches donne accès aux applications épinglées ou ouvertes. La zone située près de l’horloge présente notamment le réseau, le son et les notifications.

Un clic sur une icône épinglée ouvre l’application ou ramène sa fenêtre au premier plan. Une application peut avoir plusieurs fenêtres. À l’inverse, plusieurs onglets d’un navigateur peuvent se trouver dans une seule fenêtre.

<figure><img src=".gitbook/assets/image (132).png" alt=""><figcaption><p>Les éléments du Bureau permettent de lancer des applications et de retrouver les fenêtres ouvertes.</p></figcaption></figure>

#### Fichier application et raccourci

Une application est un logiciel qui accomplit une tâche : rédiger, naviguer sur Internet, lire une image ou gérer des fichiers. Un fichier contient des données, par exemple le texte d’un travail ou une photo. Un raccourci est un lien vers un autre élément.

Si vous supprimez le raccourci de Word sur le Bureau, Word reste installé. Si vous supprimez votre travail Word, vous supprimez le document. Et si vous désinstallez Word, vous retirez l’application. Ces trois actions ont des conséquences différentes.

Pour ouvrir une application, cliquez sur Démarrer et tapez son nom. Pour ouvrir un fichier, double-cliquez dessus dans l’Explorateur. Windows utilise alors l’application associée au type de fichier. Avec Ouvrir avec, vous pouvez choisir une autre application compatible.

#### Manipuler les fenêtres

Les boutons en haut à droite permettent de réduire, d’agrandir ou de fermer une fenêtre. Réduire la fenêtre laisse généralement l’application en fonctionnement. Fermer une fenêtre n’arrête pas toujours tous les processus de l’application : certains logiciels continuent de fonctionner en arrière-plan.

Pour travailler avec deux fenêtres, utilisez Windows + flèche gauche sur la première, puis placez la seconde à droite. Alt + Tab permet de passer d’une fenêtre à une autre.

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Raccourci</strong></td><td><strong>Utilité</strong></td></tr><tr><td>Windows + E</td><td>Ouvrir l’Explorateur de fichiers.</td></tr><tr><td>Windows + I</td><td>Ouvrir les Paramètres.</td></tr><tr><td>Windows + L</td><td>Verrouiller la session.</td></tr><tr><td>Alt + Tab</td><td>Changer de fenêtre active.</td></tr><tr><td>Ctrl + Maj + Échap</td><td>Ouvrir le Gestionnaire des tâches.</td></tr><tr><td>Windows + Maj + S</td><td>Capturer une partie de l’écran.</td></tr></tbody></table>

&#x20;

**Verrouiller et se déconnecter**. Le verrouillage conserve la session et les applications ouvertes, mais demande de s’authentifier pour reprendre le travail. La déconnexion ferme la session. Enregistrez vos documents avant de vous déconnecter. Au laboratoire, verrouillez votre poste lorsque vous vous absentez.

#### Paramètres et Panneau de configuration

Les Paramètres regroupent les réglages courants : affichage, réseau, comptes, applications et mises à jour. Le Panneau de configuration donne encore accès à certains réglages plus anciens. Il est donc normal de rencontrer les deux interfaces. Commencez par les Paramètres ou cherchez directement le nom du réglage dans Démarrer.

### Comprendre les fichiers et leur emplacement

#### Lire un chemin

L’Explorateur de fichiers permet de parcourir les emplacements de stockage. Ouvrez-le avec Windows + E. Le volet de gauche donne accès aux dossiers et aux lecteurs. La barre d’adresse indique l’emplacement actuel. La zone centrale affiche son contenu.

Un dossier sert à regrouper des fichiers et d’autres dossiers. Un dossier placé dans un autre est un sous-dossier. L’organisation ressemble à une arborescence : on part d’un emplacement général pour aller vers un emplacement plus précis.

Considérons ce chemin :

`C:\CoursWindows\Documents\rapport.txt`

C: désigne un lecteur. Le premier antislash marque sa racine. CoursWindows, puis Documents, sont les dossiers traversés. rapport.txt est le fichier. Le chemin complet répond à la question : « Où se trouve exactement ce fichier ? »

Une lettre de lecteur ne représente pas nécessairement un disque physique distinct. Un même disque peut contenir plusieurs volumes auxquels Windows attribue des lettres différentes. Un lecteur réseau peut lui aussi recevoir une lettre.

Pour afficher le chemin sous forme de texte, cliquez dans la barre d’adresse. Vous pouvez le copier pour le transmettre à quelqu’un. Deux fichiers portant le même nom peuvent se trouver à des endroits différents : leur chemin permet de les distinguer.

<figure><img src=".gitbook/assets/image (133).png" alt=""><figcaption><p>Le chemin indique l’emplacement du fichier dans l’arborescence.</p></figcaption></figure>

#### Les emplacements courants

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Emplacement</strong></td><td><strong>Ce que l’on y trouve généralement</strong></td></tr><tr><td>C:\Windows</td><td>Les fichiers nécessaires au fonctionnement de Windows.</td></tr><tr><td>C:\Program Files</td><td>De nombreuses applications installées pour le poste.</td></tr><tr><td>C:\Program Files (x86)</td><td>De nombreuses applications 32 bits sur un Windows x64.</td></tr><tr><td>C:\Users</td><td>Les dossiers de profils des utilisateurs, parfois affichés sous le nom Utilisateurs.</td></tr><tr><td>Documents et Images</td><td>Des emplacements destinés aux documents personnels et aux images.</td></tr><tr><td>Téléchargements</td><td>Les fichiers téléchargés, dont les programmes d’installation.</td></tr><tr><td>OneDrive</td><td>Des fichiers pouvant être synchronisés avec le service en ligne, selon la configuration.</td></tr></tbody></table>

Le profil utilisateur regroupe les réglages et les fichiers propres à une personne. Son dossier se trouve habituellement sous C:\Users. Le nom du dossier de profil n’est pas toujours identique au nom affiché dans le menu Démarrer.

Certains dossiers, comme Bureau ou Documents, peuvent être redirigés vers OneDrive. Un fichier visible dans l’Explorateur peut aussi être disponible uniquement en ligne. Vérifiez donc son emplacement et son état avant de supposer qu’il se trouve entièrement sur le disque local.

Les dossiers système ne sont pas des espaces de rangement. On ne déplace pas les fichiers de C:\Windows pour faire du ménage, et on ne retire pas une application en effaçant son dossier dans Program Files.

#### Le nom et l’extension

Dans rapport.txt, l’extension est .txt. Elle aide Windows à choisir l’application qui ouvrira le fichier. Pour l’afficher dans Windows 11, `ouvrez Afficher > Afficher > Extensions de noms de fichiers dans l’Explorateur`. Selon la version, le libellé est légèrement différent. <sup>\[1]</sup>

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Extension</strong></td><td><strong>Type de fichier courant</strong></td></tr><tr><td>.txt</td><td>Texte simple.</td></tr><tr><td>.docx</td><td>Document Word.</td></tr><tr><td>.pdf</td><td>Document PDF.</td></tr><tr><td>.png ou .jpg</td><td>Image.</td></tr><tr><td>.zip</td><td>Archive pouvant regrouper plusieurs fichiers.</td></tr><tr><td>.exe</td><td>Programme exécutable, parfois un programme d’installation.</td></tr><tr><td>.msi ou .msix</td><td>Paquet utilisé pour installer une application.</td></tr><tr><td>.lnk</td><td>Raccourci Windows dont l’extension peut rester masquée.</td></tr></tbody></table>

Changer l’extension ne convertit pas le fichier. Renommer une image .jpg en .pdf ne crée pas un document PDF. Pour changer réellement le format, il faut utiliser une fonction d’exportation ou de conversion adaptée.&#x20;

Afficher les extensions évite aussi certaines erreurs. Le fichier facture.pdf.exe est un exécutable dont le nom contient « .pdf ». Son apparence ou son nom ne suffit pas à établir qu’il s’agit d’une facture.

<figure><img src=".gitbook/assets/image (134).png" alt=""><figcaption><p>L’extension aide à reconnaître le type de fichier avant de l’ouvrir</p></figcaption></figure>

#### Copier déplacer renommer et supprimer

#### renommer et supprimer

Copier crée une deuxième version à l’endroit choisi. Déplacer change l’emplacement de l’élément. Pour éviter l’ambiguïté du glisser-déposer, utilisez Ctrl + C, puis Ctrl + V pour copier, ou Ctrl + X, puis Ctrl + V pour déplacer.

Pour renommer un élément sélectionné, appuyez sur F2. Choisissez un nom descriptif, par exemple Rapport\_labo\_02.txt. Si les extensions sont affichées, conservez la bonne extension.

La touche Suppr envoie généralement un fichier local dans la Corbeille. Ce comportement varie selon l’emplacement et la configuration. Sur un partage réseau ou certains supports amovibles, la suppression peut être immédiate. Maj + Suppr contourne la Corbeille. Une Corbeille ne remplace donc pas une sauvegarde.

Les Propriétés, accessibles par clic droit, donnent notamment le type, la taille et l’emplacement de l’élément. Elles sont utiles lorsqu’un fichier refuse de s’ouvrir ou lorsqu’on doit vérifier quel document a été sélectionné.

### Relever les informations du système

Avant d’installer un logiciel ou de chercher une panne, il faut connaître le poste. La phrase « j’ai Windows » ne donne pas assez de renseignements pour vérifier la compatibilité d’une application.

Ouvrez Paramètres > Système > Informations système, parfois nommé À propos. Relevez le nom du poste, le processeur, la mémoire installée, le type du système, l’édition de Windows et sa version.&#x20;

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Information</strong></td><td><strong>Ce qu’elle permet de comprendre</strong></td></tr><tr><td>Nom du poste</td><td>Identifier l’ordinateur concerné.</td></tr><tr><td>Processeur</td><td>Connaître le modèle du composant qui exécute les instructions.</td></tr><tr><td>Mémoire RAM</td><td>Connaître la capacité de travail disponible pour Windows et les applications.</td></tr><tr><td>Type du système</td><td>Repérer notamment une architecture x64 ou ARM64.</td></tr><tr><td>Édition de Windows</td><td>Distinguer Famille, Pro, Éducation ou Entreprise.</td></tr><tr><td>Version et build</td><td>Identifier la version précise du système pour le support et la compatibilité.</td></tr></tbody></table>

L’édition indique une gamme de fonctionnalités. La version situe Windows dans son évolution. Le numéro de build est un repère plus précis. Deux ordinateurs peuvent utiliser Windows 11 tout en ayant une édition ou une version différente.

<figure><img src=".gitbook/assets/image (135).png" alt=""><figcaption><p>Les caractéristiques du poste aident à vérifier la compatibilité et à préparer un diagnostic.</p></figcaption></figure>

#### Aller plus loin avec Informations système

Cherchez Informations système dans Démarrer, ou faites Windows + R, tapez msinfo32, puis validez. Cet outil présente des renseignements plus détaillés sur le matériel et l’environnement logiciel. <sup>\[3]</sup>

Dans Résumé système, repérez le fabricant, le modèle, le processeur, la mémoire et le mode BIOS. Une indication UEFI concerne la manière dont le micrologiciel et Windows démarrent le système. Il n’est pas nécessaire de modifier ce réglage pour le consulter.

Pour connaître l’espace libre, ouvrez Ce PC dans l’Explorateur ou `Paramètres > Système > Stockage.` Pour afficher rapidement la version de Windows, vous pouvez aussi lancer winver depuis la fenêtre Exécuter.

<figure><img src=".gitbook/assets/image (136).png" alt=""><figcaption><p>Informations système donne une vue détaillée de la configuration matérielle et logicielle.</p></figcaption></figure>

### Utiliser le Gestionnaire des tâches

Le Gestionnaire des tâches montre ce qui fonctionne et les ressources utilisées. Ouvrez-le avec Ctrl + Maj + Échap. Selon la version de Windows, ses rubriques apparaissent dans un menu latéral ou sous forme d’onglets.

#### Applications et processus

Un processus est un programme en cours d’exécution. Une application peut utiliser plusieurs processus. Un navigateur, par exemple, répartit souvent son travail entre plusieurs processus : il est donc normal de voir son nom apparaître plusieurs fois.

Dans Processus, observez les applications et les activités en arrière-plan. Cliquez sur l’en-tête d’une colonne pour trier les résultats. La colonne Processeur permet de repérer ce qui sollicite le CPU ; la colonne Mémoire indique la mémoire utilisée par les processus.

| Ressource         | Comment interpréter son utilisation                                            |
| ----------------- | ------------------------------------------------------------------------------ |
| Processeur ou CPU | Une valeur élevée indique beaucoup de travail à cet instant.                   |
| Mémoire           | Une forte occupation peut laisser moins de place aux nouvelles applications.   |
| Disque            | L’activité concerne les lectures et écritures, pas simplement l’espace occupé. |
| Réseau            | L’application envoie ou reçoit des données.                                    |

Un processeur à 100 % pendant quelques secondes n’est pas forcément en panne. L’installation d’une application ou le traitement d’une vidéo peut le solliciter fortement. On s’intéresse surtout à une utilisation persistante qui correspond au ralentissement observé.

<figure><img src=".gitbook/assets/image (137).png" alt=""><figcaption><p>Le tri permet de repérer les applications qui utilisent le plus une ressource.</p></figcaption></figure>

#### Fermer une application bloquée

Essayez d’abord de fermer l’application normalement. Si elle ne répond plus, sélectionnez-la dans le Gestionnaire des tâches et choisissez Fin de tâche. Les modifications non enregistrées peuvent être perdues.

Ne terminez pas un processus simplement parce que vous ne connaissez pas son nom. Certains sont indispensables à Windows. Pour une démonstration, utilisez une application connue et un document sans importance.

#### Lire les performances globales

La rubrique Performances présente les graphiques du processeur, de la mémoire, du disque et du réseau. Elle permet de suivre une évolution dans le temps. Une mesure prise au repos ne décrit pas forcément ce qui se passe pendant l’utilisation réelle du poste.

Sur la page du disque, 100 % de temps d’activité signifie que le disque est très occupé. Cela ne veut pas dire que sa capacité de stockage est pleine. Pour connaître l’espace libre, retournez dans Ce PC ou dans les paramètres de stockage.

<figure><img src=".gitbook/assets/image (138).png" alt=""><figcaption><p>La mémoire utilisée </p></figcaption></figure>

<figure><img src=".gitbook/assets/image (139).png" alt=""><figcaption><p> L'activité du disque décrivent le travail en cours</p></figcaption></figure>

#### Les applications au démarrage

Dans Applications de démarrage, vous pouvez empêcher certaines applications de se lancer à l’ouverture de session. Désactiver ce lancement ne désinstalle pas l’application : elle reste disponible dans Démarrer.&#x20;

Un logiciel de messagerie que l’on utilise rarement n’a peut-être pas besoin de s’ouvrir à chaque connexion. En revanche, on ne désactive pas les composants de sécurité ou les outils gérés par l’établissement sans en connaître le rôle.

<figure><img src=".gitbook/assets/image (140).png" alt=""><figcaption><p>Désactiver le démarrage automatique laisse l’application installée.</p></figcaption></figure>

## Comptes locaux et sécurité des accès

### Comprendre les comptes et les groupes

#### Un compte représente une identité

Un compte utilisateur permet à Windows d’identifier une personne ou un service. Lors de l’ouverture de session, Windows vérifie l’identité : c’est l’authentification. Ensuite, il détermine ce que ce compte peut faire : c’est l’autorisation.

Entrer le bon mot de passe ne donne donc pas accès à tous les fichiers. Vous pouvez ouvrir une session sur un ordinateur tout en n’ayant aucun droit sur le dossier d’un autre utilisateur.

Un compte local est créé et géré sur un ordinateur précis. Le compte POSTE01\lea appartient à POSTE01. Un autre compte appelé lea sur POSTE02 est une identité différente, même si son nom est identique.

Un compte Microsoft est lié aux services Microsoft en ligne. Un compte professionnel ou scolaire est géré par une organisation. Dans ce chapitre, nous travaillons surtout avec des comptes locaux pour voir clairement où se trouvent les identités et les permissions.

#### Utilisateur standard et administrateur

| **Type de compte**   | **Usage attendu**                                                                        |
| -------------------- | ---------------------------------------------------------------------------------------- |
| Utilisateur standard | Utiliser les applications autorisées et travailler sur les fichiers auxquels il a accès. |
| Administrateur       | Gérer le poste, ses comptes et les réglages qui exigent une élévation de privilèges.     |

Un utilisateur standard peut parfois installer une application uniquement dans son propre profil. Toutes les installations n’exigent donc pas les mêmes droits. Le besoin d’administration dépend du programme et des modifications effectuées.

Les droits d’administration donnent un pouvoir étendu sur la machine. Ils ne devraient pas être accordés simplement pour éviter un message d’erreur. Le rôle du technicien consiste à comprendre le besoin et à donner l’accès approprié.

#### Créer un compte local

Pour une démonstration dans les Paramètres :&#x20;

1\. `Ouvrez Paramètres > Comptes > Autres utilisateurs` avec un compte autorisé à gérer le poste.

2\. Choisissez Ajouter un compte.

3\. Sélectionnez Je ne dispose pas des informations de connexion de cette personne, puis Ajouter un utilisateur sans compte Microsoft.

4\. Créez le compte lea avec un mot de passe réservé au laboratoire et complétez les renseignements demandés.

5\. Vérifiez son type de compte. Pour le travail courant, conservez Utilisateur standard.

6\. Ouvrez une première session avec ce compte afin de créer son profil et de vérifier la connexion.

<figure><img src=".gitbook/assets/image (141).png" alt=""><figcaption><p>Un compte administrateur permet de travailler en disposant de tous les pouvoirs sur le poste.</p></figcaption></figure>

#### Pourquoi utiliser des groupes

Un groupe rassemble plusieurs comptes auxquels on veut attribuer les mêmes accès. Si dix employés doivent modifier un dossier, il est plus simple d’accorder l’autorisation à un groupe que de gérer dix autorisations séparées.

Dans notre exemple, le groupe G\_Lecture contient lea et le groupe G\_Modification contient samir. Les noms sont choisis pour rendre leur rôle compréhensible. Windows possède aussi des groupes intégrés, notamment Utilisateurs et Administrateurs.

L’appartenance à un groupe ne donne pas automatiquement accès à n’importe quel dossier. Le groupe doit recevoir une permission sur la ressource concernée. On peut résumer le raisonnement ainsi : un compte appartient à un groupe ; une permission accordée au groupe s’applique à ses membres.

#### Gérer les groupes dans la console locale

Sur Windows Pro, Éducation ou Entreprise, faites un clic droit sur Démarrer, puis ouvrez Gestion de l’ordinateur > Utilisateurs et groupes locaux. La commande lusrmgr.msc, lancée avec Windows + R, ouvre directement la console correspondante.

1. Ouvrez Groupes, puis choisissez Nouveau groupe dans le menu contextuel.
2. Nommez le groupe G\_Lecture et ajoutez une description simple.
3. Cliquez sur Ajouter, saisissez lea, puis utilisez Vérifier les noms. Vérifiez que la recherche concerne le bon ordinateur.
4. Créez le groupe G\_Modification et ajoutez le compte samir, créé comme utilisateur standard.
5. Après une modification de groupe, fermez puis rouvrez la session du compte concerné avant de refaire les tests d’accès.

Sur Windows Famille, l’absence de cette console ne signifie pas que les comptes locaux n’existent pas.&#x20;

<figure><img src=".gitbook/assets/image (142).png" alt=""><figcaption><p>Les groupes permettent d’attribuer les mêmes autorisations à plusieurs comptes.</p></figcaption></figure>

**Désactiver ou supprimer**. Un compte désactivé ne peut plus être utilisé pour ouvrir une session, mais son identité reste présente. La suppression retire le compte ; selon l’outil employé, elle peut aussi supprimer ses données locales. Avant de supprimer un compte, vérifiez les fichiers à conserver. Recréer ensuite le même nom ne recrée pas la même identité de sécurité.

### Le moindre privilège et le contrôle de compte utilisateur

#### Donner seulement les droits nécessaires

Le principe du moindre privilège consiste à donner les droits nécessaires à une tâche, sans ajouter de pouvoirs inutiles. Une personne qui consulte un horaire n’a pas besoin de pouvoir le supprimer. Une personne qui rédige un rapport n’a pas besoin de pouvoir créer des administrateurs.

Cette approche réduit les conséquences d’une erreur et limite ce qu’un logiciel malveillant peut faire avec le compte utilisé. Elle s’applique aux utilisateurs, aux applications, aux dossiers et aux tâches automatisées.

#### Comprendre une demande UAC

L’UAC, ou contrôle de compte utilisateur, intervient lorsqu’une opération demande des privilèges d’administration. Avec les réglages habituels, un administrateur voit une demande de confirmation ; un utilisateur standard doit fournir les identifiants d’un administrateur. Une politique de l’établissement peut modifier ce comportement.&#x20;

L’action Exécuter en tant qu’administrateur lance le programme avec des privilèges élevés après l’autorisation nécessaire. Cela ne transforme pas définitivement le compte standard en administrateur.

Même avec un compte administrateur, les applications courantes ne s’exécutent pas toutes avec les pleins pouvoirs. L’élévation concerne le programme lancé et les opérations effectuées dans ce contexte.&#x20;

Avant d’approuver une demande, vérifiez le nom du programme, son éditeur et l’action qui l’a provoquée. Si la demande apparaît sans raison claire, annulez et cherchez son origine. L’UAC ne vérifie pas à votre place que le logiciel est utile ou sans danger.

<figure><img src=".gitbook/assets/image (143).png" alt=""><figcaption><p>L’UAC demande une autorisation avant une opération nécessitant des privilèges élevés.</p></figcaption></figure>

### Les autorisations sur les fichiers et les dossiers

#### Ce que Windows contrôle

Une autorisation, souvent appelée permission, précise les actions qu’un compte ou un groupe peut effectuer sur une ressource. Sur un volume NTFS, Windows peut appliquer des permissions aux fichiers et aux dossiers. Une clé USB formatée en exFAT ne possède pas le même mécanisme de permissions NTFS.

Les permissions s’appliquent aussi lorsque la personne travaille directement sur le poste. Il n’est pas nécessaire de partager le dossier sur le réseau pour le protéger.

Ouvrez les Propriétés d’un dossier, puis l’onglet Sécurité. La partie supérieure présente des comptes et des groupes. La partie inférieure affiche leurs autorisations. L’ensemble de ces entrées forme une liste de contrôle d’accès, appelée ACL.&#x20;

#### Les permissions courantes

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Permission</strong></td><td><strong>Effet général</strong></td></tr><tr><td>Lecture</td><td>Consulter les fichiers et leurs propriétés.</td></tr><tr><td>Affichage du contenu du dossier</td><td>Voir les noms des éléments d’un dossier.</td></tr><tr><td>Lecture et exécution</td><td>Lire les fichiers et exécuter les programmes autorisés.</td></tr><tr><td>Écriture</td><td>Créer des éléments et écrire des données selon les droits applicables.</td></tr><tr><td>Modification</td><td>Lire, créer, modifier et supprimer les éléments concernés.</td></tr><tr><td>Contrôle total</td><td>Ajouter notamment la gestion des permissions et de la propriété aux droits de modification.</td></tr></tbody></table>

Écriture et Modification ne sont pas équivalentes. L’écriture seule ne comprend pas tous les droits nécessaires pour supprimer ou remplacer des fichiers. Certains logiciels enregistrent en créant un fichier temporaire, puis en remplaçant l’ancien. Pour une collaboration ordinaire, la permission Modification répond souvent mieux au besoin, mais elle permet aussi la suppression.

Le droit de supprimer un fichier peut dépendre de ses permissions et de celles de son dossier parent. Pour comprendre un résultat inattendu, il faut donc parfois regarder les deux niveaux.

<figure><img src=".gitbook/assets/image (144).png" alt=""><figcaption><p>Les permissions déterminent les actions permises sur le dossier</p></figcaption></figure>

#### Les permissions héritées

Un fichier ou un sous-dossier peut recevoir des permissions du dossier qui le contient. C’est l’héritage. Il évite de configurer chaque fichier séparément. Une permission ajoutée directement sur l’élément est une permission explicite.&#x20;

Par exemple, si le dossier Equipe transmet le droit de lecture à ses sous-dossiers et à ses fichiers, un nouveau document peut recevoir ce droit automatiquement. Dans `Sécurité > Avancé`, regardez les colonnes Hérité de et S’applique à.

Désactiver l’héritage demande un choix : convertir les permissions héritées en permissions explicites, ou les retirer. Retirer toutes les entrées sans les examiner peut supprimer des accès nécessaires.&#x20;

<figure><img src=".gitbook/assets/image (145).png" alt=""><figcaption><p>L’héritage transmet des permissions depuis le dossier parent.</p></figcaption></figure>

#### Les droits obtenus par plusieurs groupes

Un utilisateur peut appartenir à plusieurs groupes. Dans un cas simple sans refus, les permissions Autoriser se cumulent. Si Lea reçoit Lecture par un groupe et Modification par un autre, elle peut modifier : retirer une seule entrée Lecture ne supprimera pas cet accès.

Une entrée Refuser peut bloquer un droit obtenu ailleurs. L’ordre de traitement et l’héritage interviennent dans les cas plus complexes ; on ne se contente donc pas de regarder une seule case. Pour débuter, évitez les refus et accordez les accès avec des groupes bien choisis.

Une case Autoriser non cochée ne signifie pas nécessairement que l’accès est refusé. Un autre groupe peut donner ce droit. L’outil Accès effectif, lorsqu’il est disponible dans les paramètres avancés, aide à évaluer les droits NTFS d’un compte. Un essai avec le compte concerné reste nécessaire.

**Permissions et chiffrement**. Les permissions NTFS contrôlent l’accès lorsque Windows applique ces règles. Elles ne chiffrent pas le contenu. La protection contre la lecture d’un disque retiré du poste demande une solution de chiffrement adaptée.

### Partager un dossier sur le réseau

#### Le rôle du partage réseau

Un dossier partagé est un dossier auquel d’autres ordinateurs peuvent accéder par le réseau. Il permet, par exemple, à plusieurs employés de consulter le même horaire ou de travailler sur des documents communs.

Les fichiers restent sur l’ordinateur qui héberge le dossier. Les autres postes y accèdent à distance. Cela évite d’envoyer une nouvelle copie par courriel chaque fois qu’un document change. Le partage sur le réseau local ne rend pas automatiquement les fichiers accessibles sur Internet.&#x20;

L’ordinateur qui fournit les fichiers joue le rôle de serveur. Celui qui demande à les ouvrir joue le rôle de client. Dans ce contexte, un simple PC Windows peut servir de serveur de fichiers. Un serveur n’est donc pas nécessairement une machine d’un modèle particulier.

Les partages Windows utilisent généralement SMB, un protocole de communication. Un protocole est un ensemble de règles que les ordinateurs suivent pour échanger des données. Ici, ces échanges permettent notamment de lire un fichier ou d’enregistrer une modification.

#### Le chemin local et le chemin réseau

Un même dossier peut être désigné de deux façons, selon le poste depuis lequel on y accède. Sur POSTE01, le dossier Equipe se trouve, par exemple, à cet emplacement :

`C:\CoursWindows\Equipe`

Depuis un autre ordinateur, son adresse peut être :

`\\POSTE01\Equipe`

Cette adresse est un chemin réseau, aussi appelé chemin UNC. Les deux antislashs au début annoncent un emplacement réseau. POSTE01 désigne l’ordinateur qui héberge les fichiers et Equipe désigne le nom du partage. Le nom du partage peut être différent du nom du dossier sur le disque.

La barre d’adresse de l’Explorateur peut afficher ce chemin réseau. Le disque C: d’un autre ordinateur n’est pas le même que celui du poste utilisé : le nom du serveur permet de préciser où se trouvent les fichiers.

#### Les autorisations du partage

Le partage précise qui peut accéder au dossier et quelles actions sont permises par le réseau. Dans les propriétés d’un dossier, l’onglet Partage concerne l’accès réseau, alors que l’onglet Sécurité présente les permissions NTFS étudiées précédemment.

Les autorisations de partage portent généralement les noms Lecture, Modifier et Contrôle total. Lecture permet de consulter le contenu. Modifier permet aussi de créer, de changer et de supprimer des fichiers, si les permissions NTFS l’autorisent. Contrôle total ajoute notamment la possibilité de gérer les autorisations, sous réserve des autres droits applicables.

Lors d’un accès réseau, les permissions du partage et les permissions NTFS doivent toutes les deux autoriser l’action. Dans les cas simples ci-dessous, sans refus particulier ni autre droit accordé, le résultat correspond à l’accès le plus limité.

| **Partage** | **NTFS**             | **Accès par le réseau**                         |
| ----------- | -------------------- | ----------------------------------------------- |
| Lecture     | Modification         | Lecture seulement.                              |
| Modifier    | Lecture et exécution | Lecture seulement.                              |
| Modifier    | Modification         | Lecture, création, modification et suppression. |
| Lecture     | Aucun accès          | Accès refusé.                                   |

&#x20;

Par exemple, Samir peut avoir le droit de modifier un document lorsqu’il travaille directement sur POSTE01, mais seulement le droit de le lire depuis un autre poste. Cela peut arriver si ses permissions NTFS permettent la modification, alors que ses permissions de partage permettent uniquement la lecture.

<figure><img src=".gitbook/assets/image (146).png" alt=""><figcaption><p>Les permissions du partage s’ajoutent aux permissions NTFS pour contrôler l’accès par le réseau.</p></figcaption></figure>

#### Les conditions nécessaires pour accéder au dossier

L’ordinateur qui héberge les fichiers doit être allumé et joignable sur le réseau. Le partage de fichiers doit être autorisé et le pare-feu doit laisser passer les communications nécessaires. Le pare-feu est le composant qui filtre les communications entrantes et sortantes du poste.

Dans Windows, le profil Privé convient à un réseau connu et de confiance. Le profil Public est prévu pour un réseau moins fiable, comme celui d’un lieu public. Ce choix influence les règles de communication. La découverte réseau facilite l’affichage des autres postes dans l’Explorateur, mais un chemin réseau connu peut aussi être utilisé directement.

Un partage protégé demande une identité reconnue par l’ordinateur qui héberge les fichiers. Par exemple, POSTE01\lea désigne le compte local lea de POSTE01. Le mot de passe de ce compte et le code confidentiel Windows Hello utilisé sur un autre poste sont deux choses différentes.

Le partage protégé par mot de passe permet de réserver l’accès à des comptes identifiés. Une difficulté de connexion peut venir du réseau, du compte ou des permissions. Désactiver complètement le pare-feu ou donner tous les droits ne permet pas de distinguer ces causes.

### Connecter un lecteur réseau

#### Une lettre pour retrouver un dossier partagé

Un lecteur réseau associe une lettre à un dossier partagé. Par exemple, la lettre Z: peut représenter le partage suivant :

`Z:  correspond à  \\POSTE01\Equipe`

Cette association s’appelle le mappage. Elle fait apparaître le dossier dans Ce PC et facilite son utilisation. Pour l’utilisateur, ouvrir Z: revient à ouvrir le partage auquel cette lettre est associée.&#x20;

Le mappage ne copie pas les fichiers sur le poste et ne crée pas un nouveau disque physique. Il ne donne pas non plus de droits supplémentaires : une personne limitée à la lecture reste limitée à la lecture, même si le partage porte maintenant la lettre Z:.

La fenêtre Connecter un lecteur réseau réunit la lettre choisie et le chemin du dossier. L’option de reconnexion permet à Windows de tenter de retrouver ce lecteur à la prochaine ouverture de session. Une autre option permet d’utiliser un compte différent pour accéder au partage.

<figure><img src=".gitbook/assets/image (147).png" alt=""><figcaption><p>Comment connecter un lecteur réseau</p></figcaption></figure>

#### La disponibilité du lecteur réseau

Un lecteur réseau dépend de la connexion et de l’ordinateur qui héberge les fichiers. Si ce dernier est éteint ou si le réseau est coupé, le lecteur peut apparaître comme indisponible. La lettre est toujours connue de Windows, mais sa destination n’est plus accessible.

Déconnecter le lecteur retire l’association avec la lettre sur le poste client. Les fichiers restent dans le dossier partagé. En revanche, supprimer un fichier à l’intérieur du lecteur agit sur le fichier distant, si le compte possède ce droit.

| **Message ou situation**               | **Ce que cela peut indiquer**                                               |
| -------------------------------------- | --------------------------------------------------------------------------- |
| Chemin introuvable                     | Le nom du partage est incorrect, ou le poste distant n’est pas joignable.   |
| Identifiants refusés                   | Le compte ou le mot de passe n’est pas reconnu par le poste distant.        |
| Lecture possible, modification refusée | Les permissions permettent peut-être la lecture seulement.                  |
| Accès avec un compte inattendu         | Windows peut réutiliser une connexion ou des identifiants déjà enregistrés. |

## Outils pour observer et automatiser

### Consulter les événements de Windows

#### Les journaux et les événements

Windows et les applications conservent des traces de certaines activités : démarrage d’un service, installation, erreur ou connexion d’un utilisateur. Chaque trace enregistrée constitue un événement. Un journal regroupe ces événements.

L’Observateur d’événements est l’outil qui permet de lire ces journaux. Il aide à comprendre ce qui s’est passé, même lorsque le message d’erreur a disparu de l’écran. Il est accessible par la recherche du menu Démarrer. La commande eventvwr.msc désigne le même outil.&#x20;

Les journaux ne constituent pas un enregistrement de tous les gestes de l’utilisateur. Le contenu dépend de ce que Windows et les logiciels sont configurés pour enregistrer. Un service, par exemple, est un programme qui fonctionne en arrière-plan pour fournir une fonction au système.

#### Les principaux journaux

| **Journal**                               | **Renseignements habituels**                                                     |
| ----------------------------------------- | -------------------------------------------------------------------------------- |
| Application                               | Événements produits par des logiciels, comme certaines erreurs ou installations. |
| Système                                   | Événements liés au fonctionnement de Windows, aux services et aux pilotes.       |
| Sécurité                                  | Événements de sécurité, selon les règles de surveillance activées.               |
| Installation                              | Événements liés à l’installation et à la configuration de composants Windows.    |
| Journaux des applications et des services | Journaux réservés à des composants ou à des produits précis.                     |

L’Observateur présente les journaux dans une arborescence à gauche. Au centre se trouve la liste des événements du journal sélectionné. La description de l’événement choisi apparaît dans un volet ou dans une fenêtre de détails.

<figure><img src=".gitbook/assets/image (148).png" alt=""><figcaption><p>L’Observateur d’événements rassemble les traces enregistrées par Windows et ses composants.</p></figcaption></figure>

#### Les renseignements contenus dans un événement

Un événement se comprend à partir de plusieurs renseignements. Son numéro est utile, mais il ne suffit pas à expliquer ce qui s’est produit.

| **Renseignement** | **Utilité**                                                       |
| ----------------- | ----------------------------------------------------------------- |
| Date et heure     | Situer l’événement par rapport au moment du problème.             |
| Source            | Identifier le composant ou le logiciel qui a enregistré la trace. |
| Identifiant       | Reconnaître un type d’événement pour cette source.                |
| Niveau            | Connaître l’importance attribuée à l’événement.                   |
| Description       | Lire le message qui explique ce qui a été enregistré.             |

Le niveau Information correspond souvent à une opération normale. Un Avertissement attire l’attention sur une situation à examiner. Une Erreur indique qu’une opération a rencontré un problème. Le niveau Critique signale un événement considéré comme particulièrement sérieux par le composant concerné.

Deux sources peuvent utiliser le même identifiant pour des événements différents. La source, le numéro et la description se lisent donc ensemble. Une erreur ancienne ou isolée n’explique pas nécessairement le problème observé aujourd’hui.

<figure><img src=".gitbook/assets/image (149).png" alt=""><figcaption><p>La description et la source permettent de comprendre le sens d’un événement</p></figcaption></figure>

#### Le filtrage des événements

Un journal peut contenir des milliers d’entrées. Le filtrage limite l’affichage aux événements qui correspondent à certains critères, comme une période, un niveau ou une source. Les autres événements restent dans le journal : ils sont simplement masqués par le filtre.

Si une application s’est fermée vers 10 h 15, les événements enregistrés autour de cette heure sont plus intéressants que ceux de la veille. Une erreur provenant de cette application constitue une piste. Des événements de niveau Information peuvent aussi aider à comprendre ce qui l’a précédée.

<figure><img src=".gitbook/assets/image (150).png" alt=""><figcaption><p>Un filtre réduit le nombre d’événements affichés sans effacer le contenu du journal.</p></figcaption></figure>

#### Ce que les journaux permettent de conclure

Un journal fournit des indices. Par exemple, une trace d’arrêt inattendu indique que Windows n’a pas terminé son arrêt normalement. Elle ne permet pas, à elle seule, d’affirmer que le bloc d’alimentation est défectueux. Une coupure de courant, un blocage ou un redémarrage forcé peuvent produire des traces semblables.

Le diagnostic consiste à rapprocher ces traces du problème observé. Effacer un journal ne répare pas la panne et retire des renseignements qui pourraient être utiles. Les événements peuvent être conservés dans un fichier .evtx, que l’Observateur d’événements peut rouvrir.

Dans le journal Sécurité, les règles d’audit déterminent les activités surveillées et enregistrées. L’absence d’une trace peut simplement signifier que cette surveillance n’était pas activée.

### C2 Utiliser le Planificateur de tâches

#### Le rôle du Planificateur

Le Planificateur de tâches permet à Windows de lancer automatiquement un programme au moment prévu. Il peut servir à exécuter un outil de maintenance chaque semaine ou à lancer une application à l’ouverture de session.

Une tâche planifiée est un ensemble de réglages enregistrés. Le Planificateur déclenche le programme choisi ; le travail lui-même est réalisé par ce programme. Par exemple, une tâche peut lancer un logiciel de sauvegarde, mais c’est ce logiciel qui copie les données.

#### Les éléments qui composent une tâche

| **Élément**    | **Rôle**                                         | **Exemple**                                       |
| -------------- | ------------------------------------------------ | ------------------------------------------------- |
| Déclencheur    | Détermine quand la tâche doit démarrer.          | Tous les jours à 17 h.                            |
| Action         | Définit le programme ou le script à lancer.      | Lancer un outil de sauvegarde.                    |
| Compte utilisé | Détermine avec quels droits la tâche fonctionne. | Un compte autorisé à lire les fichiers concernés. |
| Conditions     | Ajoutent des exigences pour l’exécution.         | Le portable doit être branché sur secteur.        |
| Paramètres     | Précisent le comportement de la tâche.           | Relancer une tâche qui a échoué.                  |

Un déclencheur peut être une heure, le démarrage de Windows ou l’ouverture d’une session. Il peut être ponctuel ou répétitif. Une tâche prévue une seule fois et une tâche quotidienne n’auront donc pas le même calendrier.

<figure><img src=".gitbook/assets/image (151).png" alt=""><figcaption><p>Le déclencheur indique à quel moment Windows doit lancer la tâche.</p></figcaption></figure>

#### Le programme et ses arguments

L’action précise ce que Windows doit exécuter. Dans une action de type Démarrer un programme, le champ Programme/script désigne le logiciel. Un script est un fichier contenant des instructions à exécuter automatiquement.

Les arguments donnent des renseignements supplémentaires au programme, comme le fichier à ouvrir ou une option à utiliser. Le programme et les arguments n’ont donc pas le même rôle.

Par exemple, une tâche appelée RappelCours pourrait ouvrir un document dans le Bloc-notes. Le programme serait le Bloc-notes et l’argument serait le chemin du document rappel.txt. Une tâche qui lance le Bloc-notes sans lui transmettre ce chemin peut ouvrir l’application sans ouvrir le document prévu.

<figure><img src=".gitbook/assets/image (152).png" alt=""><figcaption><p>Le programme indique quel logiciel lancer et les arguments précisent ce qu’il doit utiliser.</p></figcaption></figure>

#### Le compte et les conditions de fonctionnement

Une tâche s’exécute avec un compte utilisateur. Elle possède les droits de ce compte, pas automatiquement tous les droits du poste. Une tâche qui doit lire un dossier protégé a besoin d’un compte autorisé à y accéder.

Certaines tâches fonctionnent seulement lorsque l’utilisateur est connecté. D’autres peuvent fonctionner sans session ouverte. Dans ce dernier cas, un programme peut s’exécuter en arrière-plan sans afficher de fenêtre sur le Bureau.

Les conditions peuvent aussi empêcher le démarrage. Une tâche réservée à un portable branché sur secteur peut rester inactive lorsqu’il fonctionne sur batterie. Un ordinateur complètement éteint n’exécute pas la tâche à l’heure prévue. Une sortie de veille ou un rattrapage après une heure manquée dépend des options et du matériel.

Pour les fichiers partagés, une lettre comme Z: peut être connue dans la session d’un utilisateur et absente dans le contexte de la tâche. Un chemin UNC désigne directement le partage. Le compte de la tâche doit toujours disposer des accès nécessaires.

#### Le suivi des tâches

La bibliothèque du Planificateur rassemble les tâches enregistrées. Elle présente notamment leur état, la dernière exécution, la prochaine exécution et le dernier résultat. L’historique, lorsqu’il est activé, conserve des événements liés à leur fonctionnement.

Un résultat indiquant une réussite signifie que l’exécution s’est terminée sans erreur signalée. Il reste à distinguer ce résultat technique de l’effet attendu : un programme peut s’être lancé correctement sans avoir traité le bon fichier. L’historique et le résultat produit se complètent.

Une tâche désactivée conserve ses réglages, mais ne se déclenche plus. Une tâche supprimée disparaît du Planificateur. Windows et les logiciels possèdent leurs propres tâches de maintenance ; leur nom et leur rôle permettent de les distinguer des tâches ajoutées par un utilisateur.

<figure><img src=".gitbook/assets/image (153).png" alt=""><figcaption><p>Les renseignements du Planificateur et le résultat visible aident à comprendre ce que la tâche a fait.</p></figcaption></figure>

## Installation et désinstallation des applications

### Comprendre ce qui est installé

Télécharger consiste à récupérer un fichier depuis une source distante. Installer consiste à préparer une application pour qu’elle puisse fonctionner sur le poste. Le fichier téléchargé et l’application installée sont donc deux éléments différents.

Lors d’une installation, des fichiers sont placés sur le disque, des paramètres sont enregistrés et des raccourcis peuvent être créés. Certains logiciels ajoutent aussi des services qui fonctionnent en arrière-plan.

Une application peut être installée pour l’utilisateur actuel ou pour tous les utilisateurs du poste. Selon le logiciel et les modifications nécessaires, l’installation peut demander des droits d’administration.

Une application portable peut fonctionner sans installation classique, par exemple depuis un dossier extrait d’une archive. Elle reste un programme capable d’agir avec les droits de l’utilisateur. Le terme portable décrit sa façon d’être utilisée, pas son niveau de sécurité.

#### Les formats EXE MSI et MSIX

Un programme d’installation prépare l’application. Un paquet d’installation rassemble des fichiers et les renseignements nécessaires à leur mise en place. Plusieurs formats existent sous Windows.

| **Format ou service** | **Ce que cela représente**                | **À retenir**                                                                |
| --------------------- | ----------------------------------------- | ---------------------------------------------------------------------------- |
| EXE                   | Un fichier exécutable.                    | Il peut être l’application elle-même ou son programme d’installation.        |
| MSI                   | Un paquet traité par Windows Installer.   | Windows Installer réalise les opérations prévues dans le paquet.             |
| MSIX                  | Un format de paquet moderne pour Windows. | Il organise l’installation, les mises à jour et le retrait de l’application. |
| Microsoft Store       | Un magasin d’applications.                | Il s’agit d’un moyen de distribution, pas d’une extension de fichier.        |

Un nom comme setup.exe signifie souvent qu’il s’agit d’un installateur, mais il ne suffit pas à identifier son éditeur. De même, un fichier MSI n’est pas automatiquement fiable parce que son format est pris en charge par Windows.

Le format MSIX donne une identité au paquet et prévoit une gestion structurée de l’application. Dans le fonctionnement normal, un paquet MSIX doit posséder une signature acceptée par Windows. Il peut être distribué par le Store ou par un autre canal autorisé

### Choisir une source fiable

La source est l’endroit d’où provient le logiciel. Le site officiel de l’éditeur, le Microsoft Store et le catalogue approuvé par une organisation sont des points de départ habituels. Une publicité ou un logo connu ne suffit pas à prouver qu’un site appartient à l’éditeur.

Une adresse en HTTPS indique que les échanges avec le site sont chiffrés. Cela ne garantit pas que le site est honnête ni que ses fichiers sont sans danger. Le nom de domaine et l’identité de l’éditeur restent des renseignements utiles.

Le logiciel doit aussi être compatible avec le poste : version de Windows, architecture du processeur, mémoire et espace de stockage. Les mentions x64 et ARM64, par exemple, correspondent à des architectures différentes. Les indications de l’éditeur précisent les versions prises en charge.

#### La signature numérique du logiciel

Une signature numérique aide à vérifier qui a signé un fichier et si son contenu signé a été modifié. Lorsqu’elle est visible dans les propriétés du fichier, Windows peut afficher le nom du signataire et le résultat de la vérification.

Une signature valide apporte un renseignement sur l’origine et l’intégrité du fichier. Elle ne garantit pas que le logiciel est utile ou sans risque. À l’inverse, l’absence d’un onglet Signatures numériques ne suffit pas à prouver qu’un fichier est malveillant.

Certains éditeurs publient aussi une empreinte, une valeur calculée à partir du fichier. Une comparaison avec une empreinte de référence fiable aide à repérer un fichier différent de celui attendu.

Un blocage par une protection Windows est une information à examiner. Il peut être lié à une détection, à la réputation du fichier ou à une règle de l’organisation. Le supprimer en désactivant la protection ne rend pas le logiciel plus fiable.

### Installer une application avec son interface graphique

#### Le principe de l’installation interactive

Une installation graphique, aussi appelée interactive, présente des fenêtres dans lesquelles l’utilisateur fait des choix. L’ensemble de ces fenêtres forme souvent un assistant d’installation.

Selon le logiciel, l’assistant présente les conditions d’utilisation, le dossier de destination, les composants facultatifs et les raccourcis à créer. Un composant facultatif ajoute une fonction, mais n’est pas nécessairement utile à tous les utilisateurs.

Une demande UAC peut apparaître si l’installation doit modifier des éléments protégés du système. Elle concerne les droits nécessaires à cette opération. Elle ne remplace pas la vérification de la provenance du logiciel.

Un redémarrage peut être nécessaire pour terminer certaines modifications. L’apparition d’un raccourci indique seulement qu’un lien a été créé. Le démarrage de l’application et le fonctionnement de ses fonctions principales permettent de confirmer qu’elle est utilisable.

#### Le Microsoft Store

Le Microsoft Store regroupe des fiches d’applications. Une fiche indique notamment le nom du logiciel, son éditeur, sa description et son prix éventuel. Le bouton affiché dépend de son état : l’application peut être à obtenir, à installer ou déjà prête à être ouverte.

Le Store simplifie l’accès aux applications et peut gérer leurs mises à jour. La présence d’un logiciel dans le Store ne signifie pas que Microsoft en est l’auteur. Sur un poste d’établissement, les applications disponibles et les installations permises peuvent être limitées par la gestion informatique.

### Désinstaller et entretenir les applications

La désinstallation retire une application à l’aide du mécanisme prévu par Windows ou par son éditeur. La liste Applications installées, dans les Paramètres, permet de retrouver de nombreuses applications et leur option de désinstallation. Certaines applications classiques se gèrent aussi dans le Panneau de configuration.&#x20;

Supprimer une icône du Bureau enlève seulement le raccourci. Effacer manuellement le dossier d’un logiciel peut laisser des services ou des réglages devenus inutilisables. La désinstallation coordonne le retrait des éléments concernés.

Les documents personnels et les réglages ne sont pas toujours supprimés avec l’application. Le comportement dépend du logiciel et des options proposées. Certaines données peuvent toutefois être perdues lors du retrait ou d’une réinitialisation.

#### Les différentes opérations d’entretien

| **Opération** | **But principal**                            | **Conséquence possible**                                     |
| ------------- | -------------------------------------------- | ------------------------------------------------------------ |
| Mettre à jour | Installer une version plus récente.          | Corrections de problèmes, de sécurité ou de fonctionnalités. |
| Réparer       | Corriger le fonctionnement de l’application. | Remise en état de certains éléments, selon le logiciel.      |
| Réinitialiser | Remettre l’application dans un état initial. | Perte possible des réglages et des données de l’application. |
| Désinstaller  | Retirer l’application du poste.              | L’application n’est plus disponible pour l’usage concerné.   |

Les options Réparer et Réinitialiser ne sont pas proposées pour toutes les applications. Une mise à jour peut aussi modifier l’interface ou la compatibilité avec d’autres outils. Dans une organisation, ces changements sont généralement évalués avant leur déploiement sur l’ensemble des postes.

### Installation silencieuse et installation automatisée

#### Une installation silencieuse

Une installation silencieuse se déroule sans afficher l’assistant habituel ni demander les choix un à un. Les réponses sont fournies à l’avance par des options ou par les réglages prévus dans le programme d’installation.

Le mot silencieuse concerne l’interface de l’installateur. L’installation continue à copier des fichiers et à modifier le système. Elle peut échouer ou demander un redémarrage même si aucune fenêtre ne s’affiche.

Une personne peut lancer manuellement une installation silencieuse. Ce mode ne donne pas de droits supplémentaires : si l’application exige des privilèges d’administration, ceux-ci restent nécessaires.

#### Une installation automatisée

Une installation automatisée est prise en charge par une procédure ou un outil qui réalise les opérations prévues. Elle peut inclure la récupération du logiciel, son installation et la vérification du résultat. Un script ou un outil de gestion de postes peut coordonner ces opérations.

Dans une salle de trente ordinateurs, l’automatisation permet de préparer les postes avec les mêmes applications et les mêmes réglages. Elle évite de refaire les choix à la main sur chacun. Elle utilise souvent le mode silencieux, mais les deux notions décrivent des aspects différents : l’une concerne l’absence de questions à l’écran, l’autre l’enchaînement des opérations.

#### Les options et les traces de l’installation

Les installateurs peuvent recevoir des options qui précisent leur comportement. Pour un paquet MSI, l’outil msiexec propose notamment /qn pour masquer l’interface et /norestart pour empêcher un redémarrage automatique. Un redémarrage peut quand même rester nécessaire pour terminer l’installation. Les installateurs EXE n’utilisent pas tous les mêmes options.&#x20;

Un journal d’installation conserve des messages sur le déroulement de l’opération. Un code de retour est une valeur fournie par le programme pour signaler son résultat. Sa signification dépend de l’outil : elle peut indiquer une réussite, une erreur ou un redémarrage nécessaire.

Une automatisation fiable tient compte de l’état du poste. Le logiciel peut être déjà présent, le téléchargement peut échouer ou une autre installation peut être en cours. Le résultat d’une opération détermine si la suivante peut commencer. Un essai sur un poste représentatif aide à éviter de reproduire une erreur sur toute une salle.

### Découvrir Windows Package Manager

#### Le rôle de WinGet

Windows Package Manager est un outil de Microsoft pour gérer des applications à l’aide de commandes. Son outil en ligne de commande s’appelle WinGet. Il permet notamment de rechercher un logiciel, de l’installer, de le mettre à jour ou de le retirer.&#x20;

WinGet s’appuie sur des sources, c’est-à-dire des catalogues d’applications. Le catalogue fournit des renseignements sur les logiciels et leur installation. Une application y possède notamment un nom, un identifiant et une version. Le catalogue communautaire winget et la source msstore, associée au Microsoft Store, sont deux exemples.

WinGet utilise notamment les fichiers d’installation fournis par les éditeurs. Tous les logiciels du catalogue ne sont donc pas créés par Microsoft. Leur provenance et leur compatibilité gardent la même importance que lors d’une installation graphique.

L’outil est distribué avec le composant Programme d’installation d’application, aussi appelé App Installer. Sa présence dépend de la configuration de Windows et des choix de gestion du poste.&#x20;

#### Le terminal et les commandes

Un terminal est une fenêtre dans laquelle on peut saisir des commandes et lire leur résultat. Il peut accueillir un environnement comme PowerShell. WinGet est un outil utilisé dans cet environnement ; il n’est pas le terminal lui-même.

Une commande WinGet commence par le mot winget, suivi de l’action demandée. Le vocabulaire est limité : search signifie rechercher, install signifie installer et list signifie afficher une liste. Des options permettent ensuite de préciser le logiciel ou le catalogue visé.

#### La recherche dans un catalogue

La commande suivante illustre une recherche de l’application 7-Zip dans la source winget :

`winget search 7zip --source winget`

Le résultat présente des applications disponibles dans le catalogue. Il ne signifie pas qu’elles sont déjà installées sur le poste. La commande show permet de consulter les renseignements détaillés d’un paquet, comme l’éditeur, la version et la provenance de l’installateur.

L’identifiant désigne un paquet de façon plus précise que son nom courant. Par exemple, 7zip.7zip est l’identifiant utilisé pour 7-Zip dans cet exemple. Le contenu d’un catalogue peut évoluer.

#### Les applications disponibles et les applications installées

La commande install demande l’installation d’une application. Une commande précise peut prendre cette forme :

`winget install --id 7zip.7zip --exact --source winget`

Dans cet exemple, --id indique que le logiciel est désigné par son identifiant. --exact demande une correspondance exacte et --source winget précise le catalogue. Ces options réduisent les ambiguïtés lorsqu’il existe plusieurs résultats proches.&#x20;

La commande list affiche les applications installées que WinGet reconnaît sur l’ordinateur. Elle peut aussi présenter des applications installées par une autre méthode. La recherche porte donc sur les catalogues, tandis que la liste porte sur le contenu du poste

#### Les principales commandes de WinGet

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Commande ou action</strong></td><td><strong>Rôle</strong></td></tr><tr><td>winget --version</td><td>Afficher la version de l’outil WinGet.</td></tr><tr><td>winget --help</td><td>Afficher l’aide générale.</td></tr><tr><td>search</td><td>Rechercher une application dans les sources configurées.</td></tr><tr><td>show</td><td>Consulter les renseignements détaillés d’un paquet.</td></tr><tr><td>install</td><td>Demander l’installation d’une application.</td></tr><tr><td>list</td><td>Afficher les applications installées reconnues par WinGet.</td></tr><tr><td>upgrade</td><td>Voir les mises à jour disponibles ou mettre à jour les applications ciblées, selon les options.</td></tr><tr><td>uninstall</td><td>Demander la désinstallation d’une application.</td></tr><tr><td>winget source list</td><td>Afficher les sources configurées.</td></tr></tbody></table>

La commande winget upgrade, utilisée seule, affiche les mises à jour que l’outil identifie. Lorsqu’une application est précisée, elle peut en demander la mise à jour. Consulter une liste et lancer une modification sont deux actions différentes.&#x20;

WinGet peut demander une confirmation, présenter des conditions d’utilisation ou provoquer une demande UAC. L’option --silent demande un installateur silencieux lorsque ce mode est pris en charge. Elle ne supprime pas les exigences de sécurité ni les éventuelles autres demandes de confirmation.&#x20;

La ligne de commande facilite la répétition des opérations, mais elle ne garantit pas leur réussite. Un message d’erreur peut concerner le catalogue, la connexion, les droits du compte ou l’installateur. Le message et le résultat obtenu permettent de distinguer ces situations.

## Repères essentiels

### Les outils et leur utilité

Chaque outil répond à un besoin précis. Ce tableau rassemble les principaux repères du cours.

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Besoin</strong></td><td><strong>Outil ou emplacement</strong></td></tr><tr><td>Retrouver un document et son chemin</td><td>Explorateur de fichiers.</td></tr><tr><td>Connaître la RAM et l’édition de Windows</td><td>Paramètres > Système > Informations système ou À propos.</td></tr><tr><td>Examiner la configuration détaillée</td><td>Informations système, avec msinfo32.</td></tr><tr><td>Repérer une application très active</td><td>Gestionnaire des tâches.</td></tr><tr><td>Créer un compte standard</td><td>Paramètres > Comptes > Autres utilisateurs.</td></tr><tr><td>Gérer les groupes locaux</td><td>Gestion de l’ordinateur, sur une édition compatible.</td></tr><tr><td>Contrôler les permissions d’un dossier</td><td>Propriétés > Sécurité.</td></tr><tr><td>Rendre un dossier accessible par SMB</td><td>Propriétés > Partage > Partage avancé.</td></tr><tr><td>Donner une lettre à un partage</td><td>Ce PC > Connecter un lecteur réseau.</td></tr><tr><td>Examiner les traces d’un problème</td><td>Observateur d’événements.</td></tr><tr><td>Lancer une action à un moment prévu</td><td>Planificateur de tâches.</td></tr><tr><td>Retirer une application</td><td>Paramètres > Applications > Applications installées.</td></tr><tr><td>Gérer des applications par commandes</td><td>WinGet dans un terminal.</td></tr></tbody></table>

### Les distinctions à retenir

Un dossier partagé rend des fichiers accessibles par le réseau. Un lecteur réseau facilite l’accès à ce dossier grâce à une lettre. Les autorisations restent les mêmes, quelle que soit la manière d’ouvrir le partage.

L’Observateur d’événements aide à comprendre une activité déjà enregistrée. Le Planificateur de tâches sert à organiser l’exécution automatique d’une action. Le premier fournit des traces ; le second prépare un lancement.

Télécharger, installer, mettre à jour et désinstaller correspondent à des opérations différentes. Le mode graphique présente des choix à l’écran. Le mode silencieux utilise des choix déjà prévus. L’automatisation coordonne les opérations et leur suivi.

## Références:&#x20;

Ces références permettent de retrouver les notions et les outils présentés. Le nom et l’emplacement de certaines options peuvent évoluer avec les versions de Windows.

<sup>\[1]</sup>  [Extensions de nom de fichier courantes dans Windows](https://support.microsoft.com/fr-fr/windows/experience/storage-filemanagement/common-file-name-extensions-in-windows)

<sup>\[2]</sup>  [Rechercher des informations sur votre appareil Windows](https://support.microsoft.com/fr-FR/Windows/Experience/find-information-about-your-windows-device)

<sup>\[3]</sup>  [Description of Microsoft System Information](https://support.microsoft.com/en-US/Windows/Experience/description-of-microsoft-system-information-msinfo32-exe-tool)

<sup>\[4]</sup>  [Configurer des applications de démarrage dans Windows](https://support.microsoft.com/fr-fr/windows/experience/startup-boot/configure-startup-applications-in-windows)

<sup>\[5]</sup>  [Gérer les comptes d’utilisateur dans Windows](https://support.microsoft.com/fr-fr/windows/security/identity-signin/manage-user-accounts-in-windows)

<sup>\[6]</sup>  [Fonctionnement du contrôle de compte utilisateur](https://learn.microsoft.com/fr-fr/windows/security/application-security/application-control/user-account-control/how-it-works)

<sup>\[7]</sup>  [Vue d’ensemble du contrôle d’accès](https://learn.microsoft.com/fr-fr/windows/security/identity-protection/access-control/access-control)

<sup>\[8]</sup>  [Partage de fichiers sur un réseau dans Windows](https://support.microsoft.com/fr-fr/windows/experience/connectivity-networking/file-sharing-over-a-network-in-windows)

<sup>\[9]</sup>  [System configuration tools in Windows](https://support.microsoft.com/en-us/windows/experience/system-configuration-tools-in-windows)

<sup>\[10]</sup>  [Task Scheduler for developers](https://learn.microsoft.com/en-us/windows/win32/taskschd/task-scheduler-start-page)

<sup>\[11]</sup>  [Qu’est-ce que MSIX](https://learn.microsoft.com/fr-fr/windows/msix/overview)

<sup>\[12]</sup>  [Tips to improve PC performance in Windows](https://support.microsoft.com/en-us/windows/experience/performance-optimization/tips-to-improve-pc-performance-in-windows)

<sup>\[13]</sup>  [msiexec](https://learn.microsoft.com/fr-fr/windows-server/administration/windows-commands/msiexec)

<sup>\[14]</sup>  [Error Codes pour Windows Installer](https://learn.microsoft.com/en-us/windows/win32/msi/error-codes)

<sup>\[15]</sup>  [Utiliser WinGet pour installer et gérer des applications](https://learn.microsoft.com/fr-fr/windows/package-manager/winget/)

<sup>\[16]</sup>  [Commande install de WinGet](https://learn.microsoft.com/fr-fr/windows/package-manager/winget/install)

<sup>\[17]</sup>  [Commande list de WinGet](https://learn.microsoft.com/en-us/windows/package-manager/winget/list)

<sup>\[18]</sup>  [Commande upgrade de WinGet](https://learn.microsoft.com/en-us/windows/package-manager/winget/upgrade)
