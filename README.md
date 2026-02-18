 # Automatisation des taches d’administration  

**SILLAH Sankou**  
**18/02/2026**  

# TP No 4 - Shell et processus  

---

## Objectif

L’objectif de ce TP est de comprendre le fonctionnement des processus sous Linux et d’apprendre à les observer, les analyser et les gérer à l’aide des outils du shell.

---

***EXERCICE 1 - Processus***

objectif : Utiliser ps, top et pstree pour observer les processus du système et répondre aux questions. 


1- Combien de processus sont lanc´e sur votre systeme ?

Commandes + Resultat: 
```code
sankou@p20220:~$ ps -e --no-headers | wc -l
215
```
Explication
ps -e liste tous les processus ; wc -l compte le nombre de lignes donc le nombre de processus.

2- Quels processus appartiennent votre utilisateur ?

Commandes + Resultat:

```code
sankou@p20220:~$ ps -u "$USER" -f

UID          PID    PPID  C STIME TTY          TIME CMD
sankou      1810       1  0 08:49 ?        00:00:00 /lib/systemd/systemd --user
sankou      1811    1810  0 08:49 ?        00:00:00 (sd-pam)
sankou      1825    1810  0 08:49 ?        00:00:00 /usr/bin/pipewire
sankou      1826    1810  0 08:49 ?        00:00:00 /usr/bin/pulseaudio --daemon
sankou      1829    1810  0 08:49 ?        00:00:00 /usr/bin/dbus-daemon --sessi
sankou      1831       1  0 08:49 ?        00:00:00 /usr/bin/gnome-keyring-daemo
sankou      1833    1825  0 08:49 ?        00:00:00 /usr/bin/pipewire-media-sess
sankou      1836    1800  0 08:49 ?        00:00:00 xfce4-session
sankou      1885    1836  0 08:49 ?        00:00:00 /usr/bin/ssh-agent x-session
sankou      1895    1810  0 08:49 ?        00:00:00 /usr/libexec/at-spi-bus-laun
sankou      1900    1895  0 08:49 ?        00:00:00 /usr/bin/dbus-daemon --confi
sankou      1904    1810  0 08:49 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xf
sankou      1910    1810  0 08:49 ?        00:00:00 /usr/libexec/at-spi2-registr
sankou      1914    1810  0 08:49 ?        00:00:00 /usr/bin/mate-screensaver --
sankou      1918    1810  0 08:49 ?        00:00:00 /usr/libexec/gvfsd
sankou      1931    1810  0 08:49 ?        00:00:00 /usr/bin/gpg-agent --supervi
sankou      1933    1836  1 08:49 ?        00:00:22 xfwm4
sankou      1941    1836  0 08:49 ?        00:00:00 xfsettingsd
sankou      1960    1836  1 08:49 ?        00:00:19 xfce4-panel
sankou      1964    1836  0 08:49 ?        00:00:00 Thunar --daemon
sankou      1969    1836  0 08:49 ?        00:00:03 xfdesktop
sankou      1972    1836  0 08:49 ?        00:00:00 /usr/lib/policykit-1-gnome/p
sankou      1973    1836  0 08:49 ?        00:00:00 /usr/bin/python3 /usr/share/
sankou      1974    1836  0 08:49 ?        00:00:00 xfce4-power-manager
sankou      1981    1836  0 08:49 ?        00:00:00 light-locker
sankou      1988    1836  0 08:49 ?        00:00:00 xiccd
sankou      1994    1836  0 08:49 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xf
sankou      1997    1836  0 08:49 ?        00:00:00 nm-applet
sankou      1999    1810  0 08:49 ?        00:00:00 /usr/libexec/dconf-service
sankou      2017    1960  0 08:49 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xf
sankou      2018    1960  0 08:49 ?        00:00:01 /usr/lib/x86_64-linux-gnu/xf
sankou      2019    1960  0 08:49 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xf
sankou      2020    1960  0 08:49 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xf
sankou      2036    1960  0 08:49 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xf
sankou      2063    1810  0 08:49 ?        00:00:00 /usr/libexec/gvfs-udisks2-vo
sankou      2068    1810  0 08:49 ?        00:00:00 /usr/libexec/gvfs-afc-volume
sankou      2073    1810  0 08:49 ?        00:00:00 /usr/libexec/gvfs-gphoto2-vo
sankou      2077    1810  0 08:49 ?        00:00:00 /usr/libexec/gvfs-mtp-volume
sankou      2081    1810  0 08:49 ?        00:00:00 /usr/libexec/gvfs-goa-volume
sankou      2093    1918  0 08:49 ?        00:00:00 /usr/libexec/gvfsd-trash --s
sankou      2098    1810  0 08:49 ?        00:00:00 /usr/libexec/gvfsd-metadata
sankou      2113    2102  0 08:49 ?        00:00:00 /usr/bin/veyon-worker {8e997
sankou      2128       1 11 08:50 ?        00:03:13 /usr/bin/x-www-browser
sankou      2164    1810  0 08:50 ?        00:00:00 /usr/libexec/xdg-desktop-por
sankou      2168    1810  0 08:50 ?        00:00:00 /usr/libexec/xdg-document-po
sankou      2171    1810  0 08:50 ?        00:00:00 /usr/libexec/xdg-permission-
sankou      2180    1810  0 08:50 ?        00:00:00 /usr/libexec/xdg-desktop-por
sankou      2192    1810  0 08:50 ?        00:00:00 /usr/bin/gnome-keyring-daemo
sankou      2232    2128  0 08:50 ?        00:00:01 /usr/lib/firefox-esr/firefox
sankou      2277    2128  0 08:50 ?        00:00:10 /usr/lib/firefox-esr/firefox
sankou      2316    2128  0 08:50 ?        00:00:00 /usr/lib/firefox-esr/firefox
sankou      2417    2128  0 08:50 ?        00:00:14 /usr/lib/firefox-esr/firefox
sankou      2637    2128  0 08:53 ?        00:00:00 /usr/lib/firefox-esr/firefox
sankou      2667    2128  8 08:53 ?        00:02:09 /usr/lib/firefox-esr/firefox
sankou      2703    2128  0 08:54 ?        00:00:00 /usr/lib/firefox-esr/firefox
sankou      2973    1918  0 08:55 ?        00:00:00 /usr/libexec/gvfsd-network -
sankou      2989    1918  0 08:55 ?        00:00:00 /usr/libexec/gvfsd-dnssd --s
sankou      3015    2128  1 08:55 ?        00:00:23 /usr/lib/firefox-esr/firefox
sankou      3216       1  0 08:59 ?        00:00:00 /usr/lib/libreoffice/program
sankou      3233    3216  3 08:59 ?        00:00:40 /usr/lib/libreoffice/program
sankou      3277    2128  0 09:00 ?        00:00:00 /usr/lib/firefox-esr/firefox
sankou      3280    2128  0 09:00 ?        00:00:00 /usr/lib/firefox-esr/firefox
sankou      3316    2128  0 09:00 ?        00:00:00 /usr/lib/firefox-esr/firefox
sankou      3350       1  0 09:00 ?        00:00:01 xfce4-terminal
sankou      3358    3350  0 09:00 pts/0    00:00:00 bash
sankou      3533    3358  0 09:18 pts/0    00:00:00 ps -u sankou -f
```

Explication
ps -u "$USER" filtre les processus appartenant à mon utilisateur ; -f affiche un format “long”.





















3- Combien de processus appartiennent `a root ?

Commandes + Resultat: 

```code
sankou@p20220:~$ ps -u root --no-headers | wc -l
132

```

Explication
On filtre sur l’utilisateur root, puis on compte. 



4- Quel est le processus qui a le plus petit PID ?

Commandes + Resultat: 
```code
sankou@p20220:~$ ps -e -o pid=,comm= | sort -n | head -n 1
      1 systemd
```
Explication
On affiche PID + commande, on trie par PID croissant, et on prend le premier.


5- Quelle est la m´emoire disponible sur votre syst`eme ? Quel processus occupe le plus le processeur ?

Commandes + Resultat:

```code
sankou@p20220:~$ top

top - 09:35:28 up 46 min,  1 user,  load average: 0,90, 0,45, 0,38
Tâches: 212 total,   1 en cours, 211 en veille,   0 arrêté,   0 zombie
%Cpu(s):  0,2 ut,  0,2 sy,  0,0 ni, 99,5 id,  0,1 wa,  0,0 hi,  0,0 si,  0,0 st
MiB Mem :   7726,4 total,   4200,4 libr,   1749,9 util,   1776,1 tamp/cache
MiB Éch :  32768,0 total,  32768,0 libr,      0,0 util.   5234,3 dispo Mem 

    PID UTIL.     PR  NI    VIRT    RES    SHR S  %CPU  %MEM    TEMPS+ COM.     
   3350 sankou    20   0  401740  48000  36272 S   1,7   0,6   0:03.04 xfce4-t+ 
    796 asterisk -11   0 3294256  78520  37024 S   1,3   1,0   0:28.45 asterisk 
   1566 root      20   0 1099100 112360  78896 S   1,3   1,4   3:29.20 Xorg     
   2102 root      20   0 1109332  99392  69952 S   1,0   1,3   0:20.99 veyon-s+ 
   3277 sankou    20   0 2946164 444584 112452 S   0,7   5,6   0:17.28 Isolate+ 
   3768 sankou    20   0   10404   4072   3296 R   0,7   0,1   0:00.03 top      
     13 root      rt   0       0      0      0 S   0,3   0,0   0:00.01 migrati+ 
    535 message+  20   0    9448   5424   3932 S   0,3   0,1   0:10.91 dbus-da+ 
    645 root      20   0 1504056  54116  29388 S   0,3   0,7   0:14.31 contain+ 
   2128 sankou    20   0 3800352 527092 191880 S   0,3   6,7   4:13.03 x-www-b+ 
   3398 root      20   0       0      0      0 I   0,3   0,0   0:00.48 kworker+ 
      1 root      20   0  167108  11144   7652 S   0,0   0,1   0:02.14 systemd  
      2 root      20   0       0      0      0 S   0,0   0,0   0:00.00 kthreadd 
      3 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 rcu_gp   
      4 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 rcu_par+ 
      6 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 kworker+ 
      8 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 mm_perc+
```



Explication : 

top permet d’observer en temps réel l’activité du système.
Elle affiche en haut des informations générales comme la charge CPU et l’état de la mémoire, puis en dessous la liste des processus en cours d’exécution.
Pour chaque processus on voit le PID, l’utilisateur, le pourcentage d’utilisation du processeur (%CPU), de la mémoire (%MEM) et la commande associée.
L’affichage se met à jour automatiquement toutes les quelques secondes.
On quitte avec la touche q.



6- D´ecrire ce qu’affiche la commande pstree.

Commandes + resultat : 
```code
sankou@p20220:~$ pstree
systemd─┬─ModemManager───2*[{ModemManager}]
        ├─NetworkManager───2*[{NetworkManager}]
        ├─accounts-daemon───2*[{accounts-daemon}]
        ├─2*[agetty]
        ├─apache2───5*[apache2]
        ├─asterisk─┬─astcanary
        │          └─66*[{asterisk}]
        ├─avahi-daemon───avahi-daemon
        ├─colord───2*[{colord}]
        ├─containerd───10*[{containerd}]
        ├─cron
        ├─dbus-daemon
        ├─gnome-keyring-d───3*[{gnome-keyring-d}]
        ├─gpm
        ├─libvirtd───18*[{libvirtd}]
        ├─lightdm─┬─Xorg───9*[{Xorg}]
        │         ├─lightdm─┬─xfce4-session─┬─Thunar───2*[{Thunar}]
        │         │         │               ├─applet.py
        │         │         │               ├─light-locker───3*[{light-locker}]
        │         │         │               ├─nm-applet───3*[{nm-applet}]
        │         │         │               ├─polkit-gnome-au───2*[{polkit-gnom+
        │         │         │               ├─ssh-agent
        │         │         │               ├─xfce4-notifyd───2*[{xfce4-notifyd+
        │         │         │               ├─xfce4-panel─┬─panel-10-notifi───2+
        │         │         │               │             ├─panel-14-action───2+
        │         │         │               │             ├─panel-6-systray───2+
        │         │         │               │             ├─panel-8-pulseau───2+
        │         │         │               │             ├─panel-9-power-m───2+
        │         │         │               │             └─2*[{xfce4-panel}]
        │         │         │               ├─xfce4-power-man───2*[{xfce4-power+
        │         │         │               ├─xfdesktop───2*[{xfdesktop}]
        │         │         │               ├─xfsettingsd───2*[{xfsettingsd}]
        │         │         │               ├─xfwm4───6*[{xfwm4}]
        │         │         │               ├─xiccd───2*[{xiccd}]
        │         │         │               └─2*[{xfce4-session}]
        │         │         └─2*[{lightdm}]
        │         └─2*[{lightdm}]
        ├─oosplash─┬─soffice.bin───3*[{soffice.bin}]
        │          └─{oosplash}
        ├─packagekitd───2*[{packagekitd}]
        ├─polkitd───2*[{polkitd}]
        ├─rsyslogd───3*[{rsyslogd}]
        ├─rtkit-daemon───2*[{rtkit-daemon}]
        ├─sshd
        ├─systemd─┬─(sd-pam)
        │         ├─at-spi-bus-laun─┬─dbus-daemon
        │         │                 └─3*[{at-spi-bus-laun}]
        │         ├─at-spi2-registr───2*[{at-spi2-registr}]
        │         ├─dbus-daemon
        │         ├─dconf-service───2*[{dconf-service}]
        │         ├─gnome-keyring-d───2*[{gnome-keyring-d}]
        │         ├─gpg-agent
        │         ├─gvfs-afc-volume───3*[{gvfs-afc-volume}]
        │         ├─gvfs-goa-volume───2*[{gvfs-goa-volume}]
        │         ├─gvfs-gphoto2-vo───2*[{gvfs-gphoto2-vo}]
        │         ├─gvfs-mtp-volume───2*[{gvfs-mtp-volume}]
        │         ├─gvfs-udisks2-vo───3*[{gvfs-udisks2-vo}]
        │         ├─gvfsd─┬─gvfsd-dnssd───2*[{gvfsd-dnssd}]
        │         │       ├─gvfsd-network───3*[{gvfsd-network}]
        │         │       ├─gvfsd-trash───2*[{gvfsd-trash}]
        │         │       └─2*[{gvfsd}]
        │         ├─gvfsd-metadata───2*[{gvfsd-metadata}]
        │         ├─mate-screensave───3*[{mate-screensave}]
        │         ├─pipewire─┬─pipewire-media-───{pipewire-media-}
        │         │          └─{pipewire}
        │         ├─pulseaudio───{pulseaudio}
        │         ├─xdg-desktop-por───5*[{xdg-desktop-por}]
        │         ├─xdg-desktop-por───3*[{xdg-desktop-por}]
        │         ├─xdg-document-po─┬─fusermount
        │         │                 └─5*[{xdg-document-po}]
        │         ├─xdg-permission-───2*[{xdg-permission-}]
        │         └─xfconfd───2*[{xfconfd}]
        ├─systemd-journal
        ├─systemd-logind
        ├─systemd-machine
        ├─systemd-timesyn───{systemd-timesyn}
        ├─systemd-udevd
        ├─udisksd───4*[{udisksd}]
        ├─unattended-upgr───{unattended-upgr}
        ├─upowerd───2*[{upowerd}]
        ├─usbmuxd───{usbmuxd}
        ├─veyon-service─┬─veyon-server─┬─veyon-worker───8*[{veyon-worker}]
        │               │              └─11*[{veyon-server}]
        │               └─3*[{veyon-service}]
        ├─wpa_supplicant
        ├─x-www-browser─┬─Isolated Web Co───22*[{Isolated Web Co}]
        │               ├─Isolated Web Co───26*[{Isolated Web Co}]
        │               ├─Privileged Cont───21*[{Privileged Cont}]
        │               ├─RDD Process───3*[{RDD Process}]
        │               ├─Socket Process───5*[{Socket Process}]
        │               ├─Utility Process───3*[{Utility Process}]
        │               ├─3*[Web Content───10*[{Web Content}]]
        │               ├─WebExtensions───21*[{WebExtensions}]
        │               ├─file:// Content───22*[{file:// Content}]
        │               └─130*[{x-www-browser}]
        └─xfce4-terminal─┬─bash───pstree
                         └─2*[{xfce4-terminal}]
```

**Explication**
pstree affiche les processus sous forme d’arbre : qui lance qui (relation parent → enfants). On voit la hiérarchie des processus, ce qui est plus lisible que la liste brute de ps.







***EXERCICE 2 - Code de statut d’une commande***

Objectif :  Comprendre et manipuler le code de retour (exit status) des commandes

1- En shell, comment obtenir le statut de la derni`ere commande lanc´ee ?

Commandes + resultat : 

Pour afficher le code de retour de la dernière commande exécutée, on utilise :
```code
sankou@p20220:~$ echo $?
0
```
Explication
La variable spéciale $? contient le code de retour de la commande précédente.




2- Comment terminer un script shell avec un code de statut détermine ?

Commandes + résultat : 

Dans un script shell, on utilise la commande :
```code
sankou@p20220:~$ exit 0
```
comme celle ci elle va donc nous permettre de quitter le terminal. 

Explication : 
en autre La commande exit permet de terminer le script et de renvoyer un code au système.

3- Quel code renvoie la commande ping vers une machine qui n’existe pas (nom introuvable) ?

Commandes + résultat : 
```code
sankou@p20220:~$ ping -c 1 moi
ping: moi: Nom ou service inconnu
sankou@p20220:~$ echo $?
2
```

Explication : 

Si le nom ne peut pas être résolu, ping échoue et renvoie un code différent de 0. Sur la plupart des systèmes Linux, le code renvoyé est 2 lorsque le nom est introuvable.
Il faut vérifier sur sa machine avec echo $? et dans mon cas donc il renvoie bien 2 









4- Quel code renvoie la commande ping vers l’IP d’une machine ´éteinte (request timeout).

Commandes + résultat : 
```code
sankou@p20220:~$ ping -c 1 192.0.2.1
PING 192.0.2.1 (192.0.2.1) 56(84) bytes of data.
^C
--- 192.0.2.1 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

sankou@p20220:~$ echo $?
1
```

Explication :

Lorsque l’on ping une machine éteinte ou inexistante, ping renvoie généralement le code 1.
Cela indique que la commande a fonctionné techniquement, mais que la communication réseau a échoué.
C’est important dans les scripts d’administration, car on peut tester ce code pour déclencher une alerte ou exécuter une action si le réseau est indisponible.

***EXERCICE 3 - Démarrage et paramétrage des services***

Objectif : Le but est de créer un script qui vérifie régulièrement la connexion réseau en envoyant deux requêtes ping vers www.iutv.univ-paris13.fr toutes les 60 secondes et qui enregistre le résultat avec la date et l’heure dans le fichier /var/log/test-reseau.log

1- Créez un script test-reseau.sh qui teste périodiquement (toutes les 60 secondes, par exemple) et indéfiniment la connexion au réseau en envoyant 2 requêtes ping à la machine www.iutv.univ-paris13.fr. Après chaque test, le script devra ajouter `a la
fin du fichier /var/log/test-reseau.log un message donnant la date et l’heure du
test ainsi que le résultat du test. Par exemple :
        samedi 10 sept 2016, 10:19:32 (UTC+0200): test ok (2/2)
        samedi 10 sept 2016, 10:20:32 (UTC+0200): test ok (2/2)
        samedi 10 sept 2016, 10:21:32 (UTC+0200): test pas ok (1/2)
  

Commandes + résultat :


```code
sankou@p20220:~$ sudo ./test-reseau.sh &
[1] 4741
sankou@p20220:~$ cd /var/log
sankou@p20220:/var/log$ ls
alternatives.log              debug           messages.1
alternatives.log.1            debug.1         private
apache2                       dpkg.log        runit
apt                           dpkg.log.1      speech-dispatcher
asterisk                      faillog         syslog
auth.log                      fontconfig.log  syslog.1
boot.log                      installer       test-reseau.log
boot.log.1                    journal         unattended-upgrades
bosc-fetch-update-script.log  kern.log        user.log
btmp                          kern.log.1      user.log.1
btmp.1                        lastlog         vbox-setup.log
cups                          libvirt         wtmp
daemon.log                    lightdm         Xorg.0.log
daemon.log.1                  messages
sankou@p20220:/var/log$ more test-reseau.log
mercredi 18 févr. 2026, 10:59:39 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:00:48 (CET+0100): test ok (2/2)
```

Explication : 

Le script a bien été lancé en arrière-plan avec sudo ce qui lui permet d’écrire dans le répertoire /var/log
On voit que le fichier test-reseau.log a bien été créé dans /var/log
La commande more permet de consulter son contenu et on constate que les lignes enregistrent correctement la date, l’heure et le résultat du test
Les messages test ok (2/2) signifient que les deux requêtes ping ont reçu une réponse donc la connexion réseau fonctionne correctement
Cela montre que le script fonctionne comme attendu et qu’il enregistre bien les résultats toutes les 60 secondes


2- Créez un service test-reseau qui permette de lancer/arreter ce script et de tester s’il est démarre (et, si c’est le cas, d’afficher son identifiant de processus, PID). 

Par exemple :
$ /etc/init.d/test-reseau status
Le service test-reseau est arrete.
$ /etc/init.d/test-reseau start
Service test-reseau demarre.
$ /etc/init.d/test-reseau status
Le service test-reseau est demarre (pid = 5483).
$ /etc/init.d/test-reseau stop
Service test-reseau arrete.
Remarque : le PID du service devra ˆetre sauvegard´e dans le fichier /var/run/test-reseau.pid.
Utilisez pour cela la variable $! qui contient le PID du processus en arri`ere-plan le plus
recent






***Commandes + résultat*** :

```code
sankou@p20220:~$ /etc/init.d/test-reseau start
Le service test-reseau est deja demarre.
sankou@p20220:~$ /etc/init.d/test-reseau status
Le service test-reseau est demarre (pid = 5033).
sankou@p20220:~$ /etc/init.d/test-reseau stop
/etc/init.d/test-reseau: ligne 18 : kill: (5033) - Opération non permise
rm: impossible de supprimer '/var/run/test-reseau.pid': Permission non accordée
Service test-reseau arrete.
```


**Explication** : 

Le script utilise une structure case pour gérer les trois actions start stop et status
Lorsque l’on lance start le script test-reseau.sh est exécuté en arrière-plan grâce au symbole &
La variable spéciale $! contient le PID du processus lancé en arrière-plan et ce PID est sauvegardé dans /var/run/test-reseau.pid
La commande stop lit le PID enregistré et utilise kill pour arrêter le processus puis supprime le fichier pid
La commande status vérifie si le fichier pid existe et si le processus correspondant est toujours actif avec ps
Cela permet de savoir si le service est démarré ou arrêté




3- Le système Debian utilise un mécanisme nomme ”SysVinit” (remplacé par system dans les nouvelles versions) pour g´erer les services, c’est `a dire les processus permanents
lancés au demarrage de la machine.
A l’aide de la commande ln, faites en sorte que le service test-reseau soit démarré
automatiquement lorsque votre machine démarré.
Redemarrez la machine et consultez les fichiers /var/log/boot.log
et /var/log/test-reseau.log pour v´erifier que le service test-reseau a bien ´et´e
d´emarr´e. V´erifiez aussi que le processus est bien pr´esent `a l’aide de la commande ps.


Ici on veut Configurer le service test-reseau pour qu’il démarre automatiquement au démarrage du système en utilisant le mécanisme SysVinit puis vérifier qu’il se lance correctement après redémarrage

***objectif***
Configurer le service test-reseau pour qu’il démarre automatiquement au démarrage du système en utilisant le mécanisme SysVinit puis vérifier qu’il se lance correctement après redémarrage
**commande + résultat**
```code
sankou@p20220:~$ sudo ln -s /etc/init.d/test-reseau /etc/rc2.d/S99test-reseau
[sudo] Mot de passe de sankou : 
```
ici Le S signifie start et Le nombre 99 indique l’ordre de lancement plus le nombre est élevé plus le service démarre tard

```code
sankou@p20220:~$ sudo less /var/log/boot.log
[sudo] Mot de passe de sankou : 
"/var/log/boot.log" may be a binary file.  See it anyway? 
```
Cela permet de voir si le service a été lancé pendant la séquence de démarrage

```code
sankou@p20220:~$ sudo less /var/log/test-reseau.log
mercredi 18 févr. 2026, 10:59:39 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:00:48 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:01:54 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:02:55 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:03:56 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:04:57 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:05:58 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:06:59 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:08:00 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:09:01 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:10:02 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:11:03 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:12:04 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:13:06 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:14:07 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:15:08 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:15:40 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:16:05 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:16:09 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:16:34 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:16:41 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:17:06 (CET+0100): test ok (2/2)
mercredi 18 févr. 2026, 11:17:10 (CET+0100): test ok (2/2)
```
de nouvelles lignes avec l’heure correspondant au redémarrage apparaissent

```code
sankou@p20220:~$ sudo /etc/init.d/test-reseau status
Le service test-reseau est demarre (pid = 898).
```
permet de verifié que le processus tourne bien. 

***Explication***
Avec la commande ln on crée un lien symbolique dans le niveau de démarrage du système
Au boot Debian exécute automatiquement tous les scripts commençant par S dans le répertoire rc correspondant
Cela permet de lancer le service sans intervention manuelle
La vérification se fait soit par les fichiers de log soit en contrôlant la présence du processus avec ps
Le service est maintenant configuré pour démarrer automatiquement au lancement du système


**Conclusion**
Ce TP m’a permis de comprendre concrètement le fonctionnement des processus sous Linux et la manière dont le système gère leur exécution
J’ai appris à utiliser des outils essentiels comme ps top et pstree pour observer les processus en cours et analyser l’utilisation des ressources
J’ai compris l’importance du code de retour d’une commande et comment l’exploiter dans un script pour savoir si une action a réussi ou échoué
La création du script test-reseau m’a permis de mettre en pratique les boucles les conditions la redirection vers un fichier log et la gestion des permissions système
La mise en place d’un service avec start stop status et la gestion du PID m’a permis de comprendre le fonctionnement d’un service système sous SysVinit
Enfin la configuration du démarrage automatique au boot m’a montré comment le système lance les services au démarrage et comment vérifier leur bon fonctionnement
Ce TP renforce les bases indispensables en administration système et montre comment automatiser et superviser proprement des tâches sous Linux
