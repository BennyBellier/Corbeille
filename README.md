<img src="https://upload.wikimedia.org/wikipedia/commons/0/07/Logo_Universit%C3%A9_Grenoble_Alpes_2020.svg" alt="Logo UGA" width="200"/>

# Programmation shell : Corbeille 

## Sujet 

L'objectif de cette APNEE est de réaliser un script implémentant un système de gestion de fichiers mis au rebus similaire à la corbeille présente dans la plupart des interfaces graphiques. Les différentes parties sont progressives et vous permettent de construire votre script de manière incrémentale. Pensez à conserver une copie de votre travail à chaque étape afin de pouvoir revenir dessus lors de vos révisions.

Votre travail sera donc d'écrire un script corbeille qui évoluera pour implémenter les fonctionnalités suivantes :
1. Dans sa première version, le script **corbeille** devra déplacer tous les fichiers dont les noms lui seront donnés en arguments de la ligne de commande dans le répertoire **\$HOME/.corbeille** en créant au préalable ce répertoire s'il n'existe pas. Nous supposerons que les noms de fichier donnés sont absolus ou relatifs au répertoire courant. Attention, n'oubliez pas que les noms de fichier peuvent être quelconques et, par exemple, contenir des caractères particuliers (espace, ?, *, ...). D'après vous, pourquoi le nom du répertoire **\$HOME/.corbeille** comporte-t-il un point ? D'après vous, comment devez vous traiter le cas d'arguments qui ne correspondent pas à un nom de fichier ?
2. votre script doit maintenant accepter une commande comme premier argument. Cette commande pourra être :
    - **efface** : dans ce cas, les arguments qui suivent la commande correspondront à des noms de fichier à déplacer vers le répertoire **\$HOME/.corbeille** (comme dans le cas de la question précédente);
    - **restaure** : dans ce cas, les arguments qui suivent la commande correspondront à des noms de fichier à déplacer depuis le répertoire **\$HOME/.corbeille** vers le répertoire courant. Le nom de chaque fichier à restaurer devra être donné tel qu'il était avant effacement du fichier et ce nom sera le nom du fichier une fois restauré (on restaure à l'endroit original). **Attention** si un nom de fichier comporte des repertoires intermédiaires, il faudra créer ceux-ci s'ils n'existent pas (ou plus);
    - **info** : dans ce cas, pour chacun des arguments qui suivent la commande, il faudra afficher les infos concernant les fichiers de nom correspondant (s'ils se trouvent dans la corbeille, depuis combien de temps, ...). Si aucun argument n'est donné, il faudra afficher des infos sur tous les fichiers contenus dans la corbeille;
    - **vide** : dans ce cas, il faudra supprimer de la corbeille les fichiers dont le nom sera donné en argument de la commande ou vider totalement la corbeille si aucun argument n'est donné. 
Attention, pour cette question vous aurez à stocker, sous la forme que vous voudrez, des meta informations sur les fichiers de la corbeille, en particulier la localisation originale de chaque fichier.
3. votre script doit maintenant accepter une option *-r* permettant de rechercher récursivement. La manière de traiter cette recherche va dépendre de la commande donnée :

    - **efface** : le fichier est recherché dans la sous arborescence enracinée dans le répertoire courant;
    - **restaure** : le fichier est recherché dans tous les fichiers de la corbeille dont la position originale se trouvait dans la sous arborescence enracinée dans le répertoire courant.

Si plusieurs fichiers correspondent, il faudra donner le choix à l'utilisateur entre annuler, appliquer l'opération à l'un d'entre eux ou appliquer l'opération à tous les fichiers trouvés. Ce choix pourra être fait à l'avance par l'utilisateur en utilisant une option de la ligne de commande que vous choisirez et implémenterez.

4. votre script doit maintenant permettre de restaurer ou vider des fichiers effacés durant un certain intervalle de temps qui sera donné en option de la ligne de commande. Cet intervalle ne sera pas forcément fini (par exemple l'utilisateur devra pouvoir appliquer une opération aux fichiers effacés avant une certaine date sans limite d'ancienneté). Vous remarquerez que si un fichier est effacé plusieurs fois (effacé, recréé, puis effacé à nouveau), le contenu du fichier ne sera pas forcément le même selon l'intervalle de temps précisé par l'utilisateur. Vous gèrerez cette situation en conservant plusieurs versions distinctes d'un fichier effacé plusieurs fois.

5. si nous supposons que les différentes versions d'un fichier effacé plusieurs fois ont un contenu qui varie peu, il est intéressant de ne stocker dans la corbeille que la différence entre les différentes versions. Implémentez cette solution. Quelle problème cette solution pose-t-elle en cas d'effacement d'une partie des versions ? Comment pouvez vous résoudre ce problème ?

## To use it
Clone the repository, and run with
```
./corbeille.sh [command] ...
```
If you didn't use it correctly an error will appear !

## BE AWARE
The programme will use your current directory, to us it, on all over your computer use this command :
```
mkdir $HOME/bin
mv corbeille.sh $HOME/bin/
mv corbeille_function.sh $HOME/bin/
```
Check that you are in the folder that contain "corbeille.sh" and "corbeille_function.sh".
Then after that you are able to just run it with
```
corbeille [command] ...
```
in every directory.
