# Plex docker-compose file for ds918+
A skeleton docker-compose file for running plex on your Synology Unit (ds918+)

## Requirements
Software needed to use this:
* Docker - (https://www.docker.com/)
* Git - (https://git-scm.com/)

Hint: Install packages using Synology package center or via [SynoCommunity](https://synocommunity.com/)

## Deployment

Once you have docker installed on your synology unit, you need to update the docker-compose file to suit your environment:

```
git clone https://github.com/scamfield/docker-compose-plex.git
cd docker-compose-plex
```

Create a dedicated user for your container and update the UID / GUID in the docker-compose file with your user: 

```
    environment:
      - PUID=1000
      - PGID=1000
```

Under environment, you can add your claim token generated from [here](https://www.plex.tv/claim/)

```
      - PLEX_CLAIM=<TOKEN>
```

Update or add the volumes to match your environment:

```
    volumes:
      - /volume1/docker/plex/config:/config
      - /volume1/docker/plex/transcode:/transcode
      - /volume1/Media:/media
```

The following devices are used for hardware transcoding on the ds918+. Please update or remove to match your environment:

```
    devices:
      - "/dev/dri/card0:/dev/dri/card0"
      - "/dev/dri/renderD128:/dev/dri/renderD128"
```

## Thanks

Thanks to [linuxserver.io](https://github.com/linuxserver) for maintaining a wide range of docker images.

## Note:

This docker-compose file could be used on a non-synology unit or deployed using portainer with stacks.

## Issues

Please address any issues or feedback via [issues](https://github.com/scamfield/docker-compose-plex/issues).

## License
See [LICENSE](https://github.com/scamfield/docker-compose-plex/blob/master/LICENSE) file.
