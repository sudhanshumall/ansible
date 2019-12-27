After Installing Ansible


1) Create Ansible user and set passwd on ansible control machine

useradd -m -s /bin/bash ansible

passwd ansible

2) Add ansible user to suoders list

echo  -e 'provision\tALL=(ALL)\tNOPASSWD:\tALL' > /etc/sudoers.d/ansible

3) Install whois package 

sudo apt install whois -y

4) Create encrypted password

mkpasswd --method=SHA-512
Your PASSWORD HERE 'anypassword'

#Note down the encrypted password as the same will be used in ansible playbook

5) Generated ssh key file using ssh-keygen

sudo su ansible

ssh-keygen -t rsa   # after firing this command, press enter again 3 times

6) Create new inventroy file 

mkdir -p ansibleInventory/

cd ansibleInventory

vim inventory.ini

and paste below content 

[jenkinsserver]
 ansible ansible_host=EC2_IP ansible_ssh_user=ubuntu ansible_ssh_private_key_file=/home/ansible/keyfile/ansible.pem

7) Now update the new inventory file in ansible config file 

inventory = /home/ansible/ansibleInventory/inventory.ini


8) Scan server finger prints below running ansible playbook, so that it can be stored under .ssh/known_hosts file

ssh-keyscan EC2_IP >> ~/.ssh/known_hosts


9) Now run you ansible playbook

ansible-playbook deploy-ssh-user.yml







