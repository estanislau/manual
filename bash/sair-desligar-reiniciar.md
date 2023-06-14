# Sair, desligar, reiniciar

## Sair do sistema:
Ctrl + d

## Finalizar o Shell
```
exit
```

Outra forma de terminar um shell: quando o shell é iniciado a partir de um login, é possível terminá-lo e encerrar, ao mesmo tempo, toda a sessão do usuário com o comando `logout`.

```
logout
```

## Desligar
```
halt
```

```
poweroff
```

```
init 0
```


## shutdown 
`-h` : halt
```
shutdown -h now
```

```
shutdown -r now
```

Programar o desligamento:

```
shutdown - h 18:00
```

Cancelar o shutdown:
```
shutdown -c
```

Cancelar o shutdown com aviso:
```
shutdown -c "Cancelado o reinicio programado"
```

Acrescentar mais 30 minutos a programação de shutdown:
```
shutdown +30
```

Reiniciar em 30 minutos:
```
shutdown -r +30
```

Reiniciar em 30 minutos com aviso:
```
shutdown -r +30 "Vamos reiniciar em 30 minutos"
```

## Reiniciar
`-r` : reboot
```
Shutdwon -r now
```

```
reboot
```

```
init 6
```

## Help 
```
shutdown --help
```
