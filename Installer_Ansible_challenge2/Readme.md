## Enoncé
- Répétez le challenge précédent en configurant un dépôt PPA (Personal Package Archive) pour Ansible :
- $ sudo apt-add-repository ppa:ansible/ansible
- Notez la version fournie par ce dépôt tiers et comparez avec la version officielle du challenge précédent.

*Le challenge précédent* : 
- Démarrez la VM ubuntu depuis le répertoire atelier-01.
-  Connectez-vous à cette VM.
- Rafraîchissez les informations sur les paquets.
- Recherchez le paquet ansible avec les options qui vont bien.
- Installez le paquet officiel fourni par la distribution.
- Vérifiez si l'installation s'est bien déroulée.
- Notez la version d'Ansible.
- Déconnectez-vous et supprimez la VM.


## Commandes exécutées
- cd formation-ansible/atelier-01
- vagrant up ubuntu
- vagrant ssh ubuntu
- sudo apt update
- sudo apt-add-repository ppa:ansible/ansible
- sudo apt update
- sudo apt install -y ansible
- ansible --version *#la version est différente que dans le challenge 1*
- exit
- vagrant destroy -f ubuntu
