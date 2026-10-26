# Chapitre 10 - Linux en ligne de commande

## Objectifs d'apprentissage

* Comprendre le fonctionnement du terminal Linux et utiliser les commandes avec leurs options et arguments.
* Naviguer dans l’arborescence Linux et manipuler les fichiers et les dossiers à l’aide de commandes.
* Créer et gérer des utilisateurs et des groupes à partir du terminal.
* Gérer les disques, les partitions et les systèmes de fichiers sous Linux.
* Comprendre et modifier les permissions et les droits d’accès aux fichiers et aux dossiers.
* Installer, mettre à jour et désinstaller des applications à l’aide des commandes et des gestionnaires de paquets Linux.

## Comprendre la fenêtre du terminal&#x20;

Le terminal est l’application qui affiche du texte et reçoit ce que vous tapez. Le shell est le programme qui interprète vos commandes. Dans ce chapitre, ce programme est Bash. Linux est le système qui exécute les opérations demandées, à travers son noyau et ses outils.

Sur Ubuntu, recherchez Terminal dans les applications. Le raccourci Ctrl + Alt + T fonctionne dans de nombreuses configurations du bureau.

<figure><img src=".gitbook/assets/image (154).png" alt=""><figcaption></figcaption></figure>

Dans l’invite `amelie@sec-linux:~/LaboCLI$`, `amelie` est le compte utilisé et `sec-linux` est le nom de la machine. La partie `~/LaboCLI` indique le dossier courant, c’est-à-dire celui dans lequel vous travaillez. Le symbole `~` représente votre dossier personnel.

Le symbole `$` indique habituellement une session ordinaire. Le symbole `#` est souvent utilisé pour une session administrateur `root`. L’invite reste personnalisable : `whoami` et `id` permettent de vérifier votre identité réelle.

### Saisir et corriger une commande

Tapez la commande, puis appuyez sur Entrée. Le terminal affiche le résultat, un message d’erreur ou simplement une nouvelle invite. Une commande réussie ne produit pas toujours de message.

| Touche ou raccourci              | Utilité                                                                                 |
| -------------------------------- | --------------------------------------------------------------------------------------- |
| Tab                              | Compléter un nom de commande ou de fichier ; deux pressions peuvent afficher les choix. |
| Flèches haut et bas              | Retrouver les commandes précédentes.                                                    |
| Ctrl + C                         | Interrompre généralement le programme en cours.                                         |
| Ctrl + L                         | Nettoyer l’affichage du terminal.                                                       |
| Ctrl + Maj + C et Ctrl + Maj + V | Copier et coller dans de nombreux terminaux graphiques.                                 |

Ctrl + C n’est donc pas le raccourci habituel de copie dans le terminal. Pour fermer proprement le shell, utilisez exit. Évitez de fermer la fenêtre pendant une copie ou une installation en cours.

## Lire la syntaxe et les options

Une commande comporte généralement un nom, des options et des arguments. Le nom indique l’action. Les options modifient la façon de l’exécuter. Les arguments précisent les éléments visés, par exemple un dossier ou un fichier.

```
commande [options] [arguments]
ls -lh /var/log
```

Dans cet exemple, ls liste des éléments, `-l` demande les détails et `-h` rend les tailles plus lisibles. `/var/log` est le dossier à examiner. Les crochets de la première ligne appartiennent à la notation explicative : ils indiquent des éléments facultatifs et ne se tapent pas.

### Options courtes et longues

| Exemple               | Explication                                                         |
| --------------------- | ------------------------------------------------------------------- |
| `ls -l -a`            | Deux options courtes séparées.                                      |
| `ls -la`              | Les mêmes options regroupées pour ls.                               |
| `ls --all`            | Forme longue de l’option `-a`.                                      |
| `head -n 5 notes.txt` | L’option `-n` reçoit la valeur 5 ; `notes.txt` est le fichier visé. |

Une option courte commence souvent par un tiret ; une option longue, par deux. Le sens d’une lettre dépend de la commande. Il faut donc éviter de déduire le rôle d’une option uniquement à partir de son nom. Les majuscules comptent : `-r` et `-R` peuvent avoir des rôles différents.

Pour les outils GNU utilisés ici, `--` marque la fin des options. Par exemple, `ls -- -rapport.txt` examine un fichier dont le nom commence par un tiret. Cette écriture évite que le nom soit interprété comme une option.

### Trouver de l’aide

```
ls --help
man ls
help cd
```

`--help` affiche une aide courte pour de nombreux programmes. man ouvre le manuel : utilisez les flèches pour vous déplacer, `/mot` pour rechercher un mot et `q` pour quitter. `cd` est une commande intégrée à Bash ; `help cd` explique son fonctionnement.

Les mots anglais FILE, DIRECTORY ou USER dans l’aide sont des indications à remplacer par un vrai fichier, un vrai dossier ou un nom de compte. Ne les recopiez pas automatiquement.

Les espaces séparent les éléments. Pour viser un nom contenant un espace, écrivez par exemple `mkdir "Travail equipe"`. Sans les guillemets, cette commande créerait deux dossiers distincts.

## Se déplacer dans les dossiers

Linux organise les fichiers dans une seule arborescence qui commence à `/`. Ce symbole désigne la racine. Le dossier `/home` contient habituellement les dossiers personnels des utilisateurs. Le dossier personnel de root est généralement `/root` : il ne faut pas le confondre avec la racine `/`.

### Chemins absolus et relatifs

Un chemin absolu commence par `/` et indique un emplacement depuis la racine, par exemple `/home/amelie/LaboCLI`. Un chemin relatif part du dossier courant. Si vous êtes dans `/home/amelie`, le chemin `LaboCLI` désigne le même dossier.

| Repère | Signification                       | Exemple |
| ------ | ----------------------------------- | ------- |
| `/`    | Racine de l’arborescence            | `cd /`  |
| `~`    | Dossier personnel du compte courant | `cd ~`  |
| `.`    | Dossier courant                     | `ls .`  |
| `..`   | Dossier parent                      | `cd ..` |

### Une première suite de commandes

```
pwd
mkdir -p ~/LaboCLI/Documents
cd ~/LaboCLI
pwd
cd Documents
pwd
cd ..
```

`pwd` affiche le chemin du dossier courant. `mkdir -p` crée les dossiers manquants du chemin. `cd` change de dossier. Après `cd Documents`, `pwd` affiche `/home/amelie/LaboCLI/Documents` si votre compte s’appelle `amelie`.

`cd` sans argument vous ramène dans votre dossier personnel. `cd -` revient au dossier où vous étiez juste avant le dernier déplacement. Changer de dossier ne déplace aucun fichier : cela change seulement votre emplacement de travail dans le shell.

### Quelques dossiers à reconnaître

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Dossier</td><td>Rôle habituel</td></tr><tr><td><code>/home</code></td><td>Dossiers personnels des utilisateurs.</td></tr><tr><td><code>/etc</code></td><td>Fichiers de configuration du système.</td></tr><tr><td><code>/var/log</code></td><td>Journaux produits par le système et les services.</td></tr><tr><td><code>/tmp</code></td><td>Fichiers temporaires ; ce n’est pas un lieu de conservation.</td></tr><tr><td>/dev</td><td>Fichiers représentant notamment les périphériques.</td></tr><tr><td><code>/mnt</code> et <code>/media</code></td><td>Emplacements courants pour accéder à des systèmes de fichiers montés.</td></tr></tbody></table>

## Utiliser les premières commandes

Pour commencer, quelques commandes suffisent à répondre à trois questions : qui utilise cette session, où travaille-t-on et que contient ce dossier ?

Les noms sont généralement sensibles aux majuscules sur les systèmes de fichiers Linux courants. Documents et documents peuvent désigner deux dossiers différents. Utilisez Tab pour compléter les noms et limiter les fautes de frappe.

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Commande</td><td>Ce qu’elle permet de vérifier</td></tr><tr><td><code>whoami</code></td><td>Le nom du compte effectif.</td></tr><tr><td><code>hostname</code></td><td>Le nom de la machine.</td></tr><tr><td><code>pwd</code></td><td>Le chemin du dossier courant.</td></tr><tr><td><code>date</code></td><td>La date et l’heure du système.</td></tr><tr><td><code>uname -r</code></td><td>La version du noyau Linux.</td></tr><tr><td><code>clear</code></td><td>Nettoyer l’affichage ; cela ne supprime pas les fichiers.</td></tr><tr><td><code>history</code></td><td>Afficher l’historique des commandes de la session et de son historique chargé.</td></tr></tbody></table>

`uname -r` ne donne pas le numéro de version d’Ubuntu. Pour consulter les informations sur la distribution, vous pouvez lire le fichier `/etc/os-release` avec `cat /etc/os-release`

### Examiner le contenu avec ls

```
ls
ls -a
ls -l
ls -lh
ls -ld Documents
```

`ls` liste les noms du dossier courant. `-a` inclut les noms cachés, qui commencent par un point. Un fichier caché n’est pas forcément protégé : il est simplement masqué dans l’affichage ordinaire. `-l` affiche les détails et `-h` exprime les tailles avec des unités comme K ou M.

Avec `ls -l Documents`, vous examinez les éléments contenus dans Documents. Avec `ls -ld Documents`, vous examinez le dossier Documents lui-même. Cette différence sera utile pour vérifier ses permissions.

### Exemple de ligne détaillée

```
-rw-r----- 1 amelie equipe 18 oct. 23 09:40 notes.txt
```

Cette ligne indique les permissions, le nombre de liens physiques, le propriétaire, le groupe, la taille en octets, la date de modification et le nom. Ici, `amelie` possède le fichier et equipe est le groupe associé. La partie `-rw-r-----` sera détaillée dans la section sur les permissions.

La taille affichée pour un dossier par `ls -l` ne représente pas la somme de ses fichiers. Pour mesurer l’espace utilisé par son contenu, on utilisera du.

L’historique peut conserver les commandes saisies. Ne placez pas un mot de passe directement dans une commande pour gagner du temps. Utilisez la saisie prévue par le programme.

## Créer copier et déplacer des fichiers

Pour ces exemples, placez-vous dans votre dossier de travail. Les noms choisis sans espace facilitent les premiers essais.

```
mkdir -p ~/LaboCLI
cd ~/LaboCLI
mkdir Documents Copies
touch Documents/notes.txt
```

`mkdir` crée un dossier. Plusieurs noms permettent d’en créer plusieurs à la fois. touch crée un fichier vide si celui-ci n’existe pas. Si le fichier existe déjà, touch met à jour ses horodatages ; il n’efface pas son contenu.

### Copier avec cp

```
cp Documents/notes.txt Copies/
cp Documents/notes.txt Documents/notes-copie.txt
cp -r Documents Copies/Documents
```

La première commande copie `notes.txt` dans `Copies`. La deuxième crée une copie sous un autre nom. La troisième copie le dossier `Documents` et son contenu ; elle suppose que `Copies/Documents` n’existe pas encore. L’option `-r` demande une copie récursive, c’est-à-dire une copie qui parcourt aussi les sous-dossiers.

L’ordre des arguments compte : `cp source destination`. Si le fichier de destination existe, une copie peut le remplacer. `cp -i` demande une confirmation avant un écrasement. Une copie ordinaire ne garantit pas la conservation de tous les attributs ; `cp -a` sert à préserver autant que possible la structure et les attributs lors d’une copie d’archive.

### Déplacer ou renommer avec mv

```
mv Documents/notes-copie.txt Documents/brouillon.txt
mv Documents/brouillon.txt Copies/
```

`mv` sert à renommer un élément ou à le déplacer. Dans la première commande, le fichier reste dans le même dossier et change de nom. Dans la deuxième, il change de dossier. Après un déplacement réussi, il n’existe plus à son ancien emplacement.

`mv -i` demande une confirmation lorsqu’une destination risque d’être remplacée. Pour déplacer un dossier, `mv` n’a pas besoin de l’option `-r`.

### Vérifier ce qui a changé

```
ls -l Documents
ls -l Copies
```

Après une copie, recherchez l’original et la copie. Après un déplacement, vérifiez la nouvelle destination. Le retour de l’invite, à lui seul, ne vous indique pas où le fichier a été placé.

## Supprimer et sélectionner des éléments

`rm` supprime un fichier sans passer par la corbeille du bureau. Avant une suppression, vérifiez le dossier courant avec pwd et les noms visés avec `ls`.

```
rm -i brouillon.txt
rmdir AncienDossier
rm -ri DossierEssai
```

`rm -i` demande une confirmation. `rmdir` supprime uniquement un dossier vide. `rm -ri` parcourt un dossier et son contenu tout en demandant des confirmations. L’option `-f` force certaines opérations et supprime les demandes de confirmation : elle n’est pas nécessaire pour les premiers exercices.

Une suppression n’est pas une façon de revenir en arrière. Si vous effacez le mauvais fichier, le terminal ne dispose pas d’un bouton Annuler général.

### Sélectionner plusieurs noms

Le shell peut développer certains caractères avant de lancer la commande. On les appelle des caractères génériques.

| Motif       | Noms sélectionnés                                       |
| ----------- | ------------------------------------------------------- |
| `*.txt`     | Noms qui se terminent par .txt dans le dossier courant. |
| `rapport*`  | Noms qui commencent par rapport.                        |
| `note?.txt` | Noms avec exactement un caractère entre note et .txt.   |

```
ls -- *.txt
cp -- *.txt Copies/
```

La première ligne permet de voir les noms qui correspondent au motif avant de les copier. Dans la configuration habituelle de Bash, `*` ne sélectionne pas les noms commençant par un point et ne traverse pas automatiquement les sous-dossiers.

Si aucun nom ne correspond, Bash laisse généralement le motif tel quel ; la commande peut alors signaler que `*.txt` n’existe pas. Les guillemets changent aussi le comportement : `"*.txt"` reste un texte littéral pour le shell.

### Reconnaître un lien symbolique

```
ln -s Documents/notes.txt raccourci-notes
ls -l raccourci-notes
```

Un lien symbolique est un nom qui pointe vers un autre emplacement. `ls -l` commence alors par l et affiche la cible. Supprimer le lien avec `rm raccourci-notes` ne supprime pas le fichier cible. Si la cible est supprimée ou déplacée, le lien peut devenir inutilisable.

## Lire modifier et rechercher du texte

Beaucoup de configurations et de journaux Linux sont des fichiers texte. Vous pouvez les consulter sans ouvrir une application graphique.

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Commande</td><td>Utilisation</td></tr><tr><td><code>cat notes.txt</code></td><td>Afficher tout le fichier dans le terminal.</td></tr><tr><td><code>less notes.txt</code></td><td>Lire un fichier écran par écran.</td></tr><tr><td><code>head -n 5 notes.txt</code></td><td>Afficher les cinq premières lignes.</td></tr><tr><td><code>tail -n 5 notes.txt</code></td><td>Afficher les cinq dernières lignes.</td></tr><tr><td><code>wc -l notes.txt</code></td><td>Compter les caractères de fin de ligne ; cela correspond généralement au nombre de lignes.</td></tr><tr><td><code>nano notes.txt</code></td><td>Ouvrir un éditeur de texte dans le terminal.</td></tr></tbody></table>

Dans `less`, utilisez Espace pour avancer, `/mot` pour rechercher et `q` pour quitter. Pour suivre un journal qui reçoit de nouvelles lignes, `tail -f fichier.log` reste actif ; Ctrl + C arrête ce suivi.

### Écrire avec nano

Lancez `nano notes.txt`, puis saisissez quelques lignes. Ctrl + O demande l’enregistrement ; validez le nom avec Entrée. Ctrl + X quitte l’éditeur. Dans la barre d’aide de `nano`, ^ représente la touche Ctrl. Si nano est absent de votre image Ubuntu, l’enseignant pourra le faire installer.

### Rechercher dans un fichier avec grep

```
grep -n "erreur" journal.txt
grep -in "erreur" journal.txt
```

`grep` affiche les lignes qui correspondent au motif. `-n` ajoute leur numéro. `-i` ignore la différence entre majuscules et minuscules. Ainsi, la deuxième commande peut trouver erreur, Erreur ou ERREUR. Un fichier sans correspondance ne produit normalement aucune ligne de résultat.

### Rechercher un fichier avec find

```
find ~/LaboCLI -type f -name "*.txt"
find ~/LaboCLI -type d -name "Copies"
```

`find` parcourt le dossier indiqué et ses sous-dossiers. `-type f` sélectionne les fichiers ordinaires ; `-type d` sélectionne les dossiers. `-name` filtre selon le nom. Ici, les guillemets autour de `"*.txt"` sont nécessaires pour transmettre le motif à `find`, sans que Bash le développe d’abord.

`grep` cherche dans le contenu. `find` cherche des éléments dans l’arborescence. Cette distinction évite d’utiliser le bon outil au mauvais endroit.

## Enregistrer et combiner les résultats

Une commande peut envoyer du texte vers l’écran, vers un fichier ou vers une autre commande. Les symboles suivants sont interprétés par le shell.

| Symbole | Rôle                                                                |
| ------- | ------------------------------------------------------------------- |
| `>`     | Écrire la sortie normale dans un fichier en remplaçant son contenu. |
| `>>`    | Ajouter la sortie normale à la fin d’un fichier.                    |
| `2>`    | Écrire les messages d’erreur dans un fichier.                       |
| `\|`    | Envoyer la sortie normale d’une commande à l’entrée de la suivante. |

### Créer un petit fichier texte

```
cd ~/LaboCLI
echo "Premiere ligne" > notes.txt
echo "Deuxieme ligne" >> notes.txt
cat notes.txt
```

Le fichier contient maintenant deux lignes. `echo` affiche le texte fourni. `>` crée le fichier s’il n’existe pas, mais vide un fichier existant avant d’écrire. `>>` conserve le contenu précédent et ajoute la nouvelle ligne.

Le remplacement par `>` ne demande pas de confirmation dans la configuration habituelle. N’utilisez donc pas le même fichier comme entrée et comme destination, par exemple `cat notes.txt > notes.txt` : son contenu serait perdu.

### Filtrer la sortie avec un tube

```
ls -l /etc | less
grep -i "erreur" journal.txt | wc -l
```

Dans la première commande, `less` reçoit la liste et permet de la lire écran par écran. Dans la deuxième, `grep` sélectionne les lignes contenant erreur, puis `wc -l` les compte. Le résultat compte les lignes trouvées, pas le nombre total d’occurrences du mot.

Un tube ne transporte normalement pas les messages d’erreur. Pour les conserver séparément lors d’une recherche, on peut écrire :

```
find /etc -name "*.conf" 2> erreurs.txt
```

### Vérifier une réussite

```
mkdir Essai
echo $?
```

`$?` contient le code de retour de la dernière commande : 0 indique une réussite, une autre valeur signale une situation différente. Il faut le consulter immédiatement. `&&` permet d’exécuter la suite seulement si la première commande réussit, par exemple `mkdir Test && cd Test`.

## Comprendre les utilisateurs et root

Chaque opération est exécutée avec l’identité d’un utilisateur. Cette identité détermine notamment quels fichiers il peut consulter ou modifier. Un compte possède un nom et un numéro appelé UID. Un groupe possède aussi un numéro, le GID.

```
whoami
id
groups
```

Exemple de résultat de id :

```
uid=1001(amelie) gid=1001(amelie) groups=1001(amelie),1003(equipe)
```

Ici, `amelie` est l’utilisatrice. Son groupe principal est `amelie` et elle appartient aussi au groupe supplémentaire `equipe`. Les numéros varient selon l’ordre de création des comptes et la configuration.

Un compte peut appartenir à plusieurs groupes. En revanche, un fichier possède un seul groupe propriétaire dans le modèle classique étudié ici. Ce groupe permet d’attribuer les mêmes droits à plusieurs personnes.

### Utiliser sudo au bon moment

root est le compte d’administration ; son UID est 0. Il dispose de privilèges très étendus. Sur Ubuntu, on effectue habituellement les tâches d’administration avec `sudo` à partir d’un compte autorisé.

```
sudo whoami
```

Cette commande affiche root lorsqu’elle est autorisée. Elle ne transforme pas définitivement votre terminal en session root : la commande suivante reste exécutée avec votre compte, sauf nouvelle demande de privilèges.

`sudo` demande habituellement votre propre mot de passe. Selon la configuration, la saisie peut ne rien afficher, même pas des astérisques. Tapez le mot de passe puis validez. Le compte utilisé doit avoir reçu l’autorisation d’administrer la machine.

### Garder une séparation claire

Utilisez votre compte ordinaire pour les exercices dans votre dossier personnel. Employez `sudo` lorsqu’une opération système le nécessite, par exemple la création d’un utilisateur. L’ajouter devant toutes les commandes risque de créer des fichiers appartenant à root et de masquer les problèmes de permissions que vous cherchez à comprendre.

Une session root peut contourner de nombreuses permissions classiques. Pour vérifier les droits d’Amélie, il faut exécuter le test avec son identité, et non simplement lancer cat avec `sudo`.

## Créer et gérer des comptes

Les commandes de cette section sont des opérations d’administration. Utilisez uniquement les comptes de laboratoire demandés. Un nom de compte simple, en minuscules et sans accent, facilite les manipulations.

### Créer un utilisateur sur Ubuntu

```
sudo adduser amelie
```

`adduser` pose les questions nécessaires, demande un mot de passe et crée habituellement le dossier `/home/amelie` ainsi qu’un groupe principal de même nom. Les champs complémentaires, comme le numéro de bureau, peuvent rester vides dans le laboratoire.

`adduser` est un outil pratique sur Ubuntu et Debian. `useradd` est un outil de plus bas niveau ; ses valeurs par défaut et ses options doivent être vérifiées. Ne considérez pas les deux noms comme interchangeables.

```
id amelie
getent passwd amelie
ls -ld /home/amelie
```

`id` vérifie l’identité et les groupes. `getent passwd` recherche les informations du compte dans les sources configurées. Sa sortie contient notamment l’UID, le GID, le dossier personnel et le shell. Le champ x n’est pas le mot de passe : les informations de vérification des mots de passe locaux sont normalement conservées dans `/etc/shadow`, dont l’accès est restreint.

### Gérer le mot de passe

| Commande                | Effet                                                                                          |
| ----------------------- | ---------------------------------------------------------------------------------------------- |
| `passwd`                | Changer le mot de passe de son propre compte.                                                  |
| `sudo passwd amelie`    | Définir un nouveau mot de passe pour Amélie.                                                   |
| `sudo passwd -e amelie` | Faire expirer le mot de passe pour demander son changement à la prochaine connexion concernée. |

### Ouvrir une session de test

```
su - amelie
whoami
pwd
exit
```

`su - amelie` ouvre un shell de connexion pour ce compte et demande normalement son mot de passe si vous n’êtes pas root. Le tiret charge son environnement de connexion. exit revient au shell précédent. Un administrateur peut aussi employer `sudo -iu amelie` si sa politique `sudo` le permet.

## Gérer les groupes et retirer un compte

Un groupe sert à réunir des utilisateurs qui ont besoin des mêmes accès. Pour un travail d’équipe, il est plus simple d’attribuer des droits au groupe equipe que de configurer séparément chaque personne.

```
sudo groupadd equipe
sudo usermod -aG equipe amelie
id amelie
getent group equipe
```

`groupadd` crée le groupe. `usermod` modifie le compte. Dans `-aG`, `-G` désigne les groupes supplémentaires et `-a` demande de les ajouter à la liste existante. Sans `-a`, la liste de groupes supplémentaires peut être remplacée : un utilisateur pourrait perdre des appartenances dont il a encore besoin.

Une session déjà ouverte conserve généralement son ancienne liste de groupes. Après l’ajout, fermez puis rouvrez la session d’Amélie. Un simple nouvel onglet de terminal dans la même session graphique peut ne pas suffire. Dans la nouvelle session, exécutez `id` sans nom de compte pour vérifier les groupes réellement actifs.

`getent group` equipe affiche les membres supplémentaires enregistrés pour ce groupe ; cette ligne ne donne pas nécessairement tous les utilisateurs qui l’ont comme groupe principal.

### Autres opérations courantes

| Commande                         | Effet                                                                    |
| -------------------------------- | ------------------------------------------------------------------------ |
| `sudo deluser amelie equipe`     | Retirer Amélie de ce groupe supplémentaire sur Ubuntu.                   |
| `sudo usermod -g equipe amelie`  | Changer son groupe principal ; ce n’est pas la même opération que -aG.   |
| `sudo groupmod -n projet equipe` | Renommer le groupe equipe en projet.                                     |
| `sudo groupdel projet`           | Supprimer le groupe lorsqu’il n’est plus utilisé comme groupe principal. |

Ces lignes présentent des opérations indépendantes. Ne les exécutez pas à la suite si les exercices suivants utilisent encore le groupe equipe.

### Supprimer un utilisateur

```
sudo deluser compteessai
```

Cette commande retire le compte, mais conserve normalement son dossier personnel. L’option `--remove-home` supprime aussi ce dossier et sa boîte de courrier locale : il faut donc vérifier et sauvegarder ce qui doit être conservé avant de l’utiliser.

Supprimer un compte ne retire pas automatiquement tous les fichiers qu’il possède ailleurs sur le système. De même, supprimer un groupe ne redistribue pas les fichiers associés à son ancien GID. Une suppression de compte ou de groupe se prépare ; elle ne se limite pas à faire disparaître un nom.

## Installer des applications &#x20;

Sur Ubuntu, on installe généralement les logiciels à l’aide d’un gestionnaire de paquets. Cet outil télécharge les fichiers nécessaires, réalise l’installation et permet ensuite de mettre à jour ou de supprimer le logiciel.

Trois termes sont à connaître :

* Un paquet contient les fichiers nécessaires à l’installation d’un logiciel ou d’un composant.
* Un dépôt est une source dans laquelle le système recherche les paquets disponibles.
* Une dépendance est un autre paquet nécessaire au fonctionnement du logiciel.

Par exemple, une application peut avoir besoin d’une bibliothèque pour afficher son interface. Le gestionnaire de paquets s’occupe généralement d’installer cette dépendance en même temps que l’application. Sur Ubuntu, on utilise notamment la commande `apt` .

### Comprendre une commande d’installation

Prenons cet exemple :

```
sudo apt install tree
```

| Élément   | Rôle                                                       |
| --------- | ---------------------------------------------------------- |
| `sudo`    | Exécuter la commande avec les privilèges d’administration. |
| `apt`     | Utiliser le gestionnaire de paquets.                       |
| `install` | Indiquer l’action à effectuer : installer.                 |
| `tree`    | Désigner le paquet à installer.                            |

Ici, install est une sous-commande, et non une option. Une option comme `-y` modifie le comportement de la commande.

L’outil tree permet d’afficher les dossiers et les fichiers sous forme d’arborescence.

### Actualiser la liste des paquets

Avant une installation, commencez par actualiser les informations sur les paquets disponibles :

```
sudo apt update
```

Cette commande contacte les dépôts configurés et récupère leur catalogue à jour.

Elle n’installe pas les mises à jour des logiciels. Elle permet simplement à Ubuntu de connaître les versions disponibles. Pour installer ces mises à jour, on utilise `upgrade`

### Rechercher un logiciel

Si vous ne connaissez pas le nom exact du paquet, effectuez une recherche :

```
apt search tree
```

Pour consulter sa description et ses caractéristiques :

```
apt show tree
```

Ces commandes servent à consulter des informations. Elles ne nécessitent normalement pas `sudo`.

Le nom d’un paquet n’est pas toujours identique au nom commercial de l’application. Il faut donc lire sa description avant de l’installer.

### Installer et vérifier un logiciel

Pour installer tree :

```
sudo apt install tree
```

APT présente les changements prévus : paquets à installer, dépendances éventuelles et espace nécessaire. Si une confirmation apparaît, lisez la liste avant de répondre avec la lettre indiquée à l’écran.

Une fois l’installation terminée, lancez le programme :

```
tree ~/LaboCLI
```

Cette commande affiche l’organisation du dossier `LaboCLI`, s’il existe.

Pour consulter l’état du paquet :

```
dpkg -s tree
```

Dans le résultat, la ligne suivante indique que le paquet est installé :

```
Status: install ok installed
```

Il est également possible d’installer plusieurs paquets dans une même commande :

```
sudo apt install tree nano
```

APT installe les paquets demandés et les dépendances nécessaires qu’il peut obtenir dans les dépôts configurés.

Vous rencontrerez parfois cette écriture :

```
sudo apt install -y tree
```

L’option `-y` accepte automatiquement les confirmations habituelles d’APT. Pour les premiers exercices, gardez la confirmation manuelle afin de prendre le temps de lire les changements proposés.

### Mettre à jour les logiciels

La mise à jour se fait habituellement en deux étapes :

```
sudo apt update
sudo apt upgrade
```

La première commande actualise le catalogue. La deuxième installe les mises à jour possibles des paquets déjà présents.

| Commande                | Effet                                                                      |
| ----------------------- | -------------------------------------------------------------------------- |
| `sudo apt update`       | Actualiser les informations sur les paquets disponibles.                   |
| `apt list --upgradable` | Afficher les paquets pour lesquels une mise à jour est disponible.         |
| `sudo apt upgrade`      | Installer les mises à jour proposées, sans supprimer de paquets installés. |

Certains paquets peuvent rester en attente si leur mise à jour exige d’autres changements. Par ailleurs, `apt upgrade` ne correspond pas à un passage vers une nouvelle version majeure d’Ubuntu.

### Désinstaller un logiciel

Pour retirer tree :

```
sudo apt remove tree
```

Cette commande désinstalle le paquet, mais conserve ses fichiers de configuration système gérés par le paquet.

Pour retirer également ces fichiers de configuration :

```
sudo apt purge tree
```

`remove` et `purge` sont deux choix possibles : il n’est pas nécessaire de lancer les deux. `purge` ne supprime généralement pas les documents ni les préférences enregistrées dans le dossier personnel des utilisateurs.

Après une désinstallation, certaines dépendances installées automatiquement peuvent être devenues inutiles :

```
sudo apt autoremove
```

Lisez la liste proposée avant de confirmer leur suppression.

### Installer un fichier téléchargé au format DEB

Un éditeur peut distribuer son logiciel sous forme de fichier `.deb`.

Placez-vous dans le dossier contenant ce fichier, puis utilisez :

```
sudo apt install ./application.deb
```

Remplacez `application.deb` par son vrai nom. Le préfixe `./` indique que le fichier se trouve dans le dossier courant. APT tente également d’installer les dépendances nécessaires depuis les dépôts configurés.

Téléchargez ce type de fichier depuis le site officiel de l’éditeur. Son installation ne garantit pas à elle seule que ses futures mises à jour seront proposées automatiquement : cela dépend notamment de l’ajout éventuel d’un dépôt par l’éditeur.

### Reconnaître les applications Snap

Ubuntu peut aussi installer des applications au format Snap. Elles se gèrent avec la commande snap.

| Action                       | Exemple                 |
| ---------------------------- | ----------------------- |
| Rechercher une application   | `snap find vlc`         |
| Installer une application    | `sudo snap install vlc` |
| Afficher les snaps installés | `snap list`             |
| Demander leur mise à jour    | `sudo snap refresh`     |
| Supprimer une application    | `sudo snap remove vlc`  |

Les snaps sont normalement mis à jour automatiquement. Une application installée avec `snap` doit être gérée avec `snap` : `apt remove` ne supprime pas sa version Snap.&#x20;

Pour les exercices, vérifiez d’abord le mode d’installation utilisé. Cela vous permettra de choisir la bonne commande pour mettre à jour ou désinstaller le logiciel.

## Repérer les disques et les partitions

Un disque est un support de stockage, physique ou virtuel. Une partition est une zone définie sur ce disque. Un système de fichiers, comme ext4, organise les fichiers dans cette zone. Enfin, le point de montage est le dossier à partir duquel on accède à ce système de fichiers.

Linux ne présente pas normalement les volumes sous forme de lettres C: ou D:. Ils sont intégrés à l’arborescence, par exemple à / ou à /mnt/labo.

```
lsblk -o NAME,SIZE,TYPE,FSTYPE,MOUNTPOINTS
lsblk -f
```

La première commande choisit explicitement les colonnes à afficher. La deuxième présente notamment le type de système de fichiers et l’UUID, un identifiant utile pour reconnaître un volume.

<figure><img src=".gitbook/assets/image (155).png" alt=""><figcaption></figcaption></figure>

Dans cet exemple , `sda` est un disque de 40 Go et `sda1` est sa partition ext4 montée sur `/`. `sdb` est un second disque de 8 Go ; `sdb1` est sa partition ext4, actuellement sans point de montage. L’absence de point de montage ne signifie pas que la partition est vide.

### Les noms peuvent changer

| Exemple          | Ce que le nom désigne                             |
| ---------------- | ------------------------------------------------- |
| `/dev/sda`       | Un disque entier.                                 |
| `/dev/sda1`      | La première partition de ce disque.               |
| `/dev/nvme0n1`   | Un espace de stockage NVMe présenté comme disque. |
| `/dev/nvme0n1p1` | Sa première partition.                            |

Vous pouvez aussi rencontrer `vda` dans une machine virtuelle, des périphériques loop ou des volumes logiques. La disposition réelle d’une installation Ubuntu peut être plus complexe que l’exemple.

Ne choisissez jamais un disque uniquement parce qu’il s’appelle `sdb`. Comparez sa taille, son modèle, ses partitions et ses points de montage. Les noms peuvent varier d’une machine à l’autre et après une modification du matériel.

## Mesurer et monter un système de fichiers

### Vérifier l’espace disponible

```
df -h
df -h /
du -sh ~/LaboCLI
```

`df` affiche l’espace utilisé et disponible dans les systèmes de fichiers montés. `df -h /` cible celui qui contient `/`. du mesure l’espace occupé par les éléments d’un dossier ; `-s` demande un total et `-h` rend les tailles lisibles.

`df` et `du` répondent donc à des questions différentes. Le premier permet de savoir si un volume est presque plein. Le second aide à trouver les dossiers qui occupent de l’espace. Leurs chiffres ne sont pas toujours identiques, notamment à cause des métadonnées ou de fichiers supprimés mais encore ouverts.

### Monter une partition déjà préparée

Dans l’exemple suivant,  `/dev/sdb1` est la partition ext4 du laboratoire. Elle existe, n’est pas montée et ne contient aucune donnée à protéger.&#x20;

```
sudo mkdir -p /mnt/labo
sudo mount /dev/sdb1 /mnt/labo
findmnt /mnt/labo
df -h /mnt/labo
ls -la /mnt/labo
```

`mount` rend le contenu du système de fichiers accessible à travers `/mnt/labo`. Il ne copie pas les fichiers dans ce dossier. Si le dossier contenait déjà des fichiers, ceux-ci seraient masqués pendant le montage, puis redeviendraient visibles après le démontage.

Monter un volume ne donne pas automatiquement le droit d’y écrire. Les permissions du système de fichiers monté continuent de s’appliquer. Sur ext4, un administrateur peut préparer un sous-dossier et lui attribuer un propriétaire et un groupe, comme dans les exemples de permissions.

### Démonter proprement

```
cd ~
sudo umount /mnt/labo
```

La commande s’écrit umount, sans n après le u. Quittez le point de montage et fermez les fichiers utilisés avant de démonter. Si le système indique target is busy, une session ou un programme utilise encore le volume. Ne forcez pas le démontage pour contourner ce message.

Un montage manuel n’est normalement pas rétabli au redémarrage. Le fichier `/etc/fstab` peut définir des montages persistants, généralement à l’aide d’UUID.&#x20;

## Préparer un nouveau disque de laboratoire

Partitionner et formater sont deux opérations différentes. Le partitionnement définit les zones du disque. Le formatage crée un système de fichiers dans une zone et rend les anciennes données de cette zone inutilisables par les accès habituels.

La procédure ci-dessous suppose un second disque virtuel neuf de 8 Go, identifié comme `/dev/sdb` . Elle ne doit jamais être appliquée au disque qui contient Ubuntu, au dossier personnel ou aux sauvegardes. Si l’identification est incertaine, arrêtez avant toute modification.

### Identifier le support

```
lsblk -o NAME,SIZE,MODEL,TYPE,FSTYPE,MOUNTPOINTS
sudo fdisk -l /dev/sdb
```

La première commande permet de comparer les supports. `fdisk -l` consulte la table de partitions ; l’option `-l` n’effectue pas un nouveau partitionnement.

### Créer une partition sur le disque neuf

`sudo fdisk /dev/sdb`

Dans l’interface de `fdisk`, suivez cette séquence uniquement sur le disque neuf confirmé :

| Saisie                                 | Action                                                                                              |
| -------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `g`                                    | Préparer une nouvelle table GPT ; cette opération remplacera la table existante lors de l’écriture. |
| `n puis Entrée aux trois propositions` | Créer une partition avec le numéro, le premier secteur et le dernier secteur proposés.              |
| `p`                                    | Relire la table prévue et vérifier le disque et la taille.                                          |
| `w`                                    | Écrire les modifications et quitter.                                                                |
| `q au lieu de w`                       | Quitter sans enregistrer les changements en attente.                                                |

### Formater puis vérifier

```
lsblk /dev/sdb
sudo mkfs.ext4 /dev/sdb1
lsblk -f /dev/sdb
```

Vérifiez que `/dev/sdb1` existe avant `mkfs.ext4`. La cible est ici la partition, et non le disque entier `/dev/sdb`. Le formatage est destructif pour les données de la partition ; il ne faut pas le relancer pour résoudre une erreur de montage.

Vous pouvez ensuite monter la partition avec la procédure de la page précédente. Une partition déjà formatée se monte directement : il n’est pas nécessaire de la reformater à chaque utilisation. Un contrôle avec `fsck` s’effectue généralement sur un système de fichiers démonté et demande une procédure adaptée ; ne le lancez pas au hasard sur un volume en cours d’utilisation.

## Lire les permissions Linux

Les permissions indiquent qui peut lire, modifier ou exécuter un élément. Dans le modèle classique, elles sont réparties entre le propriétaire, les utilisateurs qui appartiennent au groupe du fichier et les autres utilisateurs.

```
ls -l rapport.txt
```

<figure><img src=".gitbook/assets/image (156).png" alt=""><figcaption></figcaption></figure>

Le premier caractère indique le type : `-` pour un fichier ordinaire, `d` pour un dossier et `l` pour un lien symbolique. Il ne fait pas partie des trois triplets de permissions.

Les neuf caractères suivants forment trois blocs de trois positions. Leur ordre reste toujours le même : propriétaire, groupe, autres. À l’intérieur de chaque bloc, les positions correspondent à r, w et x. Un tiret signifie que la permission est absente.

| Bloc  | Personnes concernées                                   | Droits dans cet exemple      |
| ----- | ------------------------------------------------------ | ---------------------------- |
| `rw-` | amelie, propriétaire du fichier                        | Lire et modifier le contenu. |
| `r--` | Les membres du groupe equipe, hors cas du propriétaire | Lire le contenu.             |
| `---` | Les autres utilisateurs                                | Aucun droit sur le contenu.  |

### Lire toute la ligne

Après les permissions, le nombre 1 est le nombre de liens physiques. Les deux noms sont, dans l’ordre, le propriétaire puis le groupe du fichier. La taille, la date de modification et le nom viennent ensuite.

Le nom de groupe affiché par `ls -l` est donc essentiel. Le deuxième triplet ne concerne ni tous les groupes du propriétaire ni tous les utilisateurs de la machine. Il concerne le groupe associé à cet élément.

Pour examiner les permissions d’un dossier lui-même, utilisez `ls -ld nom_du_dossier`. Pour vérifier celles d’un fichier précis, donnez son nom à `ls -l`. Les couleurs d’affichage peuvent aider à se repérer, mais les caractères sont la référence à lire.

## Comprendre les droits sur un fichier et un dossier

Les lettres r, w et x ont des effets différents selon qu’elles s’appliquent à un fichier ou à un dossier.

| Droit          | Sur un fichier ordinaire                                                            | Sur un dossier                                                       |
| -------------- | ----------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| r pour read    | Lire son contenu.                                                                   | Lire la liste des noms qu’il contient.                               |
| w pour write   | Modifier son contenu.                                                               | Créer, supprimer ou renommer des entrées, avec x.                    |
| x pour execute | Autoriser son lancement comme programme, s’il est exécutable dans un format valide. | Traverser le dossier et accéder à un élément dont on connaît le nom. |

Pour travailler normalement dans un dossier, r et x sont souvent nécessaires ensemble. Avec r sans x, on peut obtenir une liste de noms sans pouvoir accéder normalement aux éléments. Avec x sans r, on peut accéder à un nom connu si les autres permissions le permettent, mais pas lister le dossier.

Donner x à un fichier texte ne le transforme pas en programme. Pour lancer un script avec ./script.sh, il faut aussi un contenu exécutable adapté, généralement un interpréteur indiqué et les accès nécessaires.

### Le chemin compte aussi

Pour lire `/srv/equipe/rapport.txt`, il faut pouvoir traverser chaque dossier du chemin, puis avoir le droit de lecture sur le fichier. Un fichier en 644 peut rester inaccessible si un dossier parent interdit le passage.

La suppression dépend surtout des permissions w et x sur le dossier parent, et non de w sur le fichier. Un utilisateur autorisé à modifier les entrées d’un dossier peut donc parfois supprimer un fichier qu’il ne peut pas modifier.&#x20;

### Quelle catégorie Linux utilise

Dans le modèle classique, Linux choisit une seule catégorie pour la vérification :

1\. Si le compte est propriétaire de l’élément, il utilise le triplet du propriétaire.

2\. Sinon, si l’un de ses groupes correspond au groupe de l’élément, il utilise le triplet du groupe.

3\. Sinon, il utilise le triplet des autres.

Les droits des trois catégories ne s’additionnent pas. Un propriétaire dont le triplet est `---` ne récupère pas les droits du groupe, même s’il en est membre.&#x20;

## Modifier les droits avec chmod

`chmod` modifie les permissions. Le propriétaire peut normalement changer les droits de ses fichiers ; l’administrateur peut aussi le faire. La commande ne change ni le propriétaire ni le groupe.

### La notation symbolique

| Élément    | Valeurs    | Sens                                                |
| ---------- | ---------- | --------------------------------------------------- |
| Catégorie  | u, g, o, a | Propriétaire, groupe, autres, tout le monde.        |
| Opération  | +, -, =    | Ajouter, retirer, fixer les droits de la catégorie. |
| Permission | r, w, x    | Lecture, écriture, exécution ou traversée.          |

```
sudo chmod g+w rapport.txt
sudo chmod o-r rapport.txt
sudo chmod u=rw,g=r,o= rapport.txt
```

`g+w` ajoute l’écriture au groupe sans modifier ses autres droits. `o-r` retire la lecture aux autres. La dernière commande fixe les trois catégories : lecture et écriture pour le propriétaire, lecture pour le groupe, aucun droit pour les autres.

Pour éviter de dépendre du masque de création du shell, indiquez explicitement la catégorie dans vos premières commandes symboliques. Écrivez par exemple `u+x`, et non simplement `+x`.

<figure><img src=".gitbook/assets/image (157).png" alt=""><figcaption></figcaption></figure>

### Appliquer des droits à un dossier

<pre><code><strong>sudo chmod u=rwx,g=rx,o= Projet
</strong>ls -ld Projet
</code></pre>

Le propriétaire peut lister le dossier, le traverser et modifier ses entrées. Les membres du groupe peuvent le lister et le traverser, mais pas y créer un fichier. Les autres n’ont aucun droit sur ce dossier.

### Se méfier des modifications récursives

`chmod -R` applique un changement au dossier et à son contenu. Un `chmod -R 755` rendrait aussi les fichiers ordinaires exécutables, ce qui est rarement le but. Les dossiers et les fichiers n’ont pas toujours besoin des mêmes droits.

Sur un ensemble bien identifié, X majuscule ajoute x aux dossiers et aux fichiers déjà exécutables pour au moins une catégorie. Par exemple, `chmod -R g+rX Projet` donne au groupe un accès en lecture et le passage nécessaire, sans rendre tous les fichiers texte exécutables. Vérifiez toujours l’étendue de l’opération avant d’utiliser `-R`.

## Calculer les permissions numériques

La notation numérique attribue une valeur à chaque permission : r vaut 4, w vaut 2 et x vaut 1. Pour un triplet, on additionne les valeurs des droits présents. Chaque résultat est un chiffre compris entre 0 et 7.

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td>Droits</td><td>Calcul</td><td>Chiffre</td></tr><tr><td><code>---</code></td><td>Aucun droit</td><td>0</td></tr><tr><td><code>--x</code></td><td>1</td><td>1</td></tr><tr><td><code>-w-</code></td><td>2</td><td>2</td></tr><tr><td><code>-wx</code></td><td>2 + 1</td><td>3</td></tr><tr><td><code>r--</code></td><td>4</td><td>4</td></tr><tr><td><code>r-x</code></td><td>4 + 1</td><td>5</td></tr><tr><td><code>rw-</code></td><td>4 + 2</td><td>6</td></tr><tr><td><code>rwx</code></td><td>4 + 2 + 1</td><td>7</td></tr></tbody></table>

<figure><img src=".gitbook/assets/image (158).png" alt=""><figcaption></figcaption></figure>

### Quelques choix courants

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td>Commande</td><td>Droits</td><td>Usage possible</td></tr><tr><td><code>chmod 600 secret.txt</code></td><td><code>rw-------</code></td><td>Fichier privé du propriétaire.</td></tr><tr><td><code>chmod 640 rapport.txt</code></td><td><code>rw-r-----</code></td><td>Fichier partagé en lecture.</td></tr><tr><td><code>chmod 644 notes.txt</code></td><td><code>rw-r--r--</code></td><td>Fichier lisible si le chemin est accessible.</td></tr><tr><td><code>chmod 700 Prive</code></td><td><code>rwx------</code></td><td>Dossier réservé au propriétaire.</td></tr><tr><td><code>chmod 750 Projet</code></td><td><code>rwxr-x---</code></td><td>Dossier consultable par le groupe.</td></tr><tr><td><code>chmod 770 Equipe</code></td><td><code>rwxrwx---</code></td><td>Dossier de travail pour le groupe.</td></tr></tbody></table>

Dans `chmod 640 rapport.txt`, le 6 concerne le propriétaire, le 4 le groupe et le 0 les autres. Ce sont trois chiffres en base huit, appelés chiffres octaux ; ils ne forment pas un score global de sécurité.

Sur un élément sans bits spéciaux, la notation à trois chiffres fixe les neuf permissions ordinaires. Elle remplace donc leurs valeurs précédentes. Les bits spéciaux, présentés plus loin, demandent une attention distincte, notamment sur les dossiers.

Évitez `777` comme solution générale à une erreur d’accès : tout utilisateur pourrait alors modifier les entrées du dossier ou le contenu du fichier concerné, sous réserve des autres protections. Identifiez la personne, son groupe et l’action dont elle a réellement besoin.

## Changer le propriétaire et le groupe

Les permissions définissent des droits pour des catégories. Il faut aussi que les bonnes personnes occupent ces catégories. Donner rw au groupe n’aide pas Amélie si elle n’appartient pas au groupe associé au fichier.

```
sudo chown amelie rapport.txt
sudo chown amelie:equipe rapport.txt
sudo chgrp equipe rapport.txt
ls -l rapport.txt
```

`chown amelie` change uniquement le propriétaire. `chown amelie:equipe` change le propriétaire et le groupe. `chgrp` equipe change uniquement le groupe. Changer le propriétaire demande normalement des privilèges d’administration. Le propriétaire peut généralement changer le groupe vers un groupe dont il est membre.

### Un dossier de travail pour Amélie et Bob

Dans cette suite, les comptes amelie et bob ainsi que le groupe equipe existent déjà. Les deux utilisateurs appartiennent à equipe et ont rouvert leur session. Le dossier `/srv/equipe` n’existe pas encore.

```
sudo mkdir /srv/equipe
sudo chown amelie:equipe /srv/equipe
sudo chmod 770 /srv/equipe
ls -ld /srv/equipe
```

Les trois derniers chiffres, `770`, donnent les droits complets au propriétaire et au groupe, aucun aux autres.&#x20;

### Créer un fichier avec les droits voulus

```
sudo -u amelie touch /srv/equipe/rapport.txt
sudo chmod 660 /srv/equipe/rapport.txt
ls -l /srv/equipe/rapport.txt
```

Le fichier appartient à Amélie et au groupe equipe. Le mode `660` autorise le propriétaire et le groupe à lire et modifier le contenu. On fixe explicitement ce mode, car l’héritage du groupe ne garantit pas à lui seul le droit d’écriture.

### Tester avec la bonne identité

```
sudo -u bob cat /srv/equipe/rapport.txt
sudo -u bob touch /srv/equipe/test-bob.txt
```

La lecture du fichier vide ne produit aucun texte si elle réussit. La création de `test-bob.txt` vérifie les droits sur le dossier. Vérifiez les deux résultats avec `ls -l` et, au besoin, le code de retour. `sudo cat rapport.txt`, exécuté en root, ne vérifierait pas les droits de Bob.



## Références&#x20;

Les manuels installés sur votre machine décrivent les options disponibles dans sa version. Consultez notamment `man ls`, `man chmod`, `man usermod`, `man lsblk`, `man mount` . Les ressources suivantes permettent d’approfondir le chapitre.

* GNU Coreutils, commandes de fichiers et permissions : https://www.gnu.org/software/coreutils/manual/coreutils.html
* GNU Coreutils, structure des permissions : https://www.gnu.org/s/coreutils/manual/html\_node/Mode-Structure.html
* GNU Coreutils, notation numérique : https://www.gnu.org/s/coreutils/manual/html\_node/Numeric-Modes.html
* GNU Bash, syntaxe, redirections et tubes : https://www.gnu.org/s/bash/manual/bash.html
* Ubuntu Server, gestion des utilisateurs : https://ubuntu.com/server/docs/how-to/security/user-management/
* Manuels Linux, disques et montages : https://man7.org/linux/man-pages/man8/lsblk.8.html et https://man7.org/linux/man-pages/man8/mount.8.html

&#x20;
