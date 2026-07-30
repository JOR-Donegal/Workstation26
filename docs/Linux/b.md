# Development

The software and configuration of a development workstation will depend on the development environment. Here, I'm going to detail a standard Ubuntu 24.04 configuration as I use in most of the modules I teach.

I'm going to show the script I used the last time this worked!

Beware, every year I have to make changes to these scripts, as nothing stays the same. These scripts will give you an idea of what software I've used and how I installed it, the last time I did.

I create a full clone of the jump server VM I created previously, I call it __ub2404-dev1__ but you can pick an appropriate name.

Next, I'm going to install VSCode

```linux
#!/bin/bash
# By: John O'Raw
# Date: 18DEC25
# Function: Add VSCode to UB2204 server
# Script: 3-vscode.sh

echo "Careful, this link may change, might be better to go via browser?"
read -p "Press return to continue"

wget https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64
sudo apt install ./code_1.105.1-1760482543_amd64.deb
```

We will be using GIT and GITHUB

```linux
#!/bin/bash
# By: John O'Raw
# Date: 18DEC25
# Function: Add github desktop to UB2204 server
# Script: 4-github.sh

sudo apt-get install git-all -y

wget -qO - https://mirror.mwt.me/shiftkey-desktop/gpgkey | gpg --dearmor | sudo tee /usr/share/keyrings/mwt-desktop.gpg > /dev/null
sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/mwt-desktop.gpg] https://mirror.mwt.me/shiftkey-desktop/deb/ any main" > /etc/apt/sources.list.d/mwt-desktop.list'
sudo apt update
sudo apt install github-desktop -y
sudo apt install gh -y
```

