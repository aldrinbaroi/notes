### Ubuntu Netplan

**Quick Reference**

For server/desktop using ***netword***, the config file (*config file name* **.yaml**) should look like the follow:
```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      dhcp4: true
```
For server/desktop using ***NetworkManager***, the config file (*config file name* **.yaml**) should look like the follow:
```
network:
  version: 2
  renderer: NetworkManager
```
To update the netplan, execute the following:
```
sudo netplan --debug generate
sudo netplan apply
reboot
```
**Detail Reference/Examples:** <br/>
https://netplan.io/examples
