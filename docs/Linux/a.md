# Jump Server

For every data centre I need to manage, I'll create a separate _jump server_. This will be a workstation included within the security of that data centre, normally part of the Active Directory domain. The software I require on that jump server will be installed and dedicated to that particular data centre. This compartmentalizes the work for one client from any other client I'm working with.

This jump server may exist on my workstation as a VM and will have a VPN client which allows me to access its specific data centre.

An almost identical copy could live in the data centre itself, for me to work locally or to log in remotely to.

In this case, I am working on a Ubuntu 24.04 VM in VMWare Workstation. As I figure out what commands to use, I document them in a script file. So first step, create a template for my scripts.

I initially create a VM with server only. I call it __ub2404-js1__

```linux
#!/bin/bash
# By: John O'Raw
# Date: 18DEC25
# Function: First actions on new UB2204 server
# Script: 0-all.sh

sudo apt update
sudo apt upgrade -y
```

To work remotely, I need SSH server. 

```linux
sudo apt install openssh-server -y
```

I need to install a GUI and RDP so I can remote into the GUI

```linux
#!/bin/bash
# By: John O'Raw
# Date: 18DEC25
# Function: Add a GUI to UB2204 server
# Script: 1-gui.sh

sudo apt install xfce4 -y
sudo apt install xrdp -y
sudo ufw allow 3389/tcp
sudo systemctl enable xrdp
sudo systemctl restart xrdp

echo "Now test if you can RDP into this server!"
```

I will need a browser, I'm going to use Chrome.

```Linux
#!/bin/bash
# By: John O'Raw
# Date: 18DEC25
# Function: Add Chrome to UB2204 server
# Script: 2-chrome.sh

sudo apt-get install fonts-liberation
sudo apt install xdg-utils -y
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
rm google-chrome-stable_current_amd64.deb
```

It can be useful to have a graphical SSH client

```linux
#!/bin/bash
# By: John O'Raw
# Date: 18DEC25
# Function: Add Putty to UB2204 server
# Script: 5-putty.sh

sudo add-apt-repository universe
sudo apt update
sudo apt install -y putty
```

## Tests

1. Log in via SSH and WinSCP
2. Log in via RDP

That is it, I have a minimal jump server.


