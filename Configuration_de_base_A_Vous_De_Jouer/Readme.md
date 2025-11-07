## Enoncé
    Éditez /etc/hosts de manière à ce que les Target Hosts soient joignables par leur nom d'hôte simple.

    Configurez l'authentification par clé SSH avec les trois Target Hosts.

    Installez Ansible.

    Envoyez un premier ping Ansible sans configuration.

    Créez un répertoire de projet ~/monprojet.

    Créez un fichier vide ansible.cfg dans ce répertoire.

    Vérifiez si ce fichier est bien pris en compte par Ansible.

    Spécifiez un inventaire nommé hosts.

    Activez la journalisation dans ~/journal/ansible.log.

    Testez la journalisation.

    Créez un groupe [testlab] avec vos trois Target Hosts.

    Définissez explicitement l'utilisateur vagrant pour la connexion à vos cibles.

    Envoyez un ping Ansible vers le groupe de machines [all].

    Définissez l'élévation des droits pour l'utilisateur vagrant sur les Target Hosts.

    Affichez la première ligne du fichier /etc/shadow sur tous les Target Hosts.

    Quittez le Control Host et supprimez toutes les VM de l'atelier.

## Commandes
- sudo nano /etc/hosts
- ssh-keyscan -t rsa target01 target02 target03 >> .ssh/known_hosts
- ssh-keygen
- ssh-copy-id vagrant@target01
- ssh-copy-id vagrant@target02
- ssh-copy-id vagrant@target03
- sudo apt update
- sudo apt install -y ansible
- ansible all -i target01,target02,target03 -u vagrant -m ping
- mkdir monprojet
- cd monprojet/
- touch ansible.cfg
- ansible --version
- sudo apt install -y direnv
- echo 'eval "$(direnv hook bash)"' >> ~/.bashrc
- source ~/.bashrc
- echo 'export ANSIBLE_CONFIG=$(expand_path ansible.cfg)' > .envrc
- direnv allow
- sudo nano ansible.cfg  

[defaults]

inventory = ./hosts

log_path = ~/journal/ansible.log

- sudo nano hosts

[testlab]

target01

target02

target03

- mkdir ~/journal
- ansible all -i target01,target02,target03 -m ping
- cat ~/journal/ansible.log
- sudo nano hosts

[testlab]

target01

target02

target03

[testlab:vars]

ansible_python_interpreter=/usr/bin/python3

ansible_user=vagrant

- ansible all -m ping
- echo 'ansible_become=yes' >> hosts
- ansible all -a "head -n 1 /etc/shadow"
- exit
- vagrant destroy -f
