# Valheim server
Instructions on setting up Valheim server locally on Ubuntu 22.04.

## Install
Here are the steps to install. Need to migrate these to Ansible playbook eventually.

Update and install base packages
```
sudo dpkg --add-architecture i386
sudo apt update
sudo apt install curl wget file tar bzip2 gzip unzip bsdmainutils python3 util-linux ca-certificates binutils bc jq tmux netcat lib32gcc-s1 lib32stdc++6 libsdl2-2.0-0:i386 steamcmd libc6-dev
```

Open firewall ports
```
sudo ufw allow 2456/tcp
sudo ufw allow 2457/tcp
sudo ufw allow 2457/udp
sudo ufw allow 2456/udp
```

Setup static IP address
```
sudo vi /etc/netplan/00-installer-config.yaml
sudo netplan apply
ip a
```

Create dedicated OS user to run the server application
```
sudo adduser vhserver
```

Switch to this user and install using linuxgsm
```
su - vhserver
wget -O linuxgsm.sh https://linuxgsm.sh && chmod +x linuxgsm.sh && bash linuxgsm.sh vhserver
./vhserver install
vi /home/vhserver/lgsm/config-lgsm/vhserver/vhserver.cfg
```

## Startup
su - vhserver

./vhserver start 

./vhserver details
