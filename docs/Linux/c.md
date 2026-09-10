# Docker

Some of my exercises use containers. I clone __ub2404-dev1__ and create a new image __ub2404-docker1__

```linux
#!/bin/bash
# By: John O'Raw
# Date: 18DEC25
# Function: Add docker to UB2204 server
# Script: 7-docker.sh

# Remove defaults first
sudo apt remove docker docker-engine docker.io
sudo snap remove docker

# Reinstall Docker
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository \
"deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(. /etc/os-release && echo $VERSION_CODENAME) stable"
sudo apt update
sudo apt install docker-ce -y

# Give the current user permissions
sudo usermod -aG ubridge,libvirt,kvm,wireshark,docker $(whoami)
```