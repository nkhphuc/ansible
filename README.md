# Ansible cmd demo

<!-- Check dev inventory -->
ansible-inventory --list -i inventory/dev

<!-- Run playbook -->
ansible-playbook -i inventory/dev playbooks/dev_web_servers.yml
