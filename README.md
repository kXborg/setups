# Setups and Installations
Hi there! I am Kukil. I work in Computer Vision, NLP, and Robotics domain. During repeat setups, sometime I spend hours finding name of a package, or how I fixed a bug. These things are easier to forget. Hence creating this repository to log installationsn for various softwares, packages, and pipelines.


## 1. Network Storage For RPis and Jetson

A Samba network share provides file and print services on a network to share resources using the SMB/CIFS protocol. I am using my PC (Running Ubuntu) as host. The commands are as follows.

### 1.1 Setup Host Machine

```
sudo apt install samba
```

Once samba is installed go to `/etc/samba` here you have to edit the `smb.conf` file. I am adding `[RPiStorage]` variables as under. You have to edit your username.

```
[RPiStorage]
path = /home/kukil/RPiStorage
available = yes
valid users = kukil
read only = no
browsable = yes
public = yes
writable = yes
guest ok = no

```
Let's create a user id and password for samba using the command `sudo smbpasswd -a kukil`. This will prompt you to enter the password of choice. Once done, go ahead and create a folder which we want to share.

```
mkdir -p /home/kukil/RPiStorage

chmod -R 777 /home/kukil/RPiStorage/
```

Post this you can(have to)restart samba services using the command `sudo systemctl restart samba`. We are done with setting up SAMBA host and network folder. Now it's time to mount this on Raspberry Pi or Jetson Nano wherever we want to access it.


### 1.2 Setup Client Machine

On the Raspberry Pi or Nano, we will begin by installing required packages.

```
sudo apt install smbclient cifs-utils -y
```

Once done, we can test whether our network storage from host machine is actually working by using the following command. You will need the username, password, and ip address of the host. Successful ping will show `smb>` terminal.

```
smbclient -L //192.168.1.2 -U kukil
```

Create a mount folder, it will be used to connect the host.

```
sudo mkdir -p /mnt/netstorage
```

We can mount the storage now.

```
sudo mount -t cifs //192.168.1.2/RPiStorage /mnt/netstorage -o username=kukil,password=123,vers=3.0,sec=ntlmssp,uid=$(id -u),gid=$(id -g)
```