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
