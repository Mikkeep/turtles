# turtles
TryHackMeRoomTurtles

## to SSH into the development machine
ssh -o PubkeyAuthentication=no -o PreferredAuthentications=password <username@ipaddress>

## Install pip3 and Ansible on the virtual machine

sudo apt install python3-pip

pip3 install ansible

## Deploy the Ansible playbook to install the needed packages and files

ansible-playbook --connection=local build.playbook --become-password-file pass.txt
