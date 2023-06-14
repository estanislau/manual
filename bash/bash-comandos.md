# Comandos do Bash

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


```
```
```
```
```
```
```
```
```
[linux : zsh e Oh my zsh](:/0192a14cad624a65ba3b010150785e31)

${toc}

## Edição de linha de comando
 
| Teclas  | Ação |
| :---: | --- |
| Ctrl-B | Mover o cursor para a esquerda |
| Ctrl-F | Mover o cursor para a direita |
| Ctrl-P | Ver o comando anterior (ou mover o cursor para cima) |
| Ctrl-N | Ver o próximo comando (ou mover o cursor para baixo) |
| Ctrl-A | Mover o cursor para o início da linha |
| Ctrl-E | Mover o cursor para o fim da linha |
| Ctrl-W | Apagar a palavra anterior |
| Ctrl-U | Apagar do cursor até o início da linha |
| Ctrl-K | Apagar do cursor até o final da linha |
| Ctrl-Y | Colar o texto apagado (por exemplo, com Ctrl-U) |
[ Teclas usadas na linha de comando]
# Linux : comandos básicos
## Obtendo ajuda
`$ help` : informações gerais sobre os built-ins do Shell  
`$ aprobos` : mostra informações sobre um tópico   
`$ whatis` : obtém uma breve descrição de um comando do sistema   
`$ info` : para a cessar o manual info.
`$ man` :  a mais completa documentação do Linux  

### man
| Comando | Ação |
| :---: | --- |
| h | Mostra a ajuda do man
| q | Sai do man |
| [N]e | Avança uma linha, ou N linhas, quando especificado |
| [N]y | Volta uma linha, ou N linhas, quando especificado |
| f | Avança uma tela |
| b | Volta uma tela |
| \texto | Procura por um texto no texto apresentado pelo man |
[ Comandos de navegação no man]

Quando alguém se referir a uma página de manual, o número da seção aparecerá entre parênteses ao lado do nome, por exemplo, ping(8). A tabela lista as seções e seus números.

| Seção | Descrição |
| --- | --- |
| 1 | Comandos de usuário: que podem ser executados a partis de um SHell |
| 2 | Chamadas de sistema: funções que têm de ser executadas pelo kernel |
| 3 | Bibliotecas de funções: documentação geral da biblioteca (libc) de programação Unix |
| 4 | Formatos de arquivos especiais: : interface de dispositivos e informações sobre drivers e hardwares |
| 5 | Arquivos de configuração: descrições de arquivo (arquivos de configuração do sistema) e convenções |
| 6 | Jogos e demonstrações (bls) |
| 7 | Pacotes de macro: formatos de arquivo, protocolos de rede, convenções e codificações (ASCII, sufixos e assim por diante) |
| 8 | Comandos de administração do sistema e servidores |
[Seções do manual online]

Você pode selecionar uma página de manual pela seção, o que, às vezes, é importante, pois `man` exibe a primeira página do manual que for encontrada quando uma correspondência for feita com um determinado termo de pesquisa. Por exemplo, para ler a descrição do arquivo `/etc/passwd` (em oposição à descrição do comando `passwd`), você poderá inserir o número da seção antes do nome da página:
`$ man 5 passwd` 
   
- `$ man -k palavra-chave` : buscar uma página do manual contendo uma palavra-chave. Isso é útil se você não souber exatamente o nome do comando que você quer. Por exemplo, se estiver procurando um comando para ordenar (sort) algo, execute:`$ man -k sort`    
- Alguns pacotes descarregam a documentação disponível em `/usr/share/doc`, sem se importar com sistemas de manual online como man ou info. Verifique esse diretório em seu sistema se você se vir procurando documentações. E, é claro, pesquise na Internet.
-  O Projeto GNU decidiu que não gostava muito das páginas de manual e mudou para outro formato chamado info (ou texinfo). Com frequência, essa documentação vai além do que contém uma página de manual típica, mas, às vezes, é mais complexa.  

`Ctrl + D` : em uma linha vazia interrompe a entrada-padrão corrente do terminal (e geralmente encerra um programa). Não o confunda com Ctrl- C   
`Ctrl + C` : encerra um programa independentemente de sua entrada ou de sua saída. 
`Ctrl + L` : limpar o terminal.    

`$ cat /etc/passwd` : exibe o conteúdo do arquivo /etc/passwd, que contém informações do sistema  

`$ cat arquivo1 arquivo2 ...` : exibe o conteúdo de arquivo1, arquivo2 e de qualquer outro arquivo que você especificar (indicado por ...)    

### ls : listando 
`$ ls` : lista o conteúdo de um diretório.  
`$ ls -l` : para obter uma listagem detalhada (longa).   
`$ ls -F` : para exibir informações sobre o tipo de arquivo.
- Ao executar `ls` sem `-a`, você não verá os arquivos de configuração chamados arquivos ponto (dot files). São arquivos e diretórios cujos nomes começam com ponto ( `.` )

### Copiar arquivos e diretórios 
`$ cp` : copia um arquivo  
`$ cp arquivo1 arquivo2` : copiar arquivo1 para arquivo2   
`$ cp arquivo1 ... arquivoN dir` : copiar vários arquivos para um diretório (pasta) chamado dir  

### Mover arquivos e diretórios
`mv` : move e renomeia um arquivo   
`$ mv arquivo1 arquivo2` : para renomear arquivo1 para arquivo2       
`$ mv arquivo1 ... arquivoN dir` : para mover vários arquivos para um diretório diferente.   
  
`$ touch arquivo` : cria um arquivo. Se o arquivo já existir, não irá alterá-lo, porém o timestamp (exibido com `ls -l`) de modificação será atualizado.   

`$ rm arquivo` : para apagar (remover) um arquivo    
`$ echo` : exibe seus argumentos na saída-padrão   

### cd : navegando pelos diretórios
- Quando um path começa com `/` (por exemplo, `/usr/lib`), temos um path completo ou absoluto.
- Um path que ==não comece== com `/` é chamado de path relativo. Na maioria das vezes, você trabalhará com paths relativos, pois já estará no diretório em que deverá estar ou em algum lugar próximo.
- `..` : especifica o pai de um diretório. Por exemplo, se você estiver trabalhando em `/usr/lib`, o path `..` refere-se a `/usr`. De modo semelhante, `../bin` se refere a `/usr/bin`.
- `.` : refere-se ao diretório corrente; por exemplo, se você estiver em `/usr/lib`, o path ponto (`.`) continua sendo `/usr/lib`, e `./X11` é `/usr/lib/X11`.

`$ cd dir` : muda o diretório de trabalho corrente do shell. Se dir for omitido, o shell retornará para o seu diretório home, que é o diretório em que você começou quando fez login.    
`$ cd ../user/` : sobe um nível e redireciona para a pasta `user`   
`$ cd <usuário>`  :  vai para a pasta do usuário especificado.      
`$ cd -` :  vai para o último diretório acessado.   
`$ cd ~` :  vai para o diretório home do usuário.   
`$ cd /` :  vai para o diretório raiz  

### Criando diretórios

`$ mkdir dir` : cria um novo diretório dir.   

Criar vários vários diretórios:   
`$ mkdir -p documents/git/lao`  

Criar um diretório `biblioteca` contendo outros quatro diretórios:  
`mkdir -p biblioteca/{Autores,Artigos,Categorias,Linux}`  

Cria o diretório biblioteca e mais quatro diretórios sendo que o diretório `Autores` conterá mais dois diretórios: 
`mkdir -p biblioteca/{Autores/{Pedro,Eduardo},Artigos,Categorias,Linux}`

`$ rmdir dir` : remove o diretório dir.   
- Se `dir` não estiver vazio, esse comando irá falhar.
- `rm -rf dir` poderá ser usado para apagar um diretório e o seu conteúdo, mas tome cuidado! Esse é um dos poucos comandos que pode causar danos sérios, especialmente se for executado como superusuário. 
- `-r` especifica uma remoção recursiva para apagar repetidamente tudo o que estiver em dir, e
-  `-f` força a operação de remoção. 
-  Não use as flags `-rf` com globs, por exemplo, com um asterisco (`*`). E, acima de tudo, sempre confira o seu comando duas vezes antes de executá-lo.  

`$ grep root /etc/passwd` : exibe as linhas de um arquivo ou de um stream de entrada que correspondam a uma expressão. No exemplo, para exibir as linhas do arquivo `/etc/passwd` que contenham o texto root   
- `$ grep root /etc/*` : verificar todos os arquivos em `/etc` que contenham a palavra root
- `-i` : para correspondências que não levem em conta a diferença entre letras maiúsculas e minúsculas
- `-v` : que inverte a pesquisa, ou seja, exibe todas as linhas em que não há correspondência. Há também uma variante mais eficaz chamada egrep (que é apenas um sinônimo para grep -E).

`less /usr/share/dict/words` :para efetuar paginação em um arquivo extenso como `/usr/share/dict/words`. Você verá o conteúdo do arquivo, uma tela cheia de cada vez. 
- Pressione a barra de espaço para avançar no arquivo e 
- `b` para retornar uma tela cheia. 
- `q` para sair   
`$ grep ie /usr/share/dict/words | less` : um exemplo do envio da saída de um comando grep para less   

### pwd : o diretório atual
`pwd` : (print working directory, ou exibir diretório de trabalho) simplesmente mostra o nome do diretório de trabalho corrente.
- `pwd -P` : links simbólicos às vezes, podem esconder o path completo verdadeiro do diretório de trabalho corrente. Use `pwd -P` para acabar com essa confusão.   

### diff : diferença entre arquivos
`$ diff arquivo1 arquivo2` : para ver as diferenças entre dois arquivos texto  
- `diff -u` : quando precisam enviá-la para alguém, pois as ferramentas automatizadas podem fazer melhor uso dela 

`$ file arquivo` : se você vir um arquivo e não estiver certo sobre o seu formato, procure usar o comando file para ver se o sistema consegue adivinhar  

`$ find dir -name arquivo -print` : execute find para descobrir em que local está arquivo em dir      

`$ head /etc/passwd` : mostra as dez primeiras linhas do arquivo de senhas 

`$ tail /etc/passwd` : mostra as dez últimas linhas do arquivo de senhas  

`$ sort` : coloca rapidamente as linhas de um arquivo-texto em ordem alfanumérica. Se as linhas do arquivo começarem com números e você quiser ordená-las numericamente, utilize a opção `-n`. A opção `-r` inverte a ordenação  

`passwd` : para modificar sua senha
- Uma das maneiras mais fáceis de criar uma boa senha é escolher uma frase, gerar um acrônimo a partir dela e, em seguida, modificar esse acrônimo com um número ou algum sinal de pontuação.


# Entrada e saída de shell
`$ comando > arquivo` : Para enviar a saída de comando para um arquivo em vez de enviar para o terminal, use o caractere de redirecionamento `>`   
- O shell cria arquivo, caso ele ainda não exista. Se arquivo existir, o shell apagará o arquivo original antes (sobrescreverá). Essa é uma maneira prática de reunir a saída em um só local ao executar sequências de comandos relacionados.  
`$ comando >> arquivo` : A saída pode ser concatenada ao arquivo em vez de sobrescrevê-lo, usando a sintaxe de redirecionamento `>>`    
- Para enviar a saída-padrão de um comando para a entrada-padrão de outro, utilize o caractere de pipe (`|`).   
`$ head /proc/cpuinfo`    
`$ head /proc/cpuinfo | tr a-z A-Z`    
	- A saída pode ser enviada para qualquer quantidade desejada de comandos com pipe; basta adicionar outro pipe antes de cada comando adicional.  
 
## Erro-padrão
Ocasionalmente, você poderá redirecionar a saída-padrão, porém perceberá que o programa continua exibindo informações no terminal. Isso é chamado de erro-padrão (stderr); é um stream de saída adicional para diagnósticos e depuração. Por exemplo, este comando gera um erro:  
`$ ls /fffffffff > f` 

Após o comando ter sido concluído, `f` deverá estar vazio, porém você continuará vendo a mensagem de erro a seguir no terminal como erro-padrão: 
`ls: cannot access /fffffffff: No such file or directory`

Se quiser, você poderá redirecionar o erro-padrão. Por exemplo, para ==enviar a saída- padrão== para `f` e o ==erro-padrão para `e`==, use a sintaxe `2>`, desta maneira:

`$ ls /fffffffff > f 2> e` 

O número `2` especifica o ID do stream modificado pelo shell. O ID de stream ==`1`
corresponde à saída-padrão== (default), e ==`2` é o erro-padrão==.
Você também pode enviar o erro-padrão para o mesmo local que stdout usando a notação `>&`. Por exemplo, para ==enviar tanto a saída-padrão quanto o erro-padrão== para o arquivo chamado `f`, experimente executar este comando:

`$ ls /fffffffff > f 2>&1`

## Redirecionamento da entrada-padrão
Para canalizar um arquivo para a entrada-padrão de um programa, utilize o operador `<`:

`$ head < /proc/cpuinfo` 

Ocasionalmente, você irá se deparar com um programa que exija esse tipo de redirecionamento, porém, pelo fato de a maioria dos comandos Unix aceitar nomes de arquivo como argumento, isso não será muito comum. Por exemplo, o comando anterior poderia ter sido escrito como `head /proc/cpuinfo.`

## Anatomia de uma mensagem de erro UNIX
`$ ls /dsafsda  
ls: cannot access /dsafsda: No such file or directory`

Há três componentes nessa mensagem:
- O nome do programa, que é `ls`. Alguns programas omitem essa informação de identificação.
- O nome do arquivo, `/dsafsda`, que é uma informação mais específica. Há um problema com esse path.
- O erro `No such file or directory` (esse arquivo ou diretório não existe) indica o problema com o nome do arquivo.

Reunindo tudo, você terá algo como “ls tentou abrir /dsafsda, porém não pôde porque ele não existe”. Isso pode parecer óbvio, mas essas mensagens podem se tornar um pouco confusas quando um shell script que inclua um comando incorreto com um nome diferente é executado.  
==Ao tentar solucionar os problemas, sempre trate o primeiro erro antes.== Alguns programas informam que não podem fazer algo antes de relatar uma série de outros problemas.
Depois dessa informação, há uma lista enorme de outras mensagens de erro que parecem indicar uma total catástrofe. ==Não deixe que esses outros erros o distraiam.==

==Observação:== não confunda mensagens de erro com mensagens de aviso (**warnings**). Os avisos geralmente se parecem com os erros, porém contêm a palavra warning. Um aviso normalmente indica que algo está errado, mas que o programa continuará tentando executar de qualquer maneira. Para corrigir um problema apontado em uma mensagem de aviso, talvez seja necessário ir atrás de um processo e matá-lo antes de executar qualquer outra tarefa.

### Erros comuns
Muitos erros que você verá em programas Unix resultam de erros associados a arquivos e processos.

### ps : listando processos e manipulando processos

`$ ps` : para uma listagem rápida dos processos em execução  
`ps x` : mostra todos os processos em execução  
`ps ax` : mostra todos os processos do sistema, e não apenas aqueles dos quais você é o proprietário.  
`ps u` : inclui informações mais detalhadas sobre os processos.  
`ps w` : mostra os nomes completos dos comandos, e não apenas o que cabe em uma linha.  

Observação: Para verificar um processo específico, adicione o seu PID na lista de argumentos do comando `ps`

### kill : matando processos
`$ kill pid` : Para encerrar um processo, envie-lhe um sinal com o comando kill  
`$ kill -STOP pid` : para congelar um processo em vez de encerrá-lo
`$ kill -CONT pi` : Use o sinal CONT para continuar a execução do processo novamente   

### Processos em background
Normalmente, ao executar um comando Unix a partir do shell, você não terá o prompt de shell de volta até que o programa tenha acabado de executar.   
Um processo pode ser desassociado do shell e colocado em “background” com o uso de `&` (ampersand, ou “e comercial”); isso fará o prompt ser devolvido:  
`$ gunzip arquivo.gz &` :    

## Modos de permissões de arquivo
Obviamente, você não deve permitir que os arquivos possam ser globalmente escritos, pois fazer isso dará capacidade a qualquer pessoa em seu sistema de alterá-los.   

| Letra	|	Descrição		|
| :---: | --- |
| u | user : usuário |
| g | group : grupo |
| o | other : outros | 

`$ groups` : para ver em que grupos você está.  
`$ chmod` : para alterar permissões.  

Inicialmente, selecione o conjunto de permissões que você quer mudar e, em seguida, o bit a ser alterado.   

`$ chmod go+r arquivo`  : para adicionar permissões de leitura para grupo (g) e para outros (o, de “other”) em arquivo. 
 
### Modos de permissão absolutos
| Modo | Significado | Usado para |
| --- | --- | --- |
| 644 | usuário: leitura/escrita; grupo, outros: leitura | arquivos | 
| 600 | usuário: leitura/escrita; grupo, outros: nenhum | arquivos |
| 755 | usuário: leitura/escrita/execução; grupo, outros: leitura/execução | diretórios, programas |
| 700 | usuário: leitura/escrita/execução; grupo, outros: nenhum | diretórios, programas |
| 711 | usuário: leitura/escrita/execução; grupo, outros: execução | diretórios |
[ Modos de permissão absolutos ]

`$ chmod 644 arquivo` : Essa alteração é chamada de absoluta, pois ela configura todos os bits de permissão de uma só vez.    

O conteúdo de um diretório pode ser listado se puder ser lido, porém ==você só poderá acessar um arquivo em um diretório se o diretório for executável.== 

Você pode especificar um conjunto de permissões default usando o comando de shell umask, que aplica um conjunto predefinido de permissões a qualquer arquivo novo que você criar.   

### Conjunto de permissões default
Você deverá ==colocar o comando `umask` com o modo desejado em um dos seus arquivos de inicialização== para que suas novas permissões default se apliquem às sessões seguintes.  

`$ umask 022` : se quiser que todos possam ver os arquivos e diretórios que você criar  
`$ umask 077` : se não quiser que todos possam ver os arquivos e diretórios que você criar

## Links simbólicos
Os links simbólicos são apenas nomes que apontam para outros nomes.  Eles oferecem uma maneira conveniente de organizar e compartilhar arquivos, além de servirem para corrigir pequenos problemas.
- Você não poderá identificar as características do alvo de um link simplesmente olhando para o nome desse link; 
- você deverá segui-lo para ver se ele aponta para um arquivo ou um diretório;
- seu sistema também pode ter links que apontem para outros links – são chamados de **links simbólicos encadeados.**
- Ao criar um link simbólico, ==verifique o comando duas vezes antes de executá-lo==, pois muitos erros podem ocorrer.
- Se algo der errado na criação de um link simbólico para um diretório, verifique se não há links simbólicos perdidos nesse diretório e remova-os
- você pode facilmente editar o que você pensa ser uma cópia de um arquivo, mas que, na realidade, é um link simbólico para o original.


`$ ln -s alvo nomedolink` : criar um link simbólico de alvo para nomedolink. 
- O argumento `nomedolink` corresponde ao nome do link simbólico, o argumento `alvo` é o path do arquivo ou do diretório para o qual o link aponta e a flag `-s` especifica um link simbólico (veja o aviso mais adiante).   
- não se esqueça da opção `-s` ao criar um link simbólico. Sem ele, `ln` criará um hard link e dará um nome de arquivo adicional a um único arquivo. O novo nome de arquivo terá o status do antigo; ele apontará (fará o link) diretamente para os dados do arquivo em vez de fazê-lo para outro nome de arquivo, como ocorre com um link simbólico. Os hard links podem ser mais confusos ainda que os links simbólicos.

`pwd -P` : links simbólicos às vezes, podem esconder o path completo verdadeiro do diretório de trabalho corrente. Use `pwd -P` para acabar com essa confusão.   

## Arquivamento e compressão de arquivos

### gzip (compactação)

- gzip não faz arquivamento, ou seja, ela não empacota vários arquivos e diretórios em um só arquivo.  
- gzip apenas compacta o original; não gera uma cópia compactada do original. 

`$ gzip arquivo` : para compactar     
`$ gunzip arquivo.gz` : para descompactar     

### tar (empacotamento)
`$ tar cvf <arquivo.tar> arquivo1 arquivo2 ...` :  empacota   
`$ tar xvf <arquivo.tar>` : desempacota.   



Arquivos tar se encontrarem normalmente compactados, com nomes de arquivo terminados com .tar.gz.   
`$ gunzip arquivo.tar.gz` : descompacta arquivo gzip  
`$ tar ztvf arquivo.tar.gz` : verificar um arquivo compactado     

- c : ativa o modo de criação (create mode)
- v : saída mais extensa para diagnóstico: mostra os nomes dos arquivos e dos diretórios.
- vv : saída mais extensa e detalhes como o tamanho e as permissões dos arquivos
- f : indica a opção de arquivo. 
	- O argumento na linha de comando após a flag `f` deve ser o arquivo a ser criado.  
	- Para usar a entrada ou a saída-padrão, digite um traço (`-`) no lugar do nome do arquivo. (?)  
- t : lista o conteúdo de um arquivo
- x :  modo de extração (desempacotamento)
- z : comprime ou descomprime o arquivo tar resultante

- tar não faz compactação, apenas **arquivamento**.
- normalmente possuem o sufixo `.tar` que é uma convenção porém não é obrigatório.
- não apaga o arquivo.tar após extrair o seu conteúdo.
- podemos extrair partes individuais do arquivo ao inserir os nomes das partes no final da linha de comando, porém seus nomes exatos deverão ser conhecidos (veja "modo tabela de conteúdo")
- um arquivo `.tgz` é igual a um arquivo `.tar.gz`. O sufixo foi concebido para se adequar aos sistemas de arquivo FAT (baseados em MS-DOS).

#### Modo tabela de conteúdo
Antes de desempacotar um arquivo `.tar`, normalmente é uma boa ideia verificar o seu conteúdo usando o modo tabela de conteúdo (*table-of-contents mode*) usando a flag `t` no lugar da flag `x`.
- Esse modo verifica a integridade básica do arquivo tar e exibe os nomes de todos os arquivos nele contidos. 
- Se um arquivo tar não for testado antes de ser desempacotado, você poderá acabar descarregando uma quantidade enorme de arquivos confusos no diretório corrente, que poderá ser bem difícil de limpar.
- considere o uso da opção `p` para preservar as permissões. Use-a em modo de extração para sobrescrever o seu `umask` e obter as permissões exatas especificadas no arquivo tar. 
	- as permissões serão configuradas somente após a verificação completa do arquivo tar.
	- A opção `p` é default ao trabalhar como superusuário. 

### zcat
Combina as funções de arquivamento e de compressão usando um pipeline.
`$ zcat arquivo.tar.gz | tar xvf -` : pipeline de comandos para descompactar .gz e desempacotar .tar.

### bz2
- geralmente compacta um pouco melhor os arquivos-texto
- arquivos compactados terminam com .bz2
- o programa de descompactação a ser usado é o bunzip2
- a opção de compactação/descompactação do bzip2 para o tar é j.

## Usuário

`# userdel -r usuario` : remover usuário

`# useradd -m usuario` : criar usuário (-m para criar o diretório)  

`# sudo usermod -aG sudo username` : adicione o usuário ao grupo sudo  

`# chsh -s /bin/bash usuario` : Altere o shell do usuário  




 ##  Globbing no shell (caracteres-curinga)
 O shell faz a correspondência dos argumentos contendo globs com nomes de arquivo, substitui os argumentos por esses nomes e, em seguida, executa a linha de comando revisada. A substituição é chamada de expansão porque o shell faz a substituição por todos os nomes de arquivo correspondentes.  
  
  `*` : diz ao shell para efetuar a correspondência com qualquer quantidade de caracteres arbitrários
  - `at*` : é expandido com todos os nomes de arquivo que comecem com at. 
- `*at` : é expandido com todos os nomes de arquivo que terminem com at. 
- `*at*` : é expandido com todos os nomes de arquivo que contenham at.  

`?` : instrui o shell a efetuar a correspondência exata com um caractere arbitrário.  Se não quiser que o shell faça a expansão de um glob em um comando, coloque o glob entre aspas simples `''`  
 - `b?at` : corresponde a boat e a brat.

## Arquivos pontos
Você poderá ter problemas com globs porque `.*` corresponde a `.` e a `..` (os diretórios corrente e pai). Pode ser que você queira usar um padrão como `.[^.]*` ou `.??*` para obter todos os arquivos ponto, exceto os diretórios corrente e pai.  

- Ao executar `ls` sem `-a`, você não verá os arquivos de configuração chamados arquivos ponto (dot files). São arquivos e diretórios cujos nomes começam com ponto ( `.` )
- Os globs de shell não farão a correspondência com arquivos ponto, a menos que você utilize explicitamente um padrão como `.*`

## Editores

`$ pico`     
`$ nano`   
`$ vi`   
`$ emacs`    
 
 ## Glossário
- Globbing : O shell pode efetuar correspondência de padrões simples com nomes de arquivos e de diretórios – processo conhecido como globbing, semelhante ao conceito de caracteres- curinga em outros sistemas.
- built-ins : são comandos que são incorporados ao Shell, isto é, não são instruções autônomas como o `who`, por exemplo. São comandos cujos códigos se encotram incorporados ao código do Shell.

[Permissão sudo](:/6b591dc806e24521bbb529ceea92a094)


## Instalar comando cal
```
$ apt install ncal
```




















  
   



