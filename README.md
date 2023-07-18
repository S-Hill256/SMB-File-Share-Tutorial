# Setting up Samba File Shares in Linux
[![Setting up Samba File Shares in Linux](https://img.youtube.com/vi/8O8EsAzmUkI/maxresdefault.jpg)](https://www.youtube.com/watch?v=8O8EsAzmUkI)

# Getting Started

 ### To install Samba on an Ubuntu machine, you need to ensure that you meet the following prerequisites: 
- A machine running Ubuntu v22.04.2 
- Root access or sudo privileges: You'll need administrative access to install packages and make system-level changes. Either log in as the root user or have a user account with sudo privileges.
- Installed Samba package (Installation shown in introduction of tutorial)
- Up-to-date system: It's always recommended to have an updated Ubuntu system. Run the following commands to update your system before installing Samba:
```sh
sudo apt update
sudo apt upgrade
```
#### Now we are ready to start!
# Basic Installation

#### Step 1: Creation of share folder

```sh
mkdir testshare
# Creates your sharable folder
```

#### Step 2: Creating/Modifying your Samba directory
 

```sh
cd /etc/samba/
# Creates Samba directory
```

```sh
sudo mv smb.conf smb.conf old
# Clears out our "smb.conf" section in our Samba directory
```

#### Step 3: Building your own smb.conf file
 
```sh
sudo gedit smb.conf
# Allows us to build our own smb.conf file (see in terminal below)
```

```sh
[global]
 server role = standalone server
 map to guest = bad user
 usershare allow guests = yes
 hosts allow = 192.168.0.0/16
 hosts deny = 0.0.0.0/0


[linuxsharename]
  comment = Open Linux Share
  path = /home/titus/linuxshare
  read only = no
  guest ok = yes
  force create mode = 0755
  force user = username
  force group = username

# smb.conf file contents
```

#### Step 4: Test configuration settings

```sh
testparm
# Tests smb.conf configuration settings
```
#### Step 5: Restart Samba service

```sh
sudo service smbd restart
# Restarts smb service
```


## Enabling "SMB 1.0" feature on  Windows Machines
![1](https://github.com/S-Hill256/SMB-Tutorial/assets/138057919/74106a1d-c69e-41a9-8d2f-0dda0f30c797)
#### Step 1:
- Open "Run" application
  - Type appwiz.cpl to open Programs and Features

![3](https://github.com/S-Hill256/SMB-Tutorial/assets/138057919/3f678e2c-31a2-4d3f-8fda-a5c1e76ef9fe)
#### Step 2:
- Select "Turn Windows features on or off"

![2](https://github.com/S-Hill256/SMB-Tutorial/assets/138057919/5391c852-5d2c-478b-a575-bee8772ead21)
#### Step: 3
- Locate "SMB 1.0/CIFS File Sharing Support" and check the box
