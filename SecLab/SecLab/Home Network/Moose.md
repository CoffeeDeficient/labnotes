## Network
SOmething odd about the built-in NIC, have to use the USB nic to get activation at boot

## Docker Images

**Plex**
fstab: 
```

delphi.asgard:/volume1/Media  /plex/media        nfs     auto,user,rw,noatime,vers=3     0       0
```

/plex/plex_run
```

#!/bin/bash

docker run \
  -d \
  --name plex-mm \
  --network=host \
  -e TZ="America/Denver" \
  -e PLEX_CLAIM="claim-Z_ZiCwBCM3d62-J6jEy3" \
  -v /plex/database:/config \
  -v /plex/transcode:/transcode \
  -v /plex/media/Movies:/data/movies \
  -v /plex/media/Music:/data/music \
  -v /plex/media/Pictures:/data/pictures \
  plexinc/pms-docker
```

**Minecraft**
```
docker run -d -it --name mc-server -e EULA=TRUE -e GAMEMODE=creative -e ALLOW_CHEATS=true -e OPS="2535465335506810,2535411546108702" -e WHITE_LIST_USERS="Ryatt01,Ryatt02" -p 19132:19132/udp -v mc-volume:/data itzg/minecraft-bedrock-serverls
```

**Unifi Controller**
Docker-compose.yaml
```
---
version: "2.1"
services:
  unifi-controller:
    image: lscr.io/linuxserver/unifi-controller:latest
    container_name: unifi-controller
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Denver
      - MEM_LIMIT=1024 #optional
      - MEM_STARTUP=1024 #optional
    volumes:
      - /home/jrm/Docker/UbiquitController/data:/config
    ports:
      - 8443:8443
      - 3478:3478/udp
      - 10001:10001/udp
      - 8080:8080
      - 1900:1900/udp #optional
      - 8843:8843 #optional
      - 8880:8880 #optional
      - 6789:6789 #optional
      - 5514:5514/udp #optional
    restart: unless-stopped
```

**Watchtower**
centurylink/watchtower

```
docker update --restart=always plex-mm
```