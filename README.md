 # Table of contents 
 #### [1. Commencer Avec Git](#Commencer)
 #### [2. Récupérer le projet](#Recup)
 #### [3. Modifier le projet](#Modifier)
 #### [4. Régler les conflits](#Regler)
 #### [5. Les Branches](#Branches)

<a name="Commencer"/>

test

## 1. Commencer avec Git
### 1.1 Qu'est ce que c'est ?

Git est un outil de **versionning**. Cet outil va permettre à l'équipe de travailler en même temps sur le projet, sans devoir passer par du transfert de fichier de disque à disque ou par envoi etc.
De plus comme "versionning" l'indique, l'historique de toute les modifications apportées par chacun sera sauvegardé. Un bug, une erreur ? On retourne à la version précédente.

- **Premier concept :** Le projet est stocké en ligne par gitlab, avec les changements fait par tout le monde. Chaque personne possède un clone de celui-ci sur sa machine en local. Cette copie va permettre de modifier le projet sans interférer avec les autres.
<div align="center">
  <img src="https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/projects/develop-app-with-salesforce-cli-and-source-control/add-salesforce-dx-project-to-source-control/images/bf546ec3acd964673bf5f6302125fd93_step-4-github-and-git-clones.png"/>
</div>


- **Deuxième concept :** Les branches. 
Au début le projet possède une seule branche "main". On peux faire d'autres branches pour travailler sur des fonctionnalités et ainsi ne pas souffrir des modifications apportées par les autres sur le projet. En effet, ces modifications peuvent créent des conflit, des bugs ou tout simplement nous faire perdre le travail accompli.
Cela permet de garder la branche main propre et donc un projet propre et de **merge** la branche main avec la branche quand la fonctionnalité est finie.
Dans les faits, chacun aura sa propre branche et pourra **merge** son travail avec la branche dev. Après quoi, le chef de projet fera le **merge** de la branche dev vers la branche main. De cette manière, la branche main contiendra toujours une version du jeu considérée comme fonctionnelle.
<div align="center">
  <img src="https://delicious-insights.com/assets/images/articles/workflows-tags.png"/>
</div>

- **Troisième concept :** Le merge a lieu dans deux cas:
    - Quand le projet local est mis a jour avec la version en ligne.
    - Quand les modifications d'une branche sont fusionnées avec une autre.
Le merge se fait automatiquement dans la plupart des cas.

**ATTENTION**: Au moment du merge, il peux y avoir des conflits, votre projet local va passé en **état de "MERGING".**

### 1.2 Installation
1. ![Télécharger git] (https://git-scm.com/downloads)
2. Lancer l'exécutable
3. Cliquer sur "Next"
4. Choisir son dossier d'Installation et cliquer sur "Next"
5. Laisser les composants séléctionnés par défaut et cliquer sur "Next"
6. Choisir l'editeur de text que vous préferez ou avez parmis la liste déroulante, sinon laisser par défaut. Cliquer sur "Next"
7. Garder "Let git decide" et cliquer sur "Next"
8. Laisser la selection par défaut "Git from command line and also from 3rd-party software". Cliquer sur "Next"
9. Laisser "Use the openSSL Library" sélectionner par défaut. Cliquer "Next"
10. Choisir l'option "Checkout as-is, commit Unix-style line endings". Cliquer sur "Next"
11. Laisser "use MinTTY" par defaut. Cliquer sur "Next"
12. Laisser "Default (fast-forward or merge). Cliquer sur "Next"
13. Garder "Git Credential Manager Core". Cliquer "Next"
14. Garder les options cocher tel quel et cliquer sur "Next"
15. Décocher "Enable experimental support for pseudo consoles" et cliquer sur "Install"
17. Lancer l'exécutable et installer

### 1.3 Ouvrir git
Clic droit dans le dossier de votre choix
Sélectionner "Git Bash Here" pour ouvrir une console git dans ce dossier
![Git Bash Here](https://www.sitereq.com/uploads/Kanzi/postassets/fadysoliman160hotmailcom_3/git-bash-here-git-gui-here11222017022716.png)

### 1.4 Quelques visuels
#### La console git:
- **En Jaune:** Le chemin du dossier dans lequel vous vous trouvez
- **En Bleu:** Le nom de la branche sur laquelle vous êtes. N'apparaît que quand vous êtes dans un projet versionné avec Git.
![git Console](https://images4.programmersought.com/790/af/af411e1fc6089b9e9d48b617043a3e66.png)

#### Etat MERGING
Quand "MERGING" en bleu apparaît à côté du nom de la branche, cela signifie que vous avez des conflits à régler avant de pouvoir continuer
![Merging](https://sarafordnet.files.wordpress.com/2017/04/image_thumb48.png?w=449&h=179)

### 1.5 Bonnes pratiques
Quelques bonnes pratiques à respecter:
- Ne jamais utilisé le "camelCase" avec du "PascalCase" pour le nommage des fichiers/dossier, il faut choisir l'un ou l'autre et si tenir ( Ici, le **PascalCase**). Windows ne fait pas la différence mais git le fait et on peu se retrouver avec deux dossier portant le même nom. Se référer à la convention de nommage disponible sur le One Drive.
- Quand le projet rentre **en état de "MERGING"** à cause de conflits, **régler** les conflits, **sauvegarder** puis **pousser** vos modifications en ligne avant de continuer à modifier le projet.

<a name="Recup"/>

## 2. Récupérer le projet
> git clone https://github.com/Ynov-Lyon-JV/Bloodlines

A ce moment là, on vous demandera de vous identifier.

<a name="Modifier"/>

## 3. Modifier le projet
### 3.1 Sauvegarder ses modifications
> git add .

> git commit -m "{le message}"

### 3.2 Pousser ses modifications
Avant de pousser les modifications sur la version en ligne il faut d'abord les **sauvegarder** (cf. Sauvegarder ses modifications)
> git push

### 3.3 Vérifier le statut de vos modifications
> git status

- **red** : Les fichiers modifiés ne sont pas ajouter pour la **sauvegarde** (cf. Sauvegarder ses modifications)
- **green**: Les fichiers modifiés sont prêts à être commité pour la **sauvegarde** (cf. Sauvegarder ses modifications)

### 3.4 Mettre le projet en locale a jour
Avant de mettre votre projet à jour vous devez **sauvegarder** vos modifications (cf. Sauvegarder ses modifications)
> git pull

**ATTENTION**: Il peux y avoir un conflit et votre branche va passer en état de "Merge"

<a name="Regler"/>

## 4. Régler un conflit
Chercher dans la liste un peu plus haut le/les fichier(s) en état de conflit

Vous pouvez regler les conflits à la main ou deux autres solution s'offre a vous
### 4.1 Prendre vos modifications
> git checkout --ours {chemin du fichier}

### 4.2 Prendre les modifications de la version en ligne
> git checkout --theirs {chemin du fichier}

### 4.3 Vérifier les conflits
> git status

Une fois que les conflits sont fixés **sauvegarder** (cf. Sauvegarder ses modifications), puis **pousser** vos modifications (cf. Pousser ses modifications) pour acter le merge.

<a name="Branches"/>

## 5. Les branches
### 5.1 Crée une branche
> git checkout -b {nom de la branche}

La branche ne sera crée que localement il faudra ensuite la **mettre en ligne**

### 5.2 Mettre une branche en ligne
**Changer de branche** pour vous mettre sur celle que vous voulez mettre en ligne, si vous n'y êtes pas déja
> git push --set-upstream origin {nom de la branche}

### 5.3 Changer de branche
Avant de changer de branche assurez-vous d'avoir ** Sauvegarder** vos modifications (cf. Sauvegarder ses modifications)
> git checkout {nom de la branche}
