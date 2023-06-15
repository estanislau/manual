# Comandos tmux

## Ajuda
C-b ?					buffer de ajuda
tmux -V					versão do tmux

## Sessão
tmux new -s <sessao> -n <janela> -d	cria sessão com janela sem conectar (-d, disconect)

## Sessão: reconectar
tmux a					reconecta a última sessão acessada/criada
tmux attach-session			anexa a última sessão
tmux a -t <nome/número>			reconecta a sessão nome/número

C-b (					alterna para a sessão anterior
C-b )					alterna para a sessão posterior

## Janelas
C-b c					cria uma nova janela

### Janelas: navegação
C-b w					menu aberto de janelas
C-b s					menu fechado de janelas

C-b <número>				vai para a janela número índicado
C-b n					vai para a próxima janela (next)
C-b p					vai para a janela anterior (preview)

C-b l					alterna entre janela atual (*) e anterior(-)

## Painéis
C-b q					Mostra o número do painél
C-b h					Corta a janela para painel horizontal
C-b v					Corta a janela para painel vertical
C-b !					Converte o painel para uma nova janela

### Painéis: navegação
C-b setas				Vai para o painel no sentido da seta
C-b q <número>				Vai para o painel número
C-b o					Vai para o próximo painel
C-b ;					Retorna para o último painel ativo
C-b {					Troca a posição do painel para trás
C-b }					Troca a posição do paiel para frente

### Painéis: redimensionar
C-b z					Zoom no painel ativo maximizando-o
C-b E					Iguala as dimensões dos painéis

C-b setas direita/esquerda		redimensiona painel esquerda/direita (manter pressionado C-b)
C-b Meta setas acima/abaixo		redimensiona os painéis para acima/abaixo (manter pressionado C-b)

C-b M-1					Layout horizontal uniforme
C-b M-2					Layout vertical uniforme
C-b M-3					Layout horizontal principal
C-b M-4					Layout vertical principal
C-b M-5					Layout lado a lado

## Renomear
tmux rename-session -t <atual> <novo>	renomeia a sessão quando fora do tmux
C-b $					renomeia a sessão quando dentro do tmux
C-b ,					renomeia a janela atual

## Destruir
tmux kill-session -t <nome/número>	destrói sessão nome/número
tmux kill-server			destrói todas as sessões

C-b &					destrói a janela corrente e seus painéis (pede confirmação)
C-b x					destrói o painel ativo (pede confirmação)

## Buffer
C-b PagUp/Down				sobre/desce página (buffer)
/					Inicia a busca após o cursor
?					inicia a busca antes do cursor
n					próxima ocorrência
m					ocorrência anterior

## Modo comando
set -g mouseon				Ativa o modo mouse
Shift +					seleciona o texto

## Modo comando: vi
setw -g mode-keys vi			ativa modo vi
^					início de linha
$					final de linha

C-b [                                   Entre no modo de cópia
Barra espaço                            Entra no modo seleção
Setas                                   Movimenta para selecionar
Enter                                   Copia para o buffer
C-b ]                                   Cola o buffer mais recente




## tmuxinator
### Configurações
`alias mux="tmuxinator"`: crie um alias no `.bashrc`
` ~/.tmuxinator/monitor.yml`: caminho do script tmuxinator

### Comandos
`mux <nome-script>`: inicia o script

`mux new <nome-script>`: cria um script
`mux edit <nome-script>`: edita um script
`mux debug <nome-script`: depuração de script
`mux debug <niome-script> > test.sh`: saída do log da depuração

Copie um projeto existente. Aliado a `c` e `cp
```
tmuxinator copy [existing] [new]
```

Liste todos os projetos que você configurou. Aliado a l e ls
```
tmuxinator list
```

Remova um projeto. Aliado a rm
```
tmuxinator delete [project]
```

Remova todas as configurações, aliases e scripts do tmuxinator. Aliado a `i`
```
tmuxinator implode
```

Examina seu ambiente e identifica problemas com sua configuração
```
tmuxinator doctor
```

Mostra a ajuda do tmuxinator. Aliado a h
```
tmuxinator help
```

Mostra os comandos do shell que são executados para um projeto
```
tmuxinator debug [project]
```

Mostra a versão do tmuxinator.
```
tmuxinator version
```

- gem install tmuxinator - instalação
- mux version - mostra a versão
* * *
- source ~/.bashrc - atualizar o arquivo .bashrc
- export DISABLE_AUTO_TITLE=true - inclua no .bashrc se o nome das janelas não estão sendo exibidos corretamente
* * *
- mux help - mostra a ajuda
* * *
- mux new <nome-projeto> - cria um projeto (script)
- mux new ~/.config/tmuxinator <nome-projeto> - cria um projeto no local determinado
- mux edit <nome-projeto> - editar o script
- mux open <nome-projeto> - editar o script
- mux <nome-projeto> - executa o script
* * *
- mux copy [existente] [novo] - copia um projeto existente
- mux list - lista todos os projetos
- mux delete <nome-projeto> - apaga um projeto
* * *
- mux implode - Remove todas as configurações, aliases e scripts
* * *
- mux doctor - examina seu ambiente e identifica problemas
- mux debug <nome-projeto> - Mostra os comandos do shell que são executados para um projeto
- mux debub <nome-projeto> > test.sh - redireciona o debug para ´test.sh


# Atualizar .tmux.conf
Se `bind r source-file ~/.tmux.conf` estiver em `.tmux.conf`, atualize com:
`C-b r` 


Use o comando (Ctrl+Space, Shift+:)
`C-b :`  e digite: `source-file ~/.tmux.conf`

