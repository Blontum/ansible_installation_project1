STEPS TO FOLLOW;
ansible controller or Master:

 sudo apt update
    sudo apt install software-properties-common
    sudo add-apt-repository --yes --update ppa:ansible/ansible
    sudo apt install ansible    install python
    install ansible
    establish ssh connetion b/n ansible controller and nodess or master and controller
    generating # id_rsa.pub
    public key
    adding clients or nodes to ansible aws inventory

ansible Nodes or clients:
    install python
    copy public-key to all node hosts

commands for ubuntu:
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible

   
ssh in to the controller:

    ifconfig : help you see the ip address
    hostnamectl: shows what is fouynd in the saver
    sudo hostnamectl set-hostname ansible-controller: rename the controller
    hostnamectl: for the second time # exit and ssh into it again. you will see the new name

verrify if python is install: 

    pyhton3 --version
    Sudo install python3

check if ansible is install:

    ansible --version
    sudo apt update
    sudo apt install software-properties-common
    sudo add-apt-repository --yes --update ppa:ansible/ansible
    sudo apt install ansible

    ansible --version

 Generate a keypay:

    sudo -i # switching to root user
    ssh-keygen -t rsa # keypay generation for rsa kaypay (private and public)
                                   # the kay is saved in (/root/.ssh/id_rsa): .ssh is a hidden file
 Enter and Enter again. private saved at:
     /root/.ssh/id_rsa # private key
     /root/.ssh/id_rsa.pub # public key

verify if those two keys are there:

cd /root/.ssh/
ls -l

# NB, copy the public key to the Node and keep the private key there.

Open a new tab and ssh into the Node:
Change the name:
    sudo hostnamectl set-hostname: ansible ;client1,client2,client3 etc  #command to set a new cliet name for other servers

    exit and log back into the server.

# we have to copy the public key from the controller to the other servers.
    cat the file and then copy the key to the node
    cat id_rsa.pub # after you cat, the copy and paste into the other servers
 GO CLIENTS:
    sudo -i                  # copy as a root user: very important
    cd .ssh
    ll

# you should see a private authorise key in there. 

    vi authorized_key #go in and paste the public key you copied

go all the way to the end of the line : function Fn forward key
    est 
    :wq! enter

repead the same process for the other Nodes:

    go back to the controller and modify it ip address.
 
ansible --version:
    cd /etc/ansible/ # it has all the configurations
    ls -l

#you find three files, ansible.cfg, hosts, roles

# youe build the invery of the Nodes in ansible host
    cat host       # it will show you what to do
    vi host        # edit (webserver)and put ubuntu-nodes
# go to the nodes and copy their private ips and coe and paste beneath "ubuntu-node"
    esc:qw! enter

# test connectivity
    ssh root@ip enter for client1
    ssh toot@ip enter for client2 etc

# test connectivity between two servers

    ansible -m ping all  # it will send a ping across all the clients from the controller

    you should have a success. with responds pong

# if you want to target a specific server: 
    ansible -m ping ubuntu-client  # for example