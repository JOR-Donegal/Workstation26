# Jump Server

For every data centre I need to manage, I'll create a separate _jump server_. This will be a workstation included within the security of that data centre, normally part of the Active Directory domain. The software I require on that jump server will be installed and dedicated to that particular data centre. This compartmentalizes the work for one client from any other client I'm working with.

This jump server may exist on my workstation as a VM and will have a VPN client which allows me to access its specific data centre.

An almost identical copy could live in the data centre itself, for me to work locally or to log in remotely to.

