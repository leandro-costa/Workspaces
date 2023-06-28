# Subir o NextCloud

## Dentro da maquina com o docker (pode ser wsl)

instalar o net-tools

```console
apt install net-tools -y
```

Obter o IP do docker

```console
ip addr show eth0 | grep -oP '(?<=inet\s)\d+(\.\d+){3}'
```

Definir o valor do ip em db.env

```console
NEXTCLOUD_TRUSTED_DOMAINS=172.19.184.93
```
subir o compose

```console
docker compose up -d
```
