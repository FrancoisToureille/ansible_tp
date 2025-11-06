## Enoncé
- Lancez une VM Rocky Linux et installez Ansible en utilisant PIP et Virtualenv.

## Commandes exécutées
- cd formation-ansible/atelier-01
- vagrant up rocky
- vagrant ssh rocky
- sudo dnf update -y
- sudo dnf install -y python3 python3-pip
- python3 -m venv ~/.venv/ansible
- source ~/.venv/ansible/bin/activate
- pip install --upgrade pip
- pip install ansible
- ansible --version
- exit
- vagrant destroy -f rocky
