My dotfiles

- First, you will need to connect to your droplet via SSH. For now, just open up your terminal app and type: ssh root@<IP-ADDRESS-OF-DROPLET> (substituting the IP-ADDRESS that you noted before).
  
- Before doing any kind of configuration on the droplet, let’s first create a user that you can use other than root. Type in adduser USER_NAME (substituting USER_NAME with the username of your choice).
  
- Now that we have created a new user, let’s make sure that we lock down sshd from allowing that user to connect with a password and continue to use the same SSH key to connect. First we will copy the key from the root user to the newly created user. Type: mkdir /home/USER_NAME/.ssh && cat ~/.ssh/authorized_keys >> /home/USER_NAME/.ssh/authorized_keys (remember to substitute USER_NAME with the username that you chose earlier).
  
- Next, we need to chown that directory that we just created so that the USER_NAME can write to it later. Execute this command: chown -R USER_NAME:USER_NAME /home/USER_NAME/.ssh

- Now we can add this new user to the sudoers file. This will allow this user to execute the sudo command. Replicate the line root ALL=(ALL:ALL) ALL, replacing root with your new username, and save the file. (If you’re in vim, you’ll need to save with :w! since the file is readonly.)
```
  vim /etc/sudoers
```
