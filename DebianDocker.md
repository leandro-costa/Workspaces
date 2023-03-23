# Debian Docker
## Configure o repositório
    
1. Atualize o índice de pacote APT e instale os pacotes para permitir que o Apt use um repositório sobre o HTTPS:

    ```console
    sudo apt-get update
    sudo apt-get install \
        ca-certificates \
        curl \
        gnupg \
        lsb-release
    ```
1. Adicione a chave GPG oficial do Docker:
    ```console
    sudo mkdir -m 0755 -p /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    ```
1. Use o seguinte comando para configurar o repositório:
    ```console
    echo \
        "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
        $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    ```

## Instale o Docker
1. Atualize o índice de pacote APT:
    ```console
    sudo apt-get update
    ```
1. Instele o Docker Engine, containerd, e Docker Compose plugin.
    ```console
    sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    ```
## erro iptables

O instalador do Docker usa iptables para NAT. Infelizmente, o Debian usa o Nftables. Você pode converter as entradas em nftables ou apenas configurar o Debian para usar os iptables legados.

```console
sudo update-alternatives --set iptables /usr/sbin/iptables-legacy
sudo update-alternatives --set ip6tables /usr/sbin/ip6tables-legacy
```

Dockerd, deve começar bem depois de mudar para a iptables legado.

```console
sudo service docker start
```

## Rodando uma imagem

1. Verifique se a instalação do docker está bem-sucedida executando a imagem do Hello-World:
    ```console
    sudo docker run hello-world
    ```

## Fazendo o docker inicializar no boot

Criar o arquivo `/etc/wsl.conf`  com o seguinte conteúdo:

```console
# Set a command to run when a new WSL instance launches. This example starts the Docker container service.
[boot]
command = service docker start
```


## Exportando Debian com Docker

Exportar a versão original do Debian com Docker para servir como base

```console
sudo apt-get autoclean
```

```console
wsl --export Debian DebianDockerTemplate
```


```console
wsl --export Debian DebianDockerTemplate
```
- Importar template para novo WSL
```console
wsl --import DebianOwnCloud DebianOwnCloud DebianDockerTemplate
```


## Referência

- https://docs.docker.com/engine/install/debian/
- https://forums.docker.com/t/failing-to-start-dockerd-failed-to-create-nat-chain-docker/78269
- https://learn.microsoft.com/pt-br/windows/wsl/wsl-config