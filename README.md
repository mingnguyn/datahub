# DATAHUB

1. Install Docker and Docker Compose:

   ```bash
   yum install -y yum-utils
   yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
   yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

   echo '{
     "exec-opts": ["native.cgroupdriver=systemd"],
     "log-driver": "json-file",
     "log-opts": {
       "max-size": "100m"
     },
     "storage-driver": "overlay2",
     "data-root": "/data/volumes/"
      }' | sudo tee /etc/docker/daemon.json

   systemctl daemon-reload
   systemctl restart docker
