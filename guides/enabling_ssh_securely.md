# Introduction
This guide serves to help you get OpenSSH functioning properly, in a more secure way than default, as quickly as possible. Its a pretty easy process.

### Step 1 - Change default password

First we gotta change the default password. All ChimeraOS installations come with the password already set to 'gamer' by default, this is bad for SSH security as everyone by default shares the same default password. 

To change the default password, run the following command:

```sudo passwd gamer```

It will prompt you for the current password which will be 'gamer', then it will ask you for the new password twice. Please enter whatever secure password you would like to use.

### Step 2 - Enable password authentication

By default password authentication is turned off. If you try to ssh into your device before turning it on it will fail with an error saying something along the lines of 

```Permission denied (publickey)```

To fix this, run the following command:

```sudo nano /etc/ssh/sshd_config```

then find the line which says ```PasswordAuthentication no``` and switch it to ```PasswordAuthentication yes```, save, and exit.

### Step 3 - Enable the SSHD service

Next, we want to start or restart the sshd service using:

```sudo systemctl stop sshd```
```sudo systemctl enable --now sshd```

you can check to make sure its running without any errors using:

```sudo systemctl status sshd```

### Step 4 - Determine your ip address

Next we need to know the IP address of the ROG Ally so we can connect to it. The easiest way to do this is to open the settings within game mode and go to the Network section, then click on your Wifi network. 
A window should appear with a bunch of network information, there will be a section called "IP Address"

you can also find it through the terminal using:

```ip a```

### Step 5 - Connect!

Now you can connect to your device so you can send commands to it from another PC, even when its in game mode! Simply enter...

```ssh gamer@your.ip.address.here```

and enter the new password you set for your ROG Ally in Step 1 when prompted. You should now be connected!