Install docker on raspbian buster

`curl -sSL https://get.docker.com | sh`

**sudo** is needed to run docker command.  This can be avoided by adding the **user** to **docker** group:

`sudo usermod -aG docker pi`

