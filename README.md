# Pi-Hole DoH Docker Composition

Docker composition for Pi-Hole with DNS over HTTPS.

## Installation

1. [Install docker](https://www.docker.com/get-started) if you haven't already.
1. [Install docker-compose](https://docs.docker.com/compose/install/) if you haven't already.
1. Clone the repository or download the `docker-compose.yml` file.
1. Modify the `.env.example` file and rename to `.env`
1. Run `docker-compose up --detach` from the directory you copied the file to and docker should do the rest.

After successfull startup you should see 3 container running. You can check their status with `docker ps`.

```zsh
CONTAINER ID   IMAGE                                COMMAND                  CREATED        STATUS                  PORTS                                                                                                                                            NAMES
c6a234baa5a9   pihole/pihole:latest                 "/s6-init"               22 hours ago   Up 22 hours (healthy)   0.0.0.0:53->53/udp, :::53->53/udp, 0.0.0.0:53->53/tcp, 0.0.0.0:67->67/udp, :::53->53/tcp, :::67->67/udp, 0.0.0.0:8088->80/tcp, :::8088->80/tcp   pihole
e9c6cedc0fdd   visibilityspots/cloudflared:latest   "/bin/sh -c '/usr/lo…"   22 hours ago   Up 22 hours (healthy)                                                                                                                                                    googleflared
8aabda076a0f   visibilityspots/cloudflared:latest   "/bin/sh -c '/usr/lo…"   22 hours ago   Up 22 hours (healthy)                                                                                                                                                    cloudflared
```

## Usage

You should be able to log in to the pi-hole web interface at `http://<VIRTUAL_HOST>:8088/admin/` using the `WEBPASSWORD` defined in the compose file.

## Updating

Run the following commands to update the pi-hole container and it's dependencies:

1. `# docker-compose pull`
1. `# docker-compose down`
1. `# docker-compose up --detach`
