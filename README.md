### Repo for [THIS VPN SPEED YOUTUBE VIDEO](https://youtu.be/2NkvsD3IP2s)

### Create 2 servers in AWS:
Should be  in the same subnet with pretty fast Internet connection like c6in.xlarge.
One will act as your client and another will be your server.

### On server:
Just have something to pull, like 1GB file you can create by using:
`dd if=/dev/zero of=speedtest bs=1M count=1024`

### On client:
Create SSH keys, copy public key to authorized keys on the server so you can SSH/SCP.
You can now use command:
`time scp <user>@<server_ip_ address>:/<file_location>`

### Running docker-compose file:
Copy the docker-compose file from this repo to the client
and export all variables that containers might need.
Then just connect to each container as shown in video using:
`docker exec -it <container_name> sh`
and run the same 'time scp' command as you did on the host.

For example -NordVPN container includes following env variables:
```bash
- OPENVPN_USER=${NORDVPN_OPENVPN_USER}
- OPENVPN_PASSWORD=${NORDVPN_OPENVPN_PASSWORD}
- SERVER_CITIES=${CITY}
```
so you need to first export all those 3 variables using command:
```bash
export NORDVPN_OPENVPN_USER=<user_provided_by_NordVPN>
export NORDVPN_OPENVPN_PASSWORD=<nordvpn_pass_that_you_got_from_NordVPN>
export CITY=London
```


