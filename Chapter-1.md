# <strong>Installation of Ansible on different Distros</strong>

Debian/Ubuntu:
The easiest way to install Ansible on a Debian or Ubuntu system is to use the official
apt package.
$ sudo apt-add-repository -y ppa:ansible/ansible
$ sudo apt-get update
$ sudo apt-get install -y ansible

For CentOs, follow the instruction within the link

[centos](https://www.tecmint.com/install-ansible-on-centos-rhel-8/)

After completing installation.

Open your GCP console and configure your server

<img width="757" alt="Capture" src="https://user-images.githubusercontent.com/29310552/166856187-64e30689-c5d6-4087-9618-e86d6deb73b6.PNG">

Second step is to configure your ssh keys on the terminal to be able to remotely connect.

For GCP, they have their methods, you can use this link also:

[GCP-ssh key creation](https://cloud.google.com/compute/docs/connect/create-ssh-keys)
[GCP-coonecting with SSH-key](https://cloud.google.com/compute/docs/instances/connecting-advanced)

```
$ ssh-keygen -t rsa -f ~/.ssh/KEY_FILENAME -C USER -b 2048

```

```

$ssh -i PATH_TO_PRIVATE_KEY USERNAME@EXTERNAL_IP

```

copy the public key pair from the from the terminal in `cat ~/.ssh/(name used during the creating)`

Paste it into the metadata console with the vm created. The metadata is on the left pane of the dashboard

![image](https://user-images.githubusercontent.com/29310552/166856725-2c66b1dc-ca3b-41e6-b404-5fb7e40f5148.png)

Go back to your terminal and copy either your static IP or emphemeral IP.

[GCP-coonecting with SSH-key](https://cloud.google.com/compute/docs/instances/connecting-advanced)


`ssh -i /home/<users>/.ssh/private-key (gcp-username)@35.226.247.199`

If not going connecting, change the permission by using 

chmond 700 private-key. This should be done /.ssh/ directory

After connecting and setting up your VM, go to your local terminal within your system where ansible has been stored

# Creating a basic inventory file

```
$ sudo mkdir /etc/ansible
$ sudo touch /etc/ansible/hosts

```

Edit this hosts file with nano, vim, or whatever editor you’d like, but note you’ll need
to edit it with sudo as root. Put the following into the file

[example](This could be the name of the server
www.example.com (IP address)

where example is the group of servers you’re managing and www.example.com is the
domain name (or IP address) of a server in that group. If you’re not using port 22 for
SSH on this server, you will need to add it to the address, like www.example.com:2222,
since Ansible defaults to port 22 and won’t get this value from your ssh config file

![image](https://user-images.githubusercontent.com/29310552/166858300-a5dd8367-3628-410c-9312-0322d0b3deed.png)

# Running your first Ad-Hoc Ansible command

ansible example -m ping -u [username]

`$ ansible webservers -m ping -u ogunmolalamide -vvv`

![image](https://user-images.githubusercontent.com/29310552/166858593-5caf583a-33cb-48c5-91df-6677da6ed228.png)

`$ ansible example -a "free -m" -u [username]`

ansible webservers -a "free -m" -u ogunmolalamide

![image](https://user-images.githubusercontent.com/29310552/166858726-8556deaf-7f3f-4317-b738-f1c205ea17a0.png)

In this example, we quickly see memory usage (in a human readable format) on all the
servers (for now, just one) in the (example /webserver) group.

Thsis tutorial is based on Book by [Jeff Geerling](https://www.mindg.cn/download/ansible-for-devops.pdf) (Ansible for DevOps)
















