
# Exercice 1. Commandes de base

1. Commencez par mettre à jour votre système avec les commandes vues dans le cours.

```
sudo apt update
sudo apt upgrade
```

2. Créez un alias “maj” de la ou des commande(s) de la question précédente. Où faut-il enregistrer cet alias pour qu’il ne soit pas perdu au prochain redémarrage ?

on edite le fichier **~/.bashrc** en rajouter en dessous de "_some more ls aliases_" :

  

```

alias agu='sudo apt-get update'

alias agg='sudo apt-get upgrade'

alias maj='agu && agg'

```

Pour que les alias soient pris en compte on fait la commande :

```

source ~/.bashrc

```

ensuite on peut faire la commande `maj` pour mettre à jour votre système avec les commandes vues dans le cours.

3. Utilisez le fichier /var/log/dpkg.log pour obtenir les 5 derniers paquets installés sur votre machine

on peut voire dans le fichier **/var/log/dpkg.log**

```

cat /var/log/dpkg.log

```

que les 5 dernier paquets installer sont :

```

- initramfs-tools:all 0.140ubuntu13

- dbus:amd64 1.12.20-2ubuntu4

- man-db:amd64 2.10.2-1

- libc-bin:amd64 2.35-0ubuntu3.1

- cryptsetup-initramfs:all 2:2.4.3-1ubuntu1.1

```

4. Listez les derniers paquets qui ont été installés explicitement avec la commande apt install

```

ls -ltr /var/lib/dpkg/info/*.list

```

5. Utilisez les commandes dpkg et apt pour compter de deux manières différentes le nombre de total de paquets installés sur la machine (ne pas hésiter à consulter le manuel !). Comment explique-t-on la (petite) différence de comptage ? Pourquoi ne peut-on pas utiliser directement le fichier dpkg.log

  

```

dpkg --list | wc --lines

611

apt list --installed | wc --lines

606

(ps meme ,nombre en vrai)

```

6. Combien de paquets sont disponibles en téléchargement sur les dépôts Ubuntu ?

```

apt list |wc -l

68744

```

  

7. A quoi servent les paquets glances, tldr et hollywood ? Installez-les et testez-les

le paquet **glances** permet grâce a la commande `glances` de lancé une interface similaire au gestionnaire des taches de Windows.

Cette interface indique les performance de la machine ,la mémoire utilisé ,les processus en cours ...

  

le paquet **tldr** permet grâce a la commande `tldr {commande}` permet de visionner les contenus d'une documentation de manière plus concise qu'avec la commande `man`

  

le paquet **hollywood** permet grâce a la commande `hollywood` de lancer une animation qui ressemble au animation utilisé dans les film (d’où sont nom) pour montré l'écran d'un développer ou d'un 'pirate'.L'animation est remplis de code et de caractère qui défile vite ,change de place et de couleur.

  

8. Quels paquets proposent de jouer au sudoku ?

`sudo apt-get install -y sudoku`

  

# Exercice 2.

A partir de quel paquet est installée la commande ls ?
Core Utilities

  

Comment obtenir cette information en une seule commande, pour n’importe quel programme ?
```
which -a $1
```
Utilisez la réponse à cette question pour écrire un script appelé origine-commande (sans l’extension .sh) prenant en argument le nom d’une commande, et indiquant quel paquet l’a installée.
```
nano origine-commande
```
```bash
which -a $1 | xargs dpkg -S 2> /dev/null | cut -f1 -d:
```
Utilisé :
```
chmod +x origine-commande (pour rendre executable)
bash origine-commande {commande}
```
Pour lancé le script.
  


# Exercice 3.
Ecrire une commande qui affiche “INSTALLÉ” ou “NON INSTALLÉ” selon le nom et le statut du package spécifié dans cette commande.
```
dpkg -L coreutils | grep "^ii" && echo "installer" || echo "non installer"
```

# Exercice 4.
Lister les programmes livrés avec coreutils. En particulier, on remarque que l’un deux se nomme [. De quoi s’agit-il ?
```
dpkg -L coreutils
```
[ est un alias pour la commande test


# Exercice 5. aptitude
Installez les paquets emacs et lynx à l’aide de la version graphique d’aptitude (et prenez deux minutes pour vous renseigner et tester ces paquets).
on utilise `sudo aptitude`  pour accédé a la version graphique d’aptitude 

emacs est un éditeur de texte
lynx est un navigateur web

# Exercice 6. Installation d’un paquet par PPA

  
vérifiez qu’un nouveau fichier a été créé dans /etc/apt/sources.list.d. Que contient-il ?
```
ls /etc/apt/sources.list.d
linuxuprising-ubuntu-java-jammy.list
cat linuxuprising-ubuntu-java-jammy.list
```


# Exercice 7. Installation d’un logiciel à partir du code source
2)
```
sudo apt install cbonsai
make install PREFIX=~/.local
sudo make install
sudo checkinstall
```


# Exercice 8. Création de dépôt personnalisé

  ```
dpkg-deb --build origine-commande
```

Création du dépôt personnel avec reprepro
```
tree
sudo apt update
```
