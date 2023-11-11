# Turtles
TryHackMeRoomTurtles

If you want to customize the RiteCMS application files, then make changes to the cms/ritedev/data/sql files.
Edit the file with the wanted changed content and generate a new database file sqlite3:

Example for content.db:

```shell
sqlite3 content.db < sqlite_content_init.sql
```

***

# Installation

The provided Ansible script and guide assumes the Ubuntu virtual machine has been created with a user called ```tester```.
If your account differs from this, change the occurences of the user within the script and from the below commands.

## To SSH into the development machine
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

## Copy the git folder to the virtual machine

Use this command from the git root repository folder

```shell
scp -r * tryhackmevm:/home/tester
```

## Install pip3 and Ansible on the virtual machine

```shell
sudo apt install python3-pip
```
```shell
pip3 install ansible
```

## Install Ansible also via apt

```shell
sudo apt install ansible
```

## Go to ansible folder

```shell
cd /home/tester/ansible
```

## Create the become pass file

```shell
nano pass.txt
```

Insert the sudo password in here

## Deploy the Ansible playbook to install the needed packages and files

```shell
ansible-playbook --connection=local build.playbook --become-password-file pass.txt
```
