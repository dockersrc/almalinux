## 👋 Welcome to almalinux 🚀  

almalinux README  
  
  
## Install my system scripts  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 sudo systemmgr --config && sudo systemmgr install scripts  
```
  
## Automatic install/update  
  
```shell
dockermgr update os almalinux
```
  
## Install and run container
  
```shell
mkdir -p "/var/lib/srv/root/docker/casjaysdev/almalinux/latest"
git clone "https://github.com/dockermgr/almalinux" "$HOME/.local/share/CasjaysDev/dockermgr/almalinux"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/almalinux/rootfs/." "/var/lib/srv/root/docker/casjaysdev/almalinux/latest/"
docker run -d \
--restart always \
--privileged \
--name casjaysdev-almalinux-latest \
--hostname almalinux \
-e TZ=${TIMEZONE:-America/New_York} \
-v "/var/lib/srv/root/docker/casjaysdev/almalinux/latest/data:/data:z" \
-v "/var/lib/srv/root/docker/casjaysdev/almalinux/latest/config:/config:z" \
casjaysdev/almalinux:latest
```
  
## via docker-compose  
  
```yaml
version: "2"
services:
  ProjectName:
    image: casjaysdev/almalinux
    container_name: casjaysdev-almalinux-latest
    environment:
      - TZ=America/New_York
      - HOSTNAME=almalinux
    volumes:
      - "/var/lib/srv/root/docker/casjaysdev/almalinux/latest/data:/data:z"
      - "/var/lib/srv/root/docker/casjaysdev/almalinux/latest/config:/config:z"
    restart: always
```
  
## Get source files  
  
```shell
dockermgr download src os almalinux
```
  
## Build container  
  
```shell
git clone "https://github.com/dockersrc/almalinux" "$HOME/Projects/github/dockersrc/almalinux"
cd "$HOME/Projects/github/dockersrc/almalinux" && buildx all 
```
  
## Authors  
  
🤖 casjay: [Github](https://github.com/casjay) 🤖  
⛵ casjaysdev: [Github](https://github.com/dockersrc) [Docker](https://hub.docker.com/u/casjaysdev) ⛵  
