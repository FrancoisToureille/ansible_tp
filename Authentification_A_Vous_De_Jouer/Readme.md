## Enoncé
Placez-vous dans le répertoire du troisième atelier pratique :

$ cd ~/formation-ansible/atelier-03

Voici les quatre machines virtuelles Ubuntu 22.04 de cet atelier :

Machine virtuelle	Adresse IP

control	192.168.56.10

target01	192.168.56.20

target02	192.168.56.30

target03	192.168.56.40
Démarrez les VM :

$ vagrant up

Connectez-vous au Control Host :

$ vagrant ssh control

Ansible est déjà installé sur cette machine :

$ type ansible

ansible is /usr/bin/ansible

Faites le nécessaire pour réussir un ping Ansible comme ceci :

$ ansible all -i target01,target02,target03 -m ping

target03 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
target02 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
target01 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
## Commandes exécutées (après les précédentes)
- ansible all -i target01,target02,target03 -m ping *#on observe que cela ne fonctionne pas*
- sudo nano /etc/hosts *#voir la [capture d'écran](https://github.com/FrancoisToureille/ansible_tp/blob/main/Authentification_A_Vous_De_Jouer/capture4.png)*
- ssh-keyscan -t rsa target01 target02 target03 >> .ssh/known_hosts
- exit
- vagrant ssh target01
- sudo nano /etc/ssh/sshd_config  *#voir la [capture d'écran](https://github.com/FrancoisToureille/ansible_tp/blob/main/Authentification_A_Vous_De_Jouer/capture7.png)*
- sudo systemctl reload sshd
- exit
- vagrant ssh target02
- sudo nano /etc/ssh/sshd_config 
- sudo systemctl reload sshd
- exit
- vagrant ssh target03
- sudo nano /etc/ssh/sshd_config
- sudo systemctl reload sshd
- exit
- vagrant ssh control
- ssh-keygen
- ssh-copy-id vagrant@target01
- ssh-copy-id vagrant@target02
- ssh-copy-id vagrant@target03
- ansible all -i target01,target02,target03 -m ping *#ça fonctionne*
- vagrant destroy -f
