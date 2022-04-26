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
