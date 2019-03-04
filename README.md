# Vagrant - MariaDB - Ansible (with Vault)

MariaDB provisioning using Ansible + Ansible Vault on Ubuntu Bionic64 Vagrant Box

## How To Run

1. Installing VirtualBox Vagrant Python and Ansible on host Computer
2. Make sure to have default ssh key (```~/.ssh/id_rsa``)
3. Running vagrant box
    ```
    vagrant up
    ```
4. Running ansible
    ```
    ansible-playbook mariadb.yml -i inventories/local --ask-vault-pass
    ```
    > Input ```test``` as vault password

5. Checking database
    ```
    vagrant ssh
    mysql -u local_user -p local_db
    ```
    > MySQL pass is ```local_pass```.

## Editing Ansible-Vault file

    ```EDITOR=nano ansible-vault edit ./inventories/local/group_vars/mariadb/mariadb```

    > default text editor is VIM, you can freely change it

## What if I didn't use Vagrant?

This ansible script only works on Ubuntu, and tested on Ubuntu 18.04 64bit

1. Change file ```/inventories/local/hosts``` with your server IP, Username and Private key
2. Then run from step 4