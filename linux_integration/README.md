
# Update the APT Repository

sudo apt update
sudo apt upgrade -y

# Update /etc/hosts file

Be sure the following entry is in your /etc/hosts file.

```
192.168.7.138   goodcorp.net goodcorp
```

# Update the /etc/fstab file

The following needs to be in the /etc/fstab
```
vmhgfs-fuse	/	fuse	defaults,allow_other	0	0
```
# Update the hostname
```
sudo hostnamectl set-hostname ubuntu3.goodcorp.net
```
```
hostnamectl
```

# Install realmd if it is not already.
```
which realm || sudo apt -y install realmd
```

# Confirm Connectivity to the AD Domain
```
sudo realm discover goodcorp.net
```

# Disable DNS
```
sudo systemctl disable systemd-resolved
sudo systemctl stop systemd-resolved
```
# Join the AD Domain
```
sudo realm join -U Administrator goodcorp.net
```
# Confirm the Join
```
realm list
```