# Ansible cmds demo

## Check cmds
<!-- Check dev inventory -->
ansible-inventory --list -i inventory/dev
<!-- Check production inventory -->
ansible-inventory --list -i inventory/prod

## Run playbook cmds
<!-- Test by ping and print messages -->
ansible-playbook -i inventory/dev playbooks/test_connections.yml
ansible-playbook -i inventory/prod playbooks/test_connections.yml

<!-- Create deploy user, add SSH keys, create ansible directory -->
ansible-playbook -i inventory/dev playbooks/create_deploy_user.yml
ansible-playbook -i inventory/prod playbooks/create_deploy_user.yml

<!-- Install Postgresql, DragonflyDB, Project and Nginx using Docker -->
ansible-playbook -i inventory/dev playbooks/docker_dev_web_servers.yml --ask-vault-pass

## Other cmds
<!-- Connect to server as ec2-user / ubuntu -->
ssh -i /Users/hopee/downloads/rails-server.pem ec2-user@54.169.173.233
ssh -i /Users/hopee/downloads/rails-server.pem ubuntu@13.250.58.55

<!-- Switch to the deploy_user user -->
sudo su - deploy_user

<!-- Or login as deploy_user -->
ssh -i /Users/hopee/.ssh/hopee_mac_github_1.pub deploy_user@13.250.58.55

## Ansible Vault cmds
<!-- Create an encrypted file -->
ansible-vault create secret.yml

<!-- Edit an encrypted file -->
ansible-vault edit secret.yml

<!-- View an encrypted file -->
ansible-vault view secret.yml

<!-- Encrypt an existing file -->
ansible-vault encrypt inventory/dev/group_vars/all/vault.yml

<!-- Decrypt an existing file -->
ansible-vault decrypt inventory/dev/group_vars/all/vault.yml

## Docker
<!-- Get UID and GID of user in the container -->
docker run --rm nkhphuc/template7pg:latest id

<!-- Access docker image -->
docker run -it --rm nkhphuc/template7pg:latest /bin/bash

<!-- Remove all docker containers and networks -->
docker stop $(docker ps -aq)
docker rm $(docker ps -aq)
docker network prune -f
