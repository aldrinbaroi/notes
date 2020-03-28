
## Raspberry Pi 4 - Setup Docker & Docker Compose

### Install Docker
Install Docker

    curl -sSL https://get.docker.com | sh

Add permission to Pi User to run Docker Commands without SUDO

    sudo usermod -aG docker pi

Reboot here or run the next commands with a sudo
Test Docker installation

    docker run hello-world

### Install Docker Compose
Install dependencies

    sudo apt-get install -y libffi-dev libssl-dev
    sudo apt-get install -y python3 python3-pip
    sudo apt-get remove python-configparser

Install Docker Compose

    sudo pip3 install docker-compose


