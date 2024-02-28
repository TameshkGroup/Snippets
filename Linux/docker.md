## Installation:
```
sudo pacman -S docker
```

## Service:
```
sudo systemctl start docker
```

```
sudo systemctl enable docker
```
## Adding User to Docker group:
Running docker requires sudo privileges. So we need to root every time we run docker. This can be eliminated by adding the user to the docker group. To add the user to the docker group, use the usermod command.

```
sudo usermod -aG docker $USER
```
The user needs to log back in to see the effect.

Note: Anyone added to the docker group is root equivalent, so make sure you trust the user that you are adding to the docker group.


### Test:
```
docker run hello-world
```


You also need to install the `docker-compose` for easy running docker.

---
##  Docker domains to apply on firewall rules or routing
https://auth.docker.io

https://registry.docker.io

https://registry-1.docker.io

https://registry-2.docker.io

https://index.docker.io/

https://dseasb33srnrn.cloudfront.net/

https://production.cloudflare.docker.com/


## Make docker use socks proxy for pulling images

On Arch edit the following file:
```
/usr/lib/systemd/system/docker.service
```

```bash
[Service]
Environment="HTTP_PROXY=socks5://ip:port"
Environment="HTTPS_PROXY=socks5://ip:port"
```

Running the following command are necessary afterwards:

```bash
systemctl daemon-reload
systemctl restart docker
```
---

## Relocate docker files to free more space on root dir

- Stop the docker
```bash
sudo systemctl stop docker
```
- Add a file to `/etc/docker`

```bash
sudo vi /etc/docker/daemon.json
```
- Add the following lines to the file

```javascript
{
  "data-root": "/path/to/your/docker"
}
```
- Copy the files
```bash
sudo rsync -aP /var/lib/docker/ /path/to/your/docker
```

- Backup current files:
```bash
sudo mv /var/lib/docker /var/lib/docker.old
```
- Start the service:
```bash
sudo systemctl start docker
```
- Test if everything works well
- Remove the redundant files:
```bash
sudo rm -rf /var/lib/docker.old
```








## How to use UFW firewall with Docker containers?

iptables=false in /etc/docker/daemon.json and manually setting up ufw rules
In this solution, we start with setting up our Docker to the mode where it doesn’t modify iptables rules:


```bash
$ echo "{
\"iptables\": false
}" > /etc/docker/daemon.json
```
Let’s restart the docker server:

```bash
$ sudo systemctl restart docker
```
After than we need to tweak the default ufw forward policy from dropping connection to accepting them, then force ufw to reload the rules, this allows the connections from external interfaces to pass the internal one: 

```bash
$ sudo sed -i -e 's/DEFAULT_FORWARD_POLICY="DROP"/DEFAULT_FORWARD_POLICY="ACCEPT"/g' /etc/default/ufw
$ sudo ufw reload
```
Finally we need to add a rule to the iptable that will pass the connection to the docker network. Given that the docker network is on 172.17.0.0/16 space:

```bash
$ iptables -t nat -A POSTROUTING ! -o docker0 -s 172.17.0.0/16 -j MASQUERADE
```
This means that connections coming to the network interface will be passed via ufw to the docker network 172.17.0.0/16, and now ufw can control the traffic to that network. A lot of manual work

[source](https://blog.jarrousse.org/2023/03/18/how-to-use-ufw-firewall-with-docker-containers/)


## Docker: How to clear the logs properly for a Docker container?
Use:
```bash
truncate -s 0 /var/lib/docker/containers/**/*-json.log
```
You may need sudo
```bash
sudo sh -c "truncate -s 0 /var/lib/docker/containers/**/*-json.log"
```
