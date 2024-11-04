# centOS Commands



## Instalação de pacotes .rpm

```sudo rpm -Uvh <package>.rpm```


## yum

### pesquisa

```yum search <package name>```

### verifica versão

```yum info <package name>```

### desinstala pacote

```yum remove <package name>```


## gerenciamento de processos

### lista processo baseado na porta que ele esta rodando 

```sudo lsof -i :25672```

### mata o processo    

```sudo kill <PID>```



## firewalld

### Libera trafego de entrada nas portas    

```sudo firewall-cmd --zone=public --permanent --add-port=4369/tcp```

### Recarrega a sessão atual do firewalld para aplicar mudanças realizadas

```sudo firewall-cmd --reload```

### Show all rules in firewalld
```sudo firewall-cmd --list-all```


## network commands

### Lista conexões filtrando por porta   

```sudo netstat -putan | grep <port>```


# Suse Linux

## Network

### Interface configuration
``` vi /etc/sysconfig/network/ifcfg-eth0 ```
```
# change like follows (replace IP and other values for your own environment)
BOOTPROTO='static'
# broadcast address
BROADCAST='10.0.0.255'
# server's static IP address
IPADDR='10.0.0.30'
# subnet mask
NETMASK='255.255.255.0'
# network address
NETWORK='10.0.0.0'
STARTMODE='auto'
DHCLIENT_SET_DEFAULT_ROUTE='yes'
```

### Gateway configuration
``` vi /etc/sysconfig/network/routes ```
```
# Destination   [Gateway]     mask           Interface
default        <gateway-ip> <network-mask>   eth0 
```
``` systemctl restart wicked ```
### Restart Network "service" wicked

```
systemctl restart wicked

systemctl status wicked
```

### Validate if changes are applied to gateway
```
ip route
```

### DNS configuration
``` vi /etc/sysconfig/network/config ```
```
NETCONFIG_DNS_STATIC_SERVERS="8.8.8.8"
```
``` systemctl restart wicked ```

### Test if DNS server is resolving
```
ping -c 4 google.com

or

nslookup google.com

```
## Licesing

### Add license

``` SUSEConnect -r <license-id> -e  <license-email> ```

### Update packages

``` zypper update ```

## Add external package repository

``` 
zypper addrepo https://download.opensuse.org/repositories/server:http/15.5/server:http.repo
zypper addrepo https://download.opensuse.org/repositories/network/15.5/network.repo
zypper refresh
```

# General

## Daily Heroes:
• ps aux | grep {process} - Encontre aquele processo furtivo
• lsof -i :{port} - Quem está monopolizando aquela porta?
• df -h - O clássico verificador de "estamos sem espaço"
• netstat -tulpn - Detetive de conexão de rede

## Log Warriors:
• tail -f /var/log/* - Observador de log em tempo real
• journalctl -fu service-name - Perseguidor de log do SystemD
• grep -r "error" . - O caçador de erros
• zcat access.log.gz | grep "500" - Ninja de log compactado
• less +F - O melhor comando tail

## Container Whisperers:
• docker ps --format '{{.Names}} {{.Status}}' - Verificação de status limpa
• docker stats --no-stream - Verificação rápida de recursos
• crictl logs {container} - Histórias brutas de contêineres
• docker exec -it - O backdoor do contêiner
• podman top - Espiada de processos dentro de contêineres

## System Detectives:
• htop - Contador de histórias de recursos do sistema
• iostat -xz 1 - Poeta de desempenho de disco
• free -h - Solucionador de mistérios de memória
• vmstat 1 - Sinais vitais do sistema
• dmesg -T | tail - Fofocas recentes do Kernel

## Network Ninjas:
• curl -v - Depurador de conversação HTTP
• dig +short - Pesquisa rápida de DNS
• ss -tunlp - Estatísticas de socket simplificadas
• iptables -L - Leitor de regras de firewall
• traceroute - Localizador de caminho

## File Jugglers:
• find . -name "*.yaml" -type f - Caçador de YAML
• rsync -avz - Melhor copiador de arquivos
• tar -xvf - O descompactador (sim, todos nós pesquisamos isso no Google)
• ln -s - Assistente de Symlink
• chmod +x - Torna executável

## Performance Profilers:
• strace -p {pid} - Espião de chamada de sistema
• tcpdump -i any - Farejador de pacotes de rede
• sar -n DEV 1 - Monitoramento de estatísticas de rede
• uptime - Média de carga em resumo
• top -c - Visualizador de processos clássico

## Git Essentials:
• git log --oneline - Histórico simplificado
• git reset --hard HEAD^ - Apagador de "oops"
• git stash - O ocultador de trabalho
• git diff --cached - O que é preparado?
• git blame - O resolvedor "quem fez isso?"

## Correções rápidas:
• sudo !! - Execute o último comando com sudo
• ctrl+r - Pesquisa de histórico de comandos
• history | grep - Máquina do tempo de comando
• alias - Criador de atalhos de comando
• watch - Repetidor de comandos
