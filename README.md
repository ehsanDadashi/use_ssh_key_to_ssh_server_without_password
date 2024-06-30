# use_ssh_key_to_ssh_server_without_password
we can use ssh key to ssh a server without password (passwordless authentication)

# assume that we have two server srv1 and srv2 and we want to ssh from srv1 to srv2

# first login to srv1 

go to this path : cd ~/.ssh/

use this command

ssh-keygen -t rsa -b 4096

it creates public and private key to ssh 

public key = ~/.ssh/id_rsa.pub

private key = ~/.ssh/id_rsa

# now login to srv2

go to this path : cd ~/.ssh/

create a file : authorized_keys

copy content of public key in srv1 to this file 

# restart sshd service in srv1 and srv2
systemctl restart sshd

# run this command on srv1
ssh-keyscan -H 192.168.71.131 >> ~/.ssh/known_hosts

# now you can ssh passwordless
ssh user@srv2ip
