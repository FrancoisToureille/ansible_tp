## Enoncé
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
- apt-cache search --names-only ansible
- sudo apt install -y ansible
- ansible --version
- exit
- vagrant destroy -f ubuntu
