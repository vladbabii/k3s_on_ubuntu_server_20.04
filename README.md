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

## Install MySQL
```
apt install -y mysql-server
```

## Setup MySQL
shell
```
mysql -u root
```

run queries
```
create database k3s;
CREATE USER 'k3s'@'%' IDENTIFIED BY 'k3sk3s';
GRANT USAGE ON *.* TO 'k3s'@'%';
GRANT EXECUTE, SELECT, SHOW VIEW, ALTER, ALTER ROUTINE, CREATE, CREATE ROUTINE, CREATE TEMPORARY TABLES, CREATE VIEW, DELETE, DROP, EVENT, INDEX, INSERT, REFERENCES, TRIGGER, UPDATE, LOCK TABLES  ON `k3s`.* TO 'k3s'@'%' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```


## Install K3s
```
curl -sfL https://get.k3s.io | sh -s - server --datastore-endpoint="mysql://k3s:k3sk3s@tcp(127.0.0.1:3306)/k3s"
```

