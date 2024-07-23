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
  #- mkdir /home/reposilite/reposilite-data
  #- chown -R reposilite:reposilite /home/reposilite/reposilite-data
```

## Anwendung deployen

```
ssh root@xxxxxxxxxx
```

```
sudo su reposilite
```

```
cd && git clone https://github.com/edigonzales/reposilite-stack.git && cd hetzner
```

```
docker compose up
```