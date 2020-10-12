# K3s on Ubuntu Server 20.04


## Remove Snapd
```
snap list
snap remove lxd
snap remove core18
snap remove snapd
apt purge snap
apt purge snapd
```

## Update Packages
```
apt update
apt upgrade -y
```

## Install some stuff (optional)
```
apt install -y nano htop screen net-tools ethtool iperf
```
