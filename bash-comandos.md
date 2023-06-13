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



