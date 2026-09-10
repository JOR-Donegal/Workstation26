# GNS3

Some of my network exercises use GNS3. I clone __ub2404-docker1__ and create a new image __ub2404-gns3__

```linux
#!/bin/bash
# By: John O'Raw
# Date: 18DEC25
# Function: Add gns3 to UB2204 server
# Script: 6-gns3.sh

sudo add-apt-repository ppa:gns3/ppa
sudo apt update                                
sudo apt install gns3-gui gns3-server -y
```

```linux
#!/bin/bash
# By: John O'Raw
# Date: 18DEC25
# Function: Add IOU support to GNS3 
# Script: 6-iou.sh

sudo dpkg --add-architecture i386
sudo apt update
sudo apt install gns3-iou -y
```
