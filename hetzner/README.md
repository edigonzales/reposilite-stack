# Hetzner

## Server erstellen

- Standort: Falkenstein
- Image: Apps - Docker CE
- Typ: CAX11 (ARM)
- Networking: Öffentliche IPv4 und IPv6.
- SSH-Keys: alle benötigten
- Firewalls: todo
- Backup: todo
- Cloud config:

```
#cloud-config
users:
  - name: reposilite
    shell: /bin/bash
    groups: docker

package_upgrade: false

runcmd:
  - [su, reposilite, -c, "git clone https://github.com/edigonzales/reposilite-stack.git /home/reposilite/reposilite-stack"]
```

- Anwendung starten: todo (siehe unten)
- Floating IP: https://docs.hetzner.com/de/cloud/floating-ips/persistent-configuration/ -> todo: in cloud-config (chmod 700 /etc/netplan/60-floating-ip.yaml)

## Anwendung deployen

```
ssh root@xxxxxxxxxx
```

```
sudo su reposilite
```

```
cd && git clone https://github.com/edigonzales/reposilite-stack.git 
```

```
docker compose -f reposilite-stack/hetzner/docker-compose.yml -p reposilite up
```


## Tokens

Admin Token in der GUI-Konsole erstellen und anschliessend Anwendung ohne `--token admin:secret` neu starten (siehe docker-compose.yml).

```
token-generate admin m
```

Weitere Benutzer und Token erstellen:

```

```