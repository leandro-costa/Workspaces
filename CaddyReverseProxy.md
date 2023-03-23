# Caddy Reverse Proxy

baixar o Caddy no github

https://github.com/caddyserver/caddy/releases

Criar o arquivo `Caddyfile` com o seguinte conteúdo

```console
ip-windows:8080 {
    reverse_proxy ip-wsl:8080 
}
```

executar o Caddy passando o arquivo de configuração `Caddyfile`

```console
caddy.exe run --config Caddyfile
```

## Referência

- https://caddyserver.com/docs/quick-starts/reverse-proxy


## Navegação

- [Construção dos ambientes de desenvolvimento com WSL](README.md)
- [Debian Docker](DebianDocker.md)
- [WSL2 Forward Port](ForwardPort.md)
- [Owncloud](owncloud.md)
- [CaddyReverseProxy](CaddyReverseProxy.md)
