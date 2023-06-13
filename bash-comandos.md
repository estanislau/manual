# Comandos do Bash
## History
`.bash_history`: histórico do shell interativo
`echo $HISTFILE`: mostra o caminho do arquivo do shell interativo

### Configuração do histórico
`HISTSIZE=10000`: altera a quantidade de comandos que podem ser armazenados para 10.000
`HISTSIZE=-1`altera a quantidade de comandos que podem ser armazenados para "ilimitado"
`HISTFILESIZE=10000`: altera a quantidade de comandos que podem ser armazenados para "ilimitado" no shell interativo
`HISTCONTROL=ignoredups`: comandos repetidos não serão acrescentados caso sejam consecutivos

### Mostrar o histórico
`history`: mostra os doze últimos comandos executados
`history -c`: limpar o histórico
`history 3`: mostra os três últimos comandos
`history | less`: mostra da entrada mais perto do início à mais perto do fim
`history | sort -nr | less`: mostra da entrada mais perto do fim à mais perto do início
`history | grep -w cd`: mostra apenas os comandos do histórico que contêm a palavra `cd`
`echo $HISTSIZE`: mostra a quantidade de comandos que podem ser armazenados

### Expansão do histórico
`!!`: reproduz o último comando executado
`!<comando-recente>`: reexecuta o comando mais recente indicado. Ex.: `!grep`
`!?<comando>?`: referencia o comando mais recente que possuia string em qualquer local
`!<ID>`: recupera o comando do ID informado
`!-<numero>`: um valor negativo recupera um comando pela sua posição relativa no histórico em vez da posição relativa
`!-<numero>:p`: exibe o comando do histórico, na posição indicada, mas sem executá-lo. Use `!!` para executá-lo

## Remover
1. Verifique: antes de executar `rm`, execute `ls`com o padrão desejado para ver quais arquivos sào encontrados.
2. Exclua: se a saida de `ls`parecer correta, execute `rm !$` para excluir os mesmo arquivos que foram encontrados.

`rm -i`: solicita confirmação para remover arquivo
`alias rm=`rm -i`: cria um alias para o comando `rm -i` 


# Comandos Linux

## Alias: rm, cp, mv: pede confirmação para executar
Edite o arquivo `/etc/profile` e inclua as linhas para solicitar a confirmação:

```
alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'
```

-f (--force)		Para ignorar o pedido de confirmação

## Links simbólicos
```
 $ ln -s <alvo> <nomedolink>
```

## wc
Exibe o número de linhas, palavras e caracteres
```
wc animals.txt
```
-l número de linhas
-w número de palavras
-c número de caracteres

## ls 
-1 resultados em apenas uma coluna
-C resultados em colunas
-a arquivos ocultos
-l em lista
-h
-F 

## head
Exibe as primeiras linhas de um arquivo
Se omitir `n` exibirá 10 linhas por padrão.
```
head -n3 animals.txt
```
Contar o número de palavras das três primeiras linhas:
```
head -n3 animals.txt|wc -w
```

## cut
Exibe uma ou mais colunas de um arquivo.

Exibe todos os conteúdos que aparecem na segunda coluna:
```
cut -f2 animals.txt
```

Exibe múltiplas colunas, separando seus números com vírgulas ou intervalo numérico:
```
cut -f1,3 animals.txt|head -n3
cut -f1-3 animals.txt|head -n3
```

Exibe os 3 primeiros caracteres de cada linha:
```
cut -c1-3 animals.txt
```

Altera o caractere separador para uma vírgula (`-d,`) em vez de uma tabulação, afim de isolar os sobrenomes dos autores
```
cut -f4 animals.txt|cut -d, -f1
```

-f coluna
-c caracteres
-d<,> delimitador é a vírgula


## grep
Exibe as linhas que contêm uma string específica.
Exibe as linhas que contém a string "Nutshell":
```
grep Nutshell animals.txt
```

Use `-v`para exibir as linhas que não contêm "Nutshell":
```
grep -v Nutshell animals.txt
```

Exibir as linhas que contêm a string "Perl" em arquivos com nomes que terminam em ".txt":
```
grep Perl *.txt
```

## cd
Retorna ao último local
```
cd -
```

## Criar arquivos
Criar arquivos vazios:
```
> nome-arquivo
```
Cria com mensagem:
```
touch "Um texto qualquer" > nome-arquivo
```


```
```
```
```
```
```
```
```
```
