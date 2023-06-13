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
Space					seleção
C-b [					modo cópia
Enter					copiar
C-b ]					colar
