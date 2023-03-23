# Construção dos ambientes de desenvolvimento com WSL

## WSL update

Garanta que seu WSL está atualizado

```console
wsl.exe --update
```

## Instalando o WSL Debian
- no prompt rodar o seguinte comando

```console
wsl --install --distribution Debian
```

- definir UNIX username como **dev**
- definir New password como **dev**
- finalizar a instalação.

## Criando ambientes específicos

- Criar o diretório no D:\WSLWorkspaces
```console
mkdir D:\WSLWorkspaces
```
- acessar D:\WSLWorkspaces
```console
cd D:\WSLWorkspaces
d:
```
- Exportar a versão original do Debian para servir como base
```console
wsl --export Debian DebianTemplate
```
- Importar template para novo WSL
```console
wsl --import DebianNode DebianNode DebianTemplate
```
```console
wsl --import DebianJava DebianJava DebianTemplate
```
```console
wsl --import DebianC DebianC DebianTemplate
```
```console
wsl --import DebianMySQL DebianMySQL DebianTemplate
```

## Executando ambientes

```console
wsl -d DebianJava
```

## Removendo WSL 

```console
wsl --unregister DebianJava 
```

## Navegação

- [Construção dos ambientes de desenvolvimento com WSL](README.md)
- [Debian Docker](DebianDocker.md)
- [WSL2 Forward Port](ForwardPort.md)
- [Owncloud](owncloud.md)
- [CaddyReverseProxy](CaddyReverseProxy.md)
