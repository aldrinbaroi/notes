### Install docker & docker-compose on raspbian buster

#### Install docker

```
curl -sSL https://get.docker.com | sh
```
  ***sudo*** is needed to run docker command.  This can be avoided by adding the ***user*** to ***docker*** group:

```
sudo usermod -aG docker pi
```
#### Install docker-compose

```
sudo apt install libffi-dev libssl-dev python3 python3-pip
sudo apt remove python-configparser
sudo pip3 install docker-compose
reboot
```
