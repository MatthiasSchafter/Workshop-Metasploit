# Workshop-Metasploit




1ère Étape : Téléchargements des ISOs :

Kali Linux :

https://cdimage.kali.org/kali-2020.4/kali-linux-2020.4-installer-amd64.iso

Metasploitable :

https://sourceforge.net/projects/metasploitable/

Une fois les ISOs téléchargés, installez en premier KALI LINUX sur une machine virtuelle (VMware / Virtualbox). 
Une fois cela fait, lancez directement le fichier "Metasploitable.vmx" situé dans le dossier compressé que vous avez téléchargé.

Un message va peut être s'afficher en vous demandant de mettre à jour la machine virtuelle, si c'est le cas, faites le.

Une fois la machine lancée, utilisez le username "msfadmin" et le password "msfadmin" pour déverouiller la machine. Attention le clavier est mis par défaut en QWERTY, utilisez la commande "loadkeys fr" pour remettre le clavier en AZERTY une fois le compte déverouillé.

Vos machines sont maintenant prêtes à être utilisées.




2ème Étape : Récupération de l’adresse IPv4 de la machine Metasploitable :

Pour récupérer l'adresse IP de votre machine, une multitude de commande existe. Pour ma part, j'utilise la commande 'ifconfig" qui me permet d'afficher les informations des interfaces réseau.

Une fois l’adresse. Ipv4 récupéré (sur la carte eth0), commence alors le travail d’analyse depuis le framework metasploit.




3ème étape : Par quoi commencer lors d’une analyse cyber ?

Plusieurs commandes existe pour analyser une machine, il existe également différents outils. 

La 1ère chose que tout cyber-analyste fait, c’est de regarder la liste des ports ouverts/fermés/filtrés.

La commande permettant de faire cela sur Linux s’appelle "nmap".
Sur Metasploit, cette dernière est appelé "db_nmap" et fonctionne comme la commande "nmap". Je vous invite donc à regarder le man de la commande pour comprendre son fonctionnement et son intérêt.
Une fois l’obtention des différentes versions, metasploit permet de chercher dans sa base de données des modules d’attaques. La commande à utiliser s’appelle search.

Pour vous aidez, nous allons effectuer la première attaque ensemble. Ensuite, en autonomie, vous rechercherez d’autres vulnérabilités à exploiter.
Effectuez une recherche grâce à la commande "search" (sur Metasploit) sur la version du port 21 (ftp) :

"search vsftpd"

Un module devrait s’afficher. Copiez le et exécutez la commande suivante :

"use  'nom_du_module'"

Ensuite pour afficher les options, ils vous suffit d’écrire "show options"

Vous pouvez alors voir que l’option RHOSTS n’est pas complétée, configurez la en lui attribuant l’adresse IP de la cible :

"set RHOSTS 'IP_CIBLE'"

Une fois cela fait, vous pouvez ré-exécutez la commande "show options" pour valider la nouvelle configuration d’attaque.

Il vous suffit de lancer la commande "exploit" afin d’exploiter la faille.

Une fois les premières vulnérabilités trouvées, renseignez vous sur internet en mettant la version du port trouvée ainsi que le mot clef « cve ». Le site « cvedetails.com » renseigne toutes les attaques (exploit) possibles sur chacune des vulnérabilités existantes selon l’application et ses versions.

Bonne chance pour les prochaines attaques !
