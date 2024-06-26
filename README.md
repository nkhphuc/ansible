# Ansible cmd demo

<!-- Check dev inventory -->
ansible-inventory --list -i inventory/dev

<!-- Run playbook -->
<!-- Create deploy user and add SSH keys -->
ansible-playbook -i inventory/dev playbooks/create_deploy_user.yml

<!-- Test by ping and print messages -->
<!-- ansible-playbook -i inventory/dev -i inventory/staging -i inventory/production playbooks/test_connections.yml -->
ansible-playbook -i inventory/dev playbooks/test_connections.yml

<!-- Install Docker and log in -->
ansible-playbook -i inventory/dev playbooks/install_docker.yml --ask-vault-pass

<!-- Install Postgresql, DragonflyDB, Project and Nginx using Docker -->
ansible-playbook -i inventory/dev playbooks/dev_web_servers.yml --ask-vault-pass

<!-- Others -->
<!-- Connect to server as ec2-user -->
ssh -i /Users/hopee/downloads/rails-server.pem ec2-user@13.250.30.252

<!-- Get UID and GID of user in the container -->
docker run --rm nkhphuc/template7pg:latest id

<!-- Access docker image -->
docker run -it --rm nkhphuc/template7pg:latest /bin/bash

<!-- Remove all docker containers and networks -->
docker stop $(docker ps -aq)
docker rm $(docker ps -aq)
docker network prune -f

<!-- Switch to the deploy_user user -->
sudo su - deploy_user

<!-- Create the .ansible directory in the deploy_user's home directory -->
mkdir -p ~/.ansible

<!-- Create the tmp directory inside the .ansible directory -->
mkdir ~/.ansible/tmp

<!-- Set the appropriate permissions for the tmp directory -->
chmod 775 ~/.ansible/tmp

<!-- Ansible Vault -->
<!-- Create an encrypted file -->
ansible-vault create secret.yml

<!-- Edit an encrypted file -->
ansible-vault edit secret.yml

<!-- Decrypt a file -->
ansible-vault decrypt secret.yml

<!-- View an encrypted file -->
ansible-vault view secret.yml

<!-- Encrypt an existing file -->
ansible-vault encrypt playbooks/roles/docker/vars/main.yml
ansible-vault decrypt playbooks/roles/docker/vars/main.yml
