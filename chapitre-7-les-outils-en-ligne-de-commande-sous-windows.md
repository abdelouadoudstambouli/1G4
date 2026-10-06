---
hidden: true
---

# Chapitre 7 - Les outils en ligne de commande sous Windows

## Objectifs d'apprentissage&#x20;

* Se familiariser avec **CMD et PowerShell** et comprendre leur utilité sous Windows.
* Savoir **se déplacer dans les dossiers** et retrouver rapidement un fichier ou un emplacement.
* Utiliser les commandes de base pour **créer, copier, déplacer, renommer et supprimer** des fichiers et des dossiers.
* Savoir utiliser **l’aide intégrée** et comprendre les principaux messages affichés par les commandes.
* Utiliser **Exécuter** et quelques commandes simples pour accéder rapidement aux outils et informations du poste.

## Comprendre la ligne de commande

Avec l’Explorateur de fichiers, on ouvre généralement un dossier en double-cliquant dessus. En ligne de commande, on fait la même chose en indiquant le chemin du dossier à l’aide d’une commande. Dans les deux cas, on accède aux mêmes fichiers et aux mêmes dossiers, avec les mêmes droits d’accès.

La ligne de commande est surtout pratique lorsqu’on sait déjà ce qu’on veut faire. Elle permet d’exécuter rapidement une action, de refaire facilement une même manipulation ou de suivre une procédure étape par étape. L’interface graphique, de son côté, est souvent plus simple pour parcourir les dossiers et voir leur contenu. Dans la pratique, les deux méthodes peuvent être utilisées selon le besoin.

### Distinguer les outils

| **Outil**                  | **Rôle**                                                           | **Exemple d’utilisation**                     |
| -------------------------- | ------------------------------------------------------------------ | --------------------------------------------- |
| Invite de commandes ou CMD | Interpréter les commandes de cmd.exe et lancer des programmes.     | Afficher les fichiers avec dir.               |
| PowerShell                 | Exécuter des commandes et manipuler des informations structurées.  | Afficher les fichiers avec Get-ChildItem.     |
| Terminal Windows           | Héberger plusieurs sessions, souvent dans des onglets.             | Ouvrir un onglet CMD et un onglet PowerShell. |
| Exécuter                   | Ouvrir rapidement une application, un dossier ou un outil Windows. | Lancer la Calculatrice avec calc.             |

Terminal Windows est la fenêtre qui accueille une session. CMD ou PowerShell est le programme qui interprète ce qu’on y écrit. Deux onglets du même Terminal peuvent donc utiliser des commandes différentes. La couleur du fond ne permet pas de reconnaître l’interpréteur.

### Lire une invite de commande

Une invite indique que le programme attend une instruction. Dans CMD, elle peut ressembler à ceci :

```
C:\Users\Abdel>
```

Le texte avant le signe `>` représente ici le dossier courant. C’est le dossier dans lequel on se trouve. On écrit la commande après ce signe, puis on appuie sur Entrée.&#x20;

PowerShell affiche généralement une invite de ce type :

```
PS C:\Users\Abdel>
```

Le préfixe PS aide à reconnaître PowerShell. Ces invites peuvent être personnalisées, et le nom Abdel est seulement un exemple. Le chemin réellement affiché dépend du compte et du dossier courant.

Après une commande, la fenêtre peut afficher un résultat, un message d’erreur ou une nouvelle invite sans autre texte. Certaines commandes réussissent sans afficher de confirmation. On vérifie alors le résultat, par exemple en affichant le contenu du dossier.

### Comprendre la structure d’une commande

Une commande comprend un nom et, selon le besoin, des arguments et des options. Un argument précise sur quoi agir. Une option, aussi appelée paramètre selon l’outil, précise comment réaliser l’action.

Dans CMD :

```
dir "C:\Windows" /p
```

`dir` demande une liste. `"C:\Windows"` indique le dossier à consulter. `/p` demande un affichage écran par écran. Les espaces séparent les différentes parties de la commande.

Dans PowerShell :

```
Get-ChildItem -Path "C:\Windows" -Directory
```

`Get-ChildItem` demande le contenu d’un emplacement. `-Path` annonce le chemin à utiliser.     `-Directory` limite le résultat aux dossiers. Ce dernier paramètre est un commutateur : sa présence suffit, sans valeur supplémentaire.

Les noms de commandes restent en anglais, même lorsque Windows est en français. Pour les commandes présentées ici, les majuscules et les minuscules ne changent généralement pas le résultat. En revanche, un espace oublié, un mauvais caractère ou un chemin incorrect peut empêcher l’exécution.

### Les gestes utiles au clavier

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Touche</strong></td><td><strong>Utilisation courante</strong></td></tr><tr><td>Entrée</td><td>Exécuter la commande saisie.</td></tr><tr><td>Flèche vers le haut</td><td>Rappeler une commande précédente.</td></tr><tr><td>Flèche vers le bas</td><td>Revenir vers une commande plus récente dans l’historique.</td></tr><tr><td>Tabulation</td><td>Compléter un nom de fichier ou de dossier. PowerShell complète aussi les commandes et les paramètres.</td></tr><tr><td>Flèches gauche et droite</td><td>Déplacer le curseur pour corriger une partie de la ligne.</td></tr><tr><td>Ctrl + C</td><td>Interrompre une commande en cours, lorsqu’elle accepte cette interruption.</td></tr></tbody></table>

Dans Terminal Windows, **Ctrl + Maj + C** et **Ctrl + Maj + V** permettent généralement de copier et de coller du texte. Les raccourcis peuvent varier selon la fenêtre et sa configuration. Lorsqu’un texte est sélectionné, **Ctrl + C** peut aussi servir à le copier.

## Se repérer dans les fichiers et les dossiers

Un fichier contient des données : un texte, une image ou un programme, par exemple. Un dossier sert à organiser des fichiers et d’autres dossiers. L’ensemble forme une arborescence.

Un lecteur Windows est souvent identifié par une lettre. `C:` désigne généralement le volume où Windows est installé. Une lettre représente un volume accessible; elle ne correspond pas nécessairement à un disque physique distinct.

### Comprendre un chemin

Le chemin suivant indique l’emplacement d’un fichier :

```
C:\Users\Abdel\CoursCommandes\notes.txt
```

`C:\` est la racine du lecteur `C:`. `Users`, `Abdel` et `CoursCommandes` sont des dossiers successifs. `notes.txt` est le fichier. La barre oblique inverse, `\`, sépare les éléments du chemin. L’extension `.txt` indique habituellement un fichier texte.

L’Explorateur peut afficher des noms traduits, comme Utilisateurs, alors que le chemin utilisé par les commandes contient `Users`. Certains dossiers personnels peuvent aussi se trouver dans OneDrive. Le plus fiable est de vérifier le chemin réel au lieu de le deviner.

| **Type de chemin** | **Exemple**                             | **Point de départ**                |
| ------------------ | --------------------------------------- | ---------------------------------- |
| Absolu             | C:\Users\Abdel\CoursCommandes\notes.txt | La racine du lecteur indiqué.      |
| Relatif            | notes.txt                               | Le dossier courant.                |
| Relatif            | .\Archives\notes.txt                    | Le dossier courant, puis Archives. |
| Relatif            | ..\notes.txt                            | Le dossier parent.                 |

Le point `.` désigne le dossier courant. Les deux points `..` désignent son parent, c’est-à-dire le dossier qui le contient. Un chemin relatif peut donc viser des endroits différents selon le dossier courant. Un chemin absolu conserve le même point de départ.

Il faut aussi distinguer `C:\` et `C:`. Dans CMD, écrire `C:` sert à sélectionner le lecteur `C`; cela ne signifie pas forcément revenir à sa racine.

### Les espaces et les guillemets

Un nom peut contenir des espaces, comme Projet Windows. On entoure alors le chemin de guillemets droits pour qu’il soit traité comme un seul élément :

```
cd "Projet Windows"
```

L’habitude de mettre les chemins entre guillemets est utile dans les deux interpréteurs. Les commandes de ce cours utilisent des guillemets droits ". Les guillemets typographiques « » qui encadrent parfois une citation ne doivent pas les remplacer.

### Les variables d’environnement

Une variable d’environnement contient une information connue de Windows. `USERPROFILE` contient le chemin du profil du compte courant. Elle évite d’écrire un nom d’utilisateur qui serait différent sur chaque poste.

Dans CMD, cette variable s’écrit `%USERPROFILE%`. Dans PowerShell, elle s’écrit `$env:USERPROFILE`. La fenêtre Exécuter accepte aussi la forme `%USERPROFILE%`.

| **Environnement** | **Exemple**        | **Effet**                            |
| ----------------- | ------------------ | ------------------------------------ |
| CMD               | echo %USERPROFILE% | Afficher le chemin du profil.        |
| PowerShell        | $env:USERPROFILE   | Afficher le chemin du profil.        |
| Exécuter          | %USERPROFILE%      | Ouvrir le profil dans l’Explorateur. |

Ces écritures ne sont pas interchangeables. PowerShell n’interprète pas `%USERPROFILE%` comme le fait CMD.

## Utiliser l’invite de commandes

L’invite de commandes est aussi appelée CMD, d’après le programme **cmd.exe**. On peut l’ouvrir en recherchant Invite de commandes dans Démarrer, ou en saisissant cmd dans la fenêtre Exécuter, accessible avec **Windows + R.**

Une fenêtre normale suffit pour les manipulations de fichiers dans son propre profil. Exécuter en tant qu’administrateur accorde des possibilités supplémentaires, mais n’est pas nécessaire pour apprendre à naviguer. Les permissions NTFS continuent de s’appliquer en ligne de commande.

### Trouver de l’aide

La commande help présente une liste de commandes courantes. Pour obtenir de l’aide sur une commande précise, on peut ajouter son nom :

```
help
help dir
dir /?
```

`help dir` et `dir /?` donnent des renseignements sur `dir`. Le paramètre `/?` est reconnu par de nombreux outils Windows, mais ce n’est pas une règle universelle pour tous les logiciels. L’aide fournie avec la commande reste la meilleure façon de vérifier ses options.

Dans une aide, les crochets indiquent généralement un élément facultatif. Par exemple, `/d` est facultatif dans la syntaxe de `cd`. Les indications comme `<chemin>` représentent une valeur à remplacer; les chevrons ne doivent pas être tapés. Les exemples complets permettent de voir immédiatement une syntaxe utilisable.

### Afficher le dossier courant et son contenu

```
cd
dir
```

`cd` sans argument affiche le dossier courant. dir en présente les fichiers et les sous-dossiers. Dans la liste, la mention `<DIR>` identifie un dossier. Pour un fichier, on voit notamment son nom, sa taille en octets et sa date de modification.

Quelques variantes de `dir` répondent à des besoins différents :

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Commande CMD</strong></td><td><strong>Résultat</strong></td></tr><tr><td><pre><code>dir /p
</code></pre></td><td>Afficher la liste écran par écran.</td></tr><tr><td><pre><code>dir /b
</code></pre></td><td>Afficher principalement les noms.</td></tr><tr><td><pre><code>dir /a
</code></pre></td><td>Inclure les éléments cachés et système.</td></tr><tr><td><pre><code>dir /s
</code></pre></td><td>Parcourir aussi les sous-dossiers.</td></tr><tr><td><pre><code>dir *.txt
</code></pre></td><td>Rechercher les noms correspondant au motif *.txt.</td></tr><tr><td><pre><code>dir "C:\Windows"
</code></pre></td><td>Consulter ce dossier sans s’y déplacer.</td></tr></tbody></table>

L’astérisque `*` représente une partie variable du nom. Dans un dossier contenant `notes.txt`, `cours.txt` et `photo.jpg`, le motif `*.txt` permet de repérer les deux fichiers texte. Avant d’utiliser un motif pour une opération qui modifie ou supprime des fichiers, on examine la liste des éléments correspondants.&#x20;

### Changer de dossier ou de lecteur

Ces exemples montrent différentes façons de se déplacer. Un dossier mentionné doit déjà exister.

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Commande CMD</strong></td><td><strong>Effet</strong></td></tr><tr><td><pre><code>cd "Archives"
</code></pre></td><td>Entrer dans le sous-dossier Archives du dossier courant.</td></tr><tr><td><pre><code>cd ..
</code></pre></td><td>Remonter d’un niveau.</td></tr><tr><td><pre><code>cd \
</code></pre></td><td>Revenir à la racine du lecteur courant.</td></tr><tr><td><pre><code>cd /d "%USERPROFILE%"
</code></pre></td><td>Aller dans son profil, même s’il est sur un autre lecteur.</td></tr><tr><td><pre><code>D:
</code></pre></td><td>Passer au lecteur D, s’il existe.</td></tr><tr><td><pre><code>cd /d "D:\Cours"
</code></pre></td><td>Changer à la fois de lecteur et de dossier.</td></tr></tbody></table>

Le paramètre `/d` est utile lorsqu’un chemin mène vers un autre lecteur. Sans lui, `cd` ne sélectionne pas forcément ce lecteur. Changer de dossier modifie uniquement l’emplacement courant : aucun fichier n’est déplacé.

Une deuxième fenêtre CMD possède son propre dossier courant. Se déplacer dans la première ne change pas l’emplacement de la deuxième.

### Créer un dossier

mkdir crée un dossier. La création et le déplacement sont deux actions distinctes :

```
cd /d "%USERPROFILE%"
mkdir CoursCommandes1G4
cd CoursCommandes1G4
mkdir "Projet Windows"
mkdir Archives
```

Cet exemple crée `CoursCommandes1G4` dans le profil, y entre, puis crée deux sous-dossiers. À la fin, le dossier courant est toujours `CoursCommandes1G4`. `mkdir` ne fait pas entrer automatiquement dans le dossier créé.

La suite des exemples CMD suppose cet emplacement et ces deux sous-dossiers. Si un dossier existe déjà, `mkdir` peut le signaler : cela ne veut pas dire que le dossier a été supprimé. La commande `dir` permet de vérifier ce qui est présent.

### Créer et lire un fichier texte

`echo` affiche un texte à l’écran :

```
echo Premier cours
```

Le signe `>` redirige ce texte vers un fichier :

```
echo Premier cours>notes.txt
```

Cette commande crée notes.txt dans le dossier courant. Si ce fichier existe déjà, son contenu est remplacé. Le symbole `>` est donc une instruction de redirection lorsqu’il apparaît dans une commande; il ne joue pas le même rôle que le signe affiché à la fin de l’invite.

Pour ajouter une ligne sans remplacer les précédentes, on utilise `>>` :

```
echo Deuxieme ligne>>notes.txt
type notes.txt
```

`type` affiche le contenu du fichier dans la fenêtre. Le fichier contient maintenant les deux lignes. Ces exemples utilisent du texte simple; `type` n’est pas un lecteur de documents Word ou PDF.

Une extension ne transforme pas le contenu d’un fichier. Renommer `notes.txt` en `notes.docx` ne crée pas un document Word valide.

### Copier un fichier

Copier crée un deuxième fichier tout en conservant l’original. Dans l’exemple, Archives existe déjà :

```
copy /-y notes.txt "Archives\notes_copie.txt"
```

`notes.txt` est la source. `Archives\notes_copie.txt` est la destination. Le fichier copié peut donc recevoir un autre nom. `/-y` demande une confirmation si un fichier portant déjà ce nom risque d’être remplacé.&#x20;

Après la copie, modifier `notes.txt` ne met pas automatiquement à jour `notes_copie.txt`. Il s’agit de deux fichiers indépendants.

`copy` sert ici à copier un fichier. La copie complète d’une arborescence demande d’autres options ou outils, comme `robocopy`; elle ne se déduit pas de cet exemple.

### Renommer puis déplacer un fichier

`ren` change le nom d’un fichier sans changer son emplacement :

```
ren notes.txt cours.txt
```

Le deuxième argument est le nouveau nom, pas un nouveau chemin. Après cette commande, `notes.txt` s’appelle `cours.txt`.

`move` permet ensuite de déplacer ce fichier :

```
move cours.txt "Projet Windows\cours.txt"
```

Le fichier original se trouve maintenant dans Projet Windows. Il n’est plus à la racine de CoursCommandes. La copie `notes_copie.txt` reste dans Archives.

Pour vérifier ce déplacement, on peut afficher `dir "Projet Windows"` ou consulter ce dossier dans l’Explorateur. Renommer change le nom; déplacer change l’emplacement.

### Supprimer un fichier ou un dossier

`del` supprime un fichier. `/p` demande une confirmation avant la suppression :

```
del /p "Archives\notes_copie.txt"
```

La réponse demandée dépend de la langue de Windows. Il faut lire le message avant de confirmer. La suppression par `del` ne place normalement pas le fichier dans la Corbeille.

Une fois Archives vide, `rmdir` peut retirer ce dossier :

```
rmdir Archives
```

`rmdir` sans option refuse de supprimer un dossier contenant encore des éléments. On doit aussi se trouver en dehors du dossier à supprimer. L’option `/s` supprime une arborescence et son contenu : elle ne doit pas être ajoutée simplement pour faire disparaître un message d’erreur

### Quelques commandes utiles pour observer le poste

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Commande CMD</strong></td><td><strong>Utilité</strong></td></tr><tr><td><pre><code>cls
</code></pre></td><td>Effacer l’affichage de la fenêtre.</td></tr><tr><td><pre><code>hostname
</code></pre></td><td>Afficher le nom de l’ordinateur.</td></tr><tr><td><pre><code>whoami
</code></pre></td><td>Afficher l’identité du compte utilisé.</td></tr><tr><td><pre><code>ipconfig
</code></pre></td><td>Afficher les principaux paramètres des interfaces réseau.</td></tr><tr><td><pre><code>ipconfig /all
</code></pre></td><td>Afficher davantage de détails réseau.</td></tr><tr><td><pre><code>exit
</code></pre></td><td>Fermer cette session CMD.</td></tr></tbody></table>

`cls` ne supprime aucun fichier. `exit` ferme la session; dans Terminal Windows, cela peut fermer l’onglet correspondant.

`ipconfig` peut présenter plusieurs cartes réseau. L’adresse d’une carte VMware sur l’ordinateur physique n’est pas nécessairement celle de la VM. Il faut lire le nom de l’interface et exécuter la commande sur la machine dont on cherche l’adresse.

La commande `ipconfig` sert ici à observer. Ses autres options peuvent modifier la configuration réseau; elles ne sont pas nécessaires pour afficher une adresse.

## Découvrir PowerShell

PowerShell est un interpréteur de commandes et un langage d’automatisation. On peut commencer à l’utiliser avec des commandes simples, sans écrire de programme.

Pour ouvrir Windows PowerShell, on peut le rechercher dans Démarrer ou saisir powershell dans Exécuter. La valeur suivante permet de consulter la version de la session :

```
$PSVersionTable.PSVersion
```

Pour suivre les exemples, une session normale suffit. Il n’est pas nécessaire de modifier la stratégie d’exécution des scripts pour saisir ces commandes interactives.

### Lire le nom d’une commande PowerShell

Les commandes propres à PowerShell sont souvent appelées cmdlets. Leur nom associe un verbe et un nom, séparés par un tiret :

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Commande</td><td>Sens du nom</td></tr><tr><td><pre><code>Get-Location
</code></pre></td><td>Obtenir l’emplacement courant.</td></tr><tr><td><pre><code>Set-Location
</code></pre></td><td>Changer l’emplacement courant.</td></tr><tr><td><pre><code>Get-ChildItem
</code></pre></td><td>Obtenir les éléments contenus dans un emplacement.</td></tr><tr><td><pre><code>New-Item
</code></pre></td><td>Créer un élément.</td></tr><tr><td><pre><code>Copy-Item
</code></pre></td><td>Copier un élément.</td></tr><tr><td><pre><code>Remove-Item
</code></pre></td><td>Supprimer un élément.</td></tr></tbody></table>

Le mot Item signifie ici élément. Dans les exemples du cours, il désigne un fichier ou un dossier. Les paramètres rendent l’action plus précise :

```
New-Item -Path ".\Archives" -ItemType Directory
```

`New-Item` est la commande. `-Path` précise l’emplacement à créer. `-ItemType` précise le type d’élément. `Directory` signifie dossier. Le point de `.\Archives` indique que le dossier sera créé dans l’emplacement courant.&#x20;

### Trouver une commande et comprendre son fonctionnement

`Get-Command` aide à retrouver un nom :

```
Get-Command *-Item
```

L’astérisque élargit la recherche. Le résultat contient les commandes disponibles dont le nom se termine par `-Item`.

`Get-Help` explique ensuite une commande :

```
Get-Help Copy-Item
Get-Help Copy-Item -Examples
Get-Help Copy-Item -Full
```

`-Examples` demande des exemples. `-Full` demande l’aide détaillée. L’aide locale peut être incomplète lorsque ses fichiers n’ont pas été téléchargés. On peut alors consulter la documentation dans un navigateur :

```
Get-Help Copy-Item -Online
```

Cette dernière commande nécessite une connexion Internet. `Update-Help` sert à télécharger les fichiers d’aide; cette mise à jour n’est pas obligatoire pour utiliser les commandes du cours.

Dans une syntaxe d’aide, `<String>` désigne une valeur textuelle à fournir. Ce n’est pas un mot à recopier. L’écriture `[-Path]` indique que le nom du paramètre peut être omis dans certaines positions; elle ne signifie pas toujours que la valeur du chemin est facultative. Au début, écrire les noms complets des paramètres rend les commandes plus faciles à lire.&#x20;

### Naviguer dans les dossiers

```
Get-Location
Get-ChildItem
```

`Get-Location` affiche l’emplacement courant. `Get-ChildItem` affiche les éléments qu’il contient. Les informations affichées comprennent généralement le nom, la date de modification et, pour les fichiers, la taille. Une ligne correspondant à un dossier n’a pas la même signification qu’une ligne correspondant à un fichier.

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Commande PowerShell</strong></td><td><strong>Effet</strong></td></tr><tr><td><pre><code>Set-Location -Path $env:USERPROFILE
</code></pre></td><td>Aller dans le profil du compte courant.</td></tr><tr><td><pre><code>Set-Location -Path "C:\"
</code></pre></td><td>Aller à la racine de C:.</td></tr><tr><td><pre><code>Set-Location -Path ".."
</code></pre></td><td>Remonter dans le dossier parent.</td></tr><tr><td><pre><code>Set-Location -Path ".\Archives"
</code></pre></td><td>Entrer dans le sous-dossier Archives.</td></tr><tr><td><pre><code>Set-Location -Path "D:\Cours"
</code></pre></td><td>Aller dans ce dossier, si le lecteur et le dossier existent.</td></tr></tbody></table>

`Set-Location` change aussi de lecteur lorsque le chemin le demande. Le paramètre `/d` propre à CMD n’a pas à être ajouté dans PowerShell.

`Get-ChildItem` peut consulter un autre dossier sans changer l’emplacement courant :

```
Get-ChildItem -Path "C:\Windows"
```

Pour préciser la liste, on peut ajouter `-File` pour les fichiers seulement, `-Directory` pour les dossiers seulement, `-Recurse` pour inclure les sous-dossiers ou `-Force` pour inclure notamment les éléments cachés. `-Force` ne contourne pas les permissions NTFS.&#x20;

### Les alias et leurs limites

Un alias est un nom court qui renvoie à une autre commande. Dans PowerShell sous Windows, dir correspond habituellement à `Get-ChildItem` et `cd` à `Set-Location`.

```
Get-Alias dir
Get-Alias cd
```

Ces raccourcis expliquent pourquoi certaines commandes semblent fonctionner dans les deux environnements. Pourtant, leurs options ne deviennent pas celles de CMD. Par exemple, `dir /s` est une syntaxe CMD; dans PowerShell, on écrit `Get-ChildItem -Recurse`.

Les exemples du cours utilisent les noms complets pour montrer clairement quelle commande PowerShell est exécutée.

## Manipuler les fichiers avec PowerShell

Les exemples suivants utilisent un dossier CoursPowerShell, distinct du dossier CoursCommandes1G4 utilisé précédemment. Ils peuvent donc être étudiés sans avoir exécuté les exemples CMD.

Le bloc suivant illustre la création de ce dossier dans le profil, puis le déplacement à l’intérieur :

```
Set-Location -Path $env:USERPROFILE
New-Item -Path ".\CoursPowerShell" -ItemType Directory
Set-Location -Path ".\CoursPowerShell"
```

La suite suppose que ce dossier existe et qu’il est le dossier courant. Si `New-Item` indique qu’il existe déjà, on vérifie son contenu avant de poursuivre. Ajouter `-Force` pour masquer le problème n’est pas une réponse automatique.

### Créer un fichier vide et un sous-dossier

```
New-Item -Path ".\notes.txt" -ItemType File
New-Item -Path ".\Archives" -ItemType Directory
```

File désigne un fichier et Directory un dossier. notes.txt est créé vide. `New-Item` affiche généralement des renseignements sur l’élément créé. On peut aussi vérifier le résultat avec `Get-ChildItem.`

Le chemin `.\notes.txt` dépend du dossier courant. Avant une création, `Get-Location` permet donc de confirmer l’endroit où le nouvel élément apparaîtra.

### Écrire et lire du texte

`Set-Content` écrit du contenu dans un fichier :

```
Set-Content -Path ".\notes.txt" -Value "Premier cours" -Encoding UTF8
```

`-Value` fournit le texte à écrire. `-Encoding UTF8` choisit un encodage capable de représenter notamment les caractères accentués. `Set-Content` crée le fichier s’il manque, mais remplace son contenu s’il existe déjà.

`Add-Content` ajoute du texte à la fin :

```
Add-Content -Path ".\notes.txt" -Value "Deuxieme ligne" -Encoding UTF8
```

`Get-Content` permet de lire le résultat dans la console :

```
Get-Content -Path ".\notes.txt"
```

Le contenu affiché comporte ici deux lignes. `Set-Content`, `Add-Content` et `Get-Content` ont des rôles différents : remplacer ou créer le contenu, ajouter du contenu, puis le consulter. Un fichier Word ou une image ne se lit pas de cette façon.&#x20;

### Copier un fichier

```
Copy-Item -Path ".\notes.txt" -Destination ".\Archives\notes_copie.txt"
```

Cette commande copie `notes.txt` dans le sous-dossier `Archives` qui existe déjà. L’original reste en place. `-Destination` précise le chemin du résultat.

Une copie peut remplacer un fichier déjà présent à la destination. Pour demander une confirmation, on peut ajouter `-Confirm` :

```
Copy-Item -Path ".\notes.txt" -Destination ".\notes_copie.txt" -Confirm
```

La copie complète d’un dossier et de ses sous-dossiers utilise `-Recurse`. L’exemple suivant suppose que `Archives` existe et que `CopieArchives` n’existe pas encore :

```
Copy-Item -Path ".\Archives" -Destination ".\CopieArchives" -Recurse
```

`CopieArchives` contient alors une copie du contenu d’`Archives`. L’état initial de la destination compte : lorsque la destination est déjà un dossier, le résultat peut être imbriqué différemment. Il faut donc vérifier les chemins avant de relancer une copie.&#x20;

### Renommer et déplacer

```
Rename-Item -Path ".\notes.txt" -NewName "cours.txt"
```

`Rename-Item` change le nom. `-NewName` contient seulement le nouveau nom, sans chemin de destination.

```
Move-Item -Path ".\cours.txt" -Destination ".\Archives\cours.txt"
```

`Move-Item` change ensuite l’emplacement du fichier. `Archives` doit exister dans cet exemple. Après le déplacement, `cours.txt` se trouve dans `Archives` et n’est plus dans le dossier courant.

Une nouvelle exécution de la même commande ne produit pas forcément le même résultat : le fichier source a changé de place. Un message indiquant qu’il est introuvable peut simplement refléter ce déplacement déjà effectué.&#x20;

### Prévisualiser une suppression

Plusieurs commandes PowerShell qui modifient des éléments acceptent `-WhatIf`. Ce paramètre décrit l’action prévue sans l’effectuer.

```
Remove-Item -Path ".\Archives\notes_copie.txt" -WhatIf
```

Le fichier reste présent. Pour le supprimer en demandant une confirmation, la commande devient :

```
Remove-Item -Path ".\Archives\notes_copie.txt" -Confirm
```

`-WhatIf` sert à prévisualiser. `-Confirm` demande une confirmation avant l’action réelle. Une prévisualisation aide à vérifier la cible; elle ne garantit pas qu’aucune erreur ne surviendra lors de l’exécution.

`Remove-Item` peut aussi supprimer un dossier. Pour un dossier et tout son contenu, `-Recurse` élargit la portée de la suppression. Dans cet exemple, on examine seulement ce qui serait supprimé :

```
Remove-Item -Path ".\CopieArchives" -Recurse -WhatIf
```

Les suppressions de fichiers effectuées avec `Remove-Item` ne passent normalement pas par la Corbeille. Avant de confirmer, il faut vérifier le dossier courant, le chemin ciblé et le contenu concerné.&#x20;

### Comprendre les objets et le pipeline

`Get-ChildItem` renvoie des objets qui représentent les fichiers et les dossiers. Un objet regroupe des informations, appelées propriétés : le nom, la taille ou la date de modification, par exemple. PowerShell peut utiliser ces propriétés pour organiser le résultat.

Le symbole `|`, appelé pipeline, transmet les résultats d’une commande à la suivante :

```
Get-ChildItem -File | Sort-Object -Property Length -Descending
```

`Get-ChildItem -File` récupère les fichiers du dossier courant. `Sort-Object` les classe selon Length, leur taille en octets. `-Descending` place les plus grands en premier.

Cette commande change l’ordre de présentation, pas les fichiers sur le disque. La barre `|` ne signifie pas simplement « puis » : elle transmet des données entre les commandes. Avec les cmdlets de cet exemple, ce sont des objets qui circulent.&#x20;

## Utiliser la fenêtre Exécuter

La fenêtre Exécuter s’ouvre avec `Windows + R`. Elle permet de saisir le nom d’une application, un chemin ou une instruction de lancement. Après validation, Windows ouvre l’élément demandé.&#x20;

Exécuter est un lanceur. Elle n’offre pas une session de travail avec un dossier courant affiché et une succession de résultats comme CMD ou PowerShell.

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Texte à saisir dans Exécuter</strong></td><td><strong>Élément ouvert</strong></td></tr><tr><td>cmd</td><td>Invite de commandes.</td></tr><tr><td>powershell</td><td>Windows PowerShell.</td></tr><tr><td>calc</td><td>Calculatrice.</td></tr><tr><td>notepad</td><td>Bloc-notes.</td></tr><tr><td>explorer</td><td>Explorateur de fichiers.</td></tr><tr><td>taskmgr</td><td>Gestionnaire des tâches.</td></tr><tr><td>control</td><td>Panneau de configuration.</td></tr><tr><td>msinfo32</td><td>Informations système.</td></tr><tr><td>winver</td><td>Informations sur la version de Windows.</td></tr><tr><td>eventvwr.msc</td><td>Observateur d’événements.</td></tr><tr><td>services.msc</td><td>Console des services.</td></tr><tr><td>ncpa.cpl</td><td>Connexions réseau.</td></tr><tr><td>ms-settings:</td><td>Application Paramètres.</td></tr></tbody></table>

Les extensions `.msc` et `.cpl` apparaissent dans plusieurs noms d’outils d’administration. Une console `.msc` regroupe des fonctions d’administration. Un élément `.cpl` correspond à un module du Panneau de configuration. Certains outils ou réglages peuvent être limités par les droits du compte et la configuration du poste.

### Ouvrir directement un emplacement

Exécuter accepte aussi un chemin :

```
C:\Windows
%USERPROFILE%
```

Chaque ligne est un exemple distinct à saisir dans Exécuter. La première ouvre le dossier Windows. La seconde ouvre le profil de l’utilisateur.

On peut également y saisir un chemin de partage, par exemple `\\NOM_VM\Partage`. L’Explorateur tente alors d’ouvrir ce partage. `NOM_VM` et `Partage` doivent être remplacés par les valeurs réelles; les exigences réseau, l’authentification et les permissions restent applicables.

### Lancer une commande qui affiche un résultat

Saisir directement `ipconfig` dans Exécuter peut ouvrir une fenêtre qui se referme aussitôt le programme terminé. Pour conserver le résultat visible, on peut ouvrir CMD et lui demander de rester actif :

```
cmd /k ipconfig
```

`/k` demande à CMD d’exécuter `ipconfig`, puis de rester ouvert. `/c` exécute une commande, puis termine CMD. La différence concerne donc la durée de vie de la session après la commande.

Une commande interne de CMD, comme `dir`, n’est pas un programme autonome que la fenêtre Exécuter peut lancer seule. Elle peut être transmise à CMD :

```
cmd /k dir
```

La session affiche alors le contenu de son dossier de départ. Pour choisir précisément le dossier, on utilise ensuite les commandes de navigation vues précédemment.

## Lire un message et corriger une erreur

Un message d’erreur renseigne sur ce qui a empêché l’action. Il faut d’abord lire la commande et identifier sa cible. Relancer immédiatement la même instruction produit souvent le même message.

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td><strong>Message ou situation</strong></td><td><strong>Explication possible</strong></td><td><strong>Vérification utile</strong></td></tr><tr><td>Commande non reconnue</td><td>Faute dans le nom, mauvais interpréteur ou programme indisponible.</td><td>Vérifier le nom, l’onglet utilisé et l’aide.</td></tr><tr><td>Chemin ou fichier introuvable</td><td>Mauvais dossier courant, erreur de chemin ou fichier déjà déplacé.</td><td>Afficher l’emplacement et le contenu du dossier.</td></tr><tr><td>Accès refusé</td><td>Le compte n’a pas les permissions nécessaires.</td><td>Vérifier la cible et les autorisations, plutôt que passer systématiquement en administrateur.</td></tr><tr><td>Le fichier ou le dossier existe déjà</td><td>Le nom est déjà utilisé.</td><td>Examiner l’élément existant avant de le remplacer.</td></tr><tr><td>Fichier utilisé par un autre processus</td><td>Une application peut le maintenir ouvert.</td><td>Enregistrer le travail et fermer l’application concernée.</td></tr><tr><td>PowerShell affiche >> au début d’une nouvelle ligne</td><td>L’instruction est incomplète, par exemple à cause d’un guillemet non fermé.</td><td>Annuler la saisie avec Ctrl + C, puis corriger la commande.</td></tr><tr><td>Aucune confirmation après une commande</td><td>La commande peut avoir réussi silencieusement.</td><td>Vérifier le résultat avec dir ou Get-ChildItem.</td></tr></tbody></table>

L’invite de continuation `>>` de PowerShell ne doit pas être confondue avec l’opérateur `>>` que l’on saisit dans CMD pour ajouter du texte à un fichier.

Lorsqu’on apprend, il est préférable de saisir une commande à la fois. On peut ainsi relier chaque résultat à l’instruction qui vient d’être exécutée. Avant de coller plusieurs lignes, on vérifie ce qu’elles font : les retours à la ligne peuvent lancer plusieurs actions.

Les commandes qui suppriment ou remplacent du contenu demandent une attention particulière. Une ligne courte peut viser de nombreux fichiers lorsqu’elle contient un astérisque ou une option qui parcourt les sous-dossiers.

## Retrouver une commande selon le besoin

Les deux colonnes ci-dessous présentent des équivalents pour les opérations étudiées. Elles ne signifient pas que toutes les options d’un environnement fonctionnent dans l’autre.

<table data-header-hidden data-search="false"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td><strong>Besoin</strong></td><td><strong>CMD</strong></td><td><strong>PowerShell</strong></td></tr><tr><td>Consulter l’aide d’une commande</td><td><pre><code>dir /?
</code></pre></td><td><pre><code>Get-Help Get-ChildItem
</code></pre></td></tr><tr><td>Afficher le dossier courant</td><td><pre><code>cd
</code></pre></td><td><pre><code>Get-Location
</code></pre></td></tr><tr><td>Afficher le contenu du dossier</td><td><pre><code>dir
</code></pre></td><td><pre><code>Get-ChildItem
</code></pre></td></tr><tr><td>Changer de dossier</td><td><pre><code>cd "Archives"
</code></pre></td><td><pre><code>Set-Location -Path ".\Archives"
</code></pre></td></tr><tr><td>Remonter d’un niveau</td><td><pre><code>cd ..
</code></pre></td><td><pre><code>Set-Location -Path ".."
</code></pre></td></tr><tr><td>Créer un dossier</td><td><pre><code>mkdir Archives
</code></pre></td><td><pre><code>New-Item -Path ".\Archives" -ItemType Directory
</code></pre></td></tr><tr><td>Lire un fichier texte</td><td><pre><code>type notes.txt
</code></pre></td><td><pre><code>Get-Content -Path ".\notes.txt"
</code></pre></td></tr><tr><td>Copier un fichier</td><td><pre><code>copy notes.txt copie.txt
</code></pre></td><td><pre><code>Copy-Item -Path ".\notes.txt" -Destination ".\copie.txt"
</code></pre></td></tr><tr><td>Renommer un fichier</td><td><pre><code>ren notes.txt cours.txt
</code></pre></td><td><pre><code>Rename-Item -Path ".\notes.txt" -NewName "cours.txt"
</code></pre></td></tr><tr><td>Déplacer un fichier</td><td><pre><code>move cours.txt Archives
</code></pre></td><td><pre><code>Move-Item -Path ".\cours.txt" -Destination ".\Archives"
</code></pre></td></tr><tr><td>Supprimer avec confirmation</td><td><pre><code>del /p copie.txt
</code></pre></td><td><pre><code>Remove-Item -Path ".\copie.txt" -Confirm
</code></pre></td></tr><tr><td>Fermer la session</td><td><pre><code>exit
</code></pre></td><td><pre><code>exit
</code></pre></td></tr></tbody></table>

Pour retrouver une opération, on commence par identifier l’environnement utilisé, le dossier courant et l’élément concerné. L’aide permet ensuite de vérifier la syntaxe exacte.

## Références&#x20;

Les références suivantes sont utilisées pour le développement du cours. Elles peuvent également être consultées pour obtenir une documentation plus approfondie.

Présentation de Terminal Windows. [Microsoft](https://learn.microsoft.com/windows/terminal/)

Premiers pas avec PowerShell. [01-getting-started](https://learn.microsoft.com/powershell/scripting/learn/ps101/01-getting-started)

Raccourcis clavier Windows. [Microsoft](https://support.microsoft.com/accessibility/windows/keyboard-shortcuts-in-windows)

Aide de cmd.exe. [cmd](https://learn.microsoft.com/windows-server/administration/windows-commands/cmd)
