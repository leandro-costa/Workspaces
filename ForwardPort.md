# WSL2 Forward Port

## `wsl.conf` e `.wslconfig`
Você pode definir as configurações para suas distribuições do Linux instaladas que serão aplicadas automaticamente sempre que você iniciar o WSL de duas maneiras, usando:

- `.wslconfig` para definir as configurações globalmente em todas as distribuições instaladas em execução no WSL 2.
- `wsl.conf` para definir as configurações por distribuição para distribuições do Linux em execução no WSL 1 ou WSL 2.

## `.wslconfig`

**Só pode ser usado para distribuições executadas pelo WSL 2**

Para acessar seu `%UserProfile%` diretório, no PowerShell, use 
```console
cd ~
```
para acessar seu diretório base (que normalmente é seu perfil de usuário, C:\Users\<UserName>) 

Outra opção é você pode abrir o Windows Explorador de Arquivos e inserir `%UserProfile%` na barra de endereços. 

O caminho do diretório deve ser semelhante a: 

```console
C:\Users\<UserName>\.wslconfig
```

## Exemplo de arquivo .wslconfig

```console
# Settings apply across all Linux distros running on WSL 2
[wsl2]

# Limits VM memory to use no more than 4 GB, this can be set as whole numbers using GB or MB
memory=4GB 

# Sets the VM to use two virtual processors
processors=2

# Specify a custom Linux kernel to use with your installed distros. The default kernel used can be found at https://github.com/microsoft/WSL2-Linux-Kernel
kernel=C:\\temp\\myCustomKernel

# Sets additional kernel parameters, in this case enabling older Linux base images such as Centos 6
kernelCommandLine = vsyscall=emulate

# Sets amount of swap storage space to 8GB, default is 25% of available RAM
swap=8GB

# Sets swapfile path location, default is %USERPROFILE%\AppData\Local\Temp\swap.vhdx
swapfile=C:\\temp\\wsl-swap.vhdx

# Disable page reporting so WSL retains all allocated memory claimed from Windows and releases none back when free
pageReporting=false

# Turn off default connection to bind WSL 2 localhost to Windows localhost
localhostforwarding=true

# Disables nested virtualization
nestedVirtualization=false

# Turns on output console showing contents of dmesg when opening a WSL 2 distro for debugging
debugConsole=true
```

## A regra de 8 segundos

Você deve aguardar até que o subsistema que executa a distribuição do Linux pare completamente de ser executado e reinicie para que as atualizações de configuração sejam exibidas. Normalmente, isso leva cerca de 8 segundos depois de fechar TODAS as instâncias do shell de distribuição.

```console
wsl --list --running
```
```console
wsl --shutdown
```

## Referências

- https://learn.microsoft.com/pt-br/windows/wsl/wsl-config


## Navegação

- [Construção dos ambientes de desenvolvimento com WSL](README.md)
- [Debian Docker](DebianDocker.md)
- [WSL2 Forward Port](ForwardPort.md)
- [Owncloud](owncloud.md)
- [CaddyReverseProxy](CaddyReverseProxy.md)
