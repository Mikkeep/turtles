# turtles
TryHackMeRoomTurtles

## to SSH into the development machine
ssh -o PubkeyAuthentication=no -o PreferredAuthentications=password <username@ipaddress>

## Make ssh config file for easier access

nano ~/.ssh/config

```
Host tryhackmevm
	Hostname <vm_ip_here>
	User tester
	PreferredAuthentications=password
	PubkeyAuthentication=no
```

# Copy the git folder to the virtual machine

Use this command from the git root repository folder

scp -r * tryhackmevm:/home/tester

## Install pip3 and Ansible on the virtual machine

sudo apt install python3-pip

pip3 install ansible

# Install Ansible also via apt

sudo apt install ansible

# Go to ansible folder

cd /home/tester/ansible

# Create the become pass file

nano pass.txt

insert the sudo password in here

## Deploy the Ansible playbook to install the needed packages and files

ansible-playbook --connection=local build.playbook --become-password-file pass.txt
