# compose-wireguard-squid

a multi-container Docker application to run a [squid](https://hub.docker.com/r/ubuntu/squid) forward http proxy behind a [Wireguard](https://hub.docker.com/r/linuxserver/wireguard) client

## how to set it up

1. download [docker-compose.yml](/docker-compose.yml)
1. put your `wg0.conf` file into `./wireguard`
1. run `docker-compose up`

if everything works correctly, go-ipfs should be running behind your VPN!

## how to use it

set your browser (or any other application) to use localhost:3128 as web proxy

## how it works

the `squid` service shares the network stack of the `vpn-sidecar` service (Wireguard), which is tunneled through your VPN provider. to maintain local connectivity to the `squid` container, we proxy to it to through the `web-proxy` service (Nginx) using [Docker container links](https://docs.docker.com/network/links/).

## note: an [OpenVPN](https://github.com/master-hax/compose-openvpn-squid) version is also available
