# Criando o serviço do owncloud

Criar o wsl para o serviço do owncloud

```console
wsl --import owncloud owncloud DebianDockerTemplate
```

Acessar o wsl

```console
wsl -d owncloud 
```

Criar pasta para armazenar arquivo

```console
mkdir owncloud-docker-server
cd owncloud-docker-server
```

Baixar o arquivo docker-compose.yml

```console
wget https://raw.githubusercontent.com/owncloud/docs-server/master/modules/admin_manual/examples/installation/docker/docker-compose.yml
```

Criar arquivo com variáveis de ambiente

```console
cat << EOF > .env
OWNCLOUD_VERSION=10.12
OWNCLOUD_DOMAIN=localhost:8080
OWNCLOUD_TRUSTED_DOMAINS=localhost
ADMIN_USERNAME=admin
ADMIN_PASSWORD=admin
HTTP_PORT=8080
EOF```

substituir localhost pelo ip

```console
ip addr show eth0 | grep -oP '(?<=inet\s)\d+(\.\d+){3}'
```

subir os containers

```console
docker compose up -d
```

Acessar `http://localhost:8080` no windows

## referência

- https://doc.owncloud.com/server/next/admin_manual/installation/docker/
