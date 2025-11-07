## Enoncé
   Pour vous familiariser avec la notion d'idempotence, exécutez une série de tâches administratives sur toutes les machines cibles. 
   
   Pour ce faire, servez-vous des commandes ad hoc que nous avons vues dans le précédent atelier pratique.
   
   Prenez soin d'exécuter chaque commande deux fois et observez ce qui se passe dans l'affichage du résultat.

    Installez successivement les paquets tree, git et nmap sur toutes les cibles.

    Désinstallez successivement ces trois paquets en utilisant le paramètre supplémentaire state=absent.

    Copiez le fichier /etc/fstab du Control Host vers tous les Target Hosts sous forme d'un fichier /tmp/test3.txt.

    Supprimez le fichier /tmp/test3.txt sur les Target Hosts en utilisant le module file avec le paramètre state=absent.

    Enfin, affichez l'espace utilisé par la partition principale sur tous les Target Hosts. Que remarquez-vous ?

## Commandes
- vagrant up
- vagrant ssh ansible
- cd ansible/projets/ema/
- ansible all -m package -a "name=tree"
- ansible all -m package -a "name=git"
- ansible all -m package -a "name=nmap"
- ansible all -m package -a "name=tree state=absent"
- ansible all -m package -a "name=git state=absent"
- ansible all -m package -a "name=nmap state=absent"
- ansible all -m copy -a "src=/etc/fstab dest=/tmp/test3.txt"
- ansible all -m file -a "path=/tmp/test3.txt state=absent"
- ansible all -m command -a "df -h /"  #*les 3 systèmes n'utilisent pas le même espace disque*
