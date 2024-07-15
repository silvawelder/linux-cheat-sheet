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
