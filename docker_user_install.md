# AGX_Orin_install

1. Docker install
```
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
```

```
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
```

```
sudo apt-get update
```
```
sudo apt-get install nvidia-docker2
```

// reference 
```
https://www.ibm.com/docs/zh-tw/mas-cd/maximo-vi/continuous-delivery?topic=planning-installing-docker-nvidia-docker2
```

2. Docker images load
```
sudo docker load --input <file_names>
```
Docker container run
```
docker run -it <image_names> /bin/sh
```
(for show GUI)
```
docker run -it --rm -e DISPLAY --net=host -v $XAUTHORITY:/root/.Xauthority -v /tmp/.X11-unix:/tmp/.X11-unix debian:11-slim <image_names> /bin/sh
```

3. Change vo

I ran out of space on an Ubuntu and had to do the following:
Stop the docker service
```
sudo systemctl stop docker.service
sudo systemctl stop docker.socket
```
Copy /var/lib/docker to new volume
```
sudo rsync -aqxP /var/lib/docker/ /media/username/spare\ disk/
```
Update /etc/docker/daemon.json
```
{
"data-root": "/media/username/spare disk/docker",
"storage-driver": "overlay2"
}
```
Reload systemd and start docker service
```
sudo systemctl daemon-reload
sudo systemctl start docker
```

See: https://docs.docker.com/config/daemon/systemd/#runtime-directory-and-storage-driver
