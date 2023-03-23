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