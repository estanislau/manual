# mkdir

OPÇÕES | SIGNIFICADOS
--------------|---------------------
-p | Se nenhum erro existir, crie diretórios pai conforme necessário. Cria qualquer diretório pai faltante para cada argumento diretório para diretórios pais é fixo pela umask modificada por "u+wx". Ignora argumentos que correspondem a diretórios existentes. (Assim, se um diretório /a existe, então "mkdir /a" vai provocar um erro, mas "mkdir -p /a" não.)

Criando diretórios:  
``` 
$ mkdir dir
```

Criar vários diretórios simultaneamente:
```
mkdir diretorio1 diretorio2 diretorio3
```

Criar vários diretórios e seus subdiretórios `documents/git/lao` com a flag `-p`
``` 
$ mkdir -p documents/git/lao
```

Criar um diretório `biblioteca` contendo outros quatro diretórios:
``` 
mkdir -p biblioteca/{Autores,Artigos,Categorias,Linux}
```

Cria o diretório biblioteca e mais quatro diretórios sendo que o diretório `Autores` conterá mais dois diretórios: 
``` 
mkdir -p biblioteca/{Autores/{Pedro,Eduardo},Artigos,Categorias,Linux}
```

Criará um diretório `curso` pendurado no diretório acima do corrente, isto é, criará um diretório ao lado do corrente
``` 
$ mkdir ../curso
```

Criará um diretório `curso` sob o diretório home do usuário `jneves`
``` 
$ mkdir ~jneves/curso
```
