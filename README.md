# Vagrant - MariaDB - Ansible (with Vault)

MariaDB provisioning using Ansible + Ansible Vault.

## How To Run

1. Installing VirtualBox Vagrant Python and Ansible on host Computer
2. Running vagrant box
    ```
    vagrant up
    ```
3. Running ansible
    ```
    ansible-playbook mariadb.yml -i inventories/local --ask-vault-pass
    ```
    > Input ```test``` as vault password

4. Checking database
    ```
    vagrant ssh
    mysql -u local_user -p local_db
    ```
    > MySQL pass is ```local_pass```.

## Editing Ansible-Vault file
    ```EDITOR=nano ansible-vault edit ./inventories/local/group_vars/mariadb/mariadb```

    > default text editor is VIM, you can freely change it
