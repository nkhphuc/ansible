# Ansible cmd demo

<!-- Check dev inventory -->
ansible-inventory --list -i inventory/dev

<!-- Run playbook -->
<!-- Create deploy user -->
ansible-playbook -i inventory/dev playbooks/create_deploy_user.yml

<!-- Test by ping and print messages -->
ansible-playbook -i inventory/dev playbooks/dev_web_servers.yml

<!-- Others -->
<!-- Connect to server as ec2-user -->
ssh -i /Users/hopee/downloads/rails-server.pem ec2-user@13.215.49.198

<!-- Switch to the deploy_user user -->
sudo su - deploy_user

<!-- Create the .ansible directory in the deploy_user's home directory -->
mkdir -p ~/.ansible

<!-- Create the tmp directory inside the .ansible directory -->
mkdir ~/.ansible/tmp

<!-- Set the appropriate permissions for the tmp directory -->
chmod 775 ~/.ansible/tmp
