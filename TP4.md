# Exercice 1. Commandes de base
1)
```
sudo apt update
sudo apt upgrade
```
2)
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
3)
on peut voire dans le fichier   **/var/log/dpkg.log**
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
4)
```
ls -ltr /var/lib/dpkg/info/*.list
```
5)

```
dpkg --list | wc --lines
611
apt list --installed | wc --lines
606
(ps meme ,nombre en vrai)
```
6)
```
apt list |wc -l
68744
```

7)
le paquet **glances** permet grâce a la commande `glances` de lancé une interface similaire au gestionnaire des taches de Windows.
Cette interface indique les performance de la machine ,la mémoire utilisé ,les processus en cours ...

le paquet **tldr** permet grâce a la commande `tldr {commande}` permet de visionner les contenus d'une documentation de manière plus concise qu'avec la commande `man`

le paquet **hollywood** permet grâce a la commande `hollywood` de lancer une animation qui ressemble au animation utilisé dans les film (d’où sont nom) pour montré l'écran d'un développer ou d'un 'pirate'.L'animation est remplis de code et de caractère qui défile vite ,change de place et de couleur.

8)
`sudo apt-get install -y sudoku`

# Exercice 2.
Core Utilities

```
dpkg -S $(which {commande})

```
```
nano origine-commande
```
```bash
dpkg -S $(which $1)
```
`
bash origine-commande {commande}
`

TODO

which -a {commande} | xargs dpkg -S 2> /dev/null | cut -f1 -d:
chmod +x origine-commande (pour rendre executable)
# Exercice 3.
dpkg -L coreutils | grep "^ii" && echo "installer" || echo "non installer"

# Exercice 4.
dpkg -L coreutils

[ est un alias pour la commande test


# Exercice 5. aptitude
sudo aptitude

emacs est un editeur de texte
lynx est un navigateur web
# Exercice 6. Installation d’un paquet par PPA


ls /etc/apt/sources.list.d
linuxuprising-ubuntu-java-jammy.list


# Exercice 7. Installation d’un logiciel à partir du code source

# Exercice 8. Création de dépôt personnalisé



```
test
```
