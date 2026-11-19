
# Projet 2 - Infrastructure as Code avec Ansible

## 1. Presentation

Ce projet consiste a automatiser le provisionnement
et le deploiement d'un site web statique avec Ansible.

Le serveur web utilise Nginx et fonctionne sur une
machine virtuelle Ubuntu 24.04 geree avec Vagrant
et VMware Workstation.

## 2. Technologies utilisees

- Ansible
- Vagrant
- VMware Workstation
- Ubuntu 24.04
- Nginx
- Git et GitHub
- Ansible Vault
- GitHub Actions

## 3. Architecture

Une machine de controle execute Ansible depuis WSL2.
Elle communique avec le serveur Ubuntu par SSH.

Le serveur Ubuntu heberge le site web avec Nginx.

## 4. Structure du projet

- Vagrantfile : configuration de la VM.
- inventory.ini : inventaire des serveurs.
- site.yml : playbook principal.
- roles/nginx_site : role de deploiement Nginx.
- group_vars/web : variables et secrets.
- verify.yml : verification du deploiement.
- .github/workflows : pipeline CI/CD.

## 5. Demarrage de l'infrastructure

Depuis PowerShell :

    vagrant up --provider=vmware_desktop

## 6. Deploiement

Depuis le dossier ansible :

    ansible web -m ping

    ansible-playbook site.yml --ask-vault-pass

## 7. Verification

    ansible-playbook verify.yml --ask-vault-pass

Ouvrir :

    http://localhost:8080

## 8. Securite

Les informations sensibles sont protegees avec
Ansible Vault.

Le mot de passe Vault ne doit jamais etre publie
dans le depot Git.

## 9. CI/CD

GitHub Actions declenche le deploiement lors
d'un push sur la branche main.

Le pipeline utilise un runner local pour executer
Ansible sur la VM.

## 10. Idempotence

Le playbook a ete execute deux fois successivement.

La seconde execution ne doit produire aucune
modification inutile (changed=0).

## 11. Conclusion

Ce projet demontre l'utilisation de l'approche
Infrastructure as Code pour automatiser la
configuration et le deploiement d'un serveur web.
