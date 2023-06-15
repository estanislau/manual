# SSH

## Acesso

```
ssh pi@192.168.0.102
```

Com definição de porta:  
```
ssh pi@192.168.0.102 -p 22
```

Modo verbose com definição de porta:  
```
ssh -v pi@192.168.0.102 -p 22
```

Reiniciar (necessário após uma configuração):
```
sudo service ssh restart
sudo restart ssh
```

Tesde de acesso SSH
```
ssh -T <email@cadastrado> 
```

Duas formas para sair:
```
exit
logout
```

## Transferência com scp

### Opções 
```
scp -Cv		# compactar com verbose
scp -c <metodo> # método de criptografia (2des, aes-128, blowfish)
csp -P <numero>	# definir a porta 
```

### Transferência de arquivo
Enviar arquivo:
```
scp <arquivo> pi@192.168.0.102:~
```

Solicitar arquivo: 
```
scp  estanislau@192.168.0.109:<caminho/arquivo> <novo-nome-arquivo>
```

### Transferência de diretório
```
scp -r <caminho-origem> pi@192.168.0.102:<caminho-destino> 
```
