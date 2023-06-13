[Tmux Cheat Sheet & Quick Reference](https://tmuxcheatsheet.com)

C = Ctrl 
S = Super (ou M)

# Trabalhando com buffers

Algumas operações fazem o tmux entrar em modo 'buffer', por exemplo: 
	
- Rolando a saída do shell com o mouse (com 'set -g mouse on');
- Com o atalho 'C-b PgUp';
- Acessando mensagens do tmux ou a ajuda;
- Iniciando o modo cópia.


# Sessões

tmux					Cria nova sessão
tmux new				Cria nova sessão
tmux new-session			Cria nova sessão
:new					Cria nova sessão
tmux new -d				Cria nova sessão mas não conecta (d = disconect)
tmux new -s <nome-sessao>		Cria nova sessão com um nome (s = session)
tmux new -s <nome-sessao> -d		Cria nova sessão com nome mas não conecta
tmux new -s mysession -n mywindow 	Cria nova sessão com o nome mysession e janela mywindow (n = name)

# Renomear sessão

tmux rename-session -t <atual> <novo>	Renomeia a sessão fora do tmux 
C-b $					Renomeia a sessão dentro do tmux

C-b '     				Solicitar índice de janela para selecionar
C-b .       				Mover a janela atual

# Listando sessões

tmux ls					Lista as sessões

# Reconectando  a uma sessão

tmux a					Reconectando a última sessão acessada (a = attach, conectar) 
tmux a -t <nome>			Reconectando a sessão <nome> 
tmux a -t 0				Retornar a sessão [0]

# Saindo da sessão
 
C-b d					Desconectar da sessão corrente (sem destruir) 

tmux kill-session -t <numero/nome>	Destrói sessão <num/nome> (-t = target, alvo) 
tmux kill-session -t 1			Destrói sessão [1]
tmux kill-ses -t <numero/nome>		Destrói sessão <num/nome> (-t = target, alvo) 
tmux kill-server			Destrói todas as sessões 


# Saindo sem preservar a sessão

C-b x					Fechando cada painel aberto (confirma) 
C-b &					Fechando cada janela aberta (confirma)

C-d					Terminando cada sessão do shell
exit					Terminando cada sessão do shell

# Janelas
 
C-b w       				Escolha uma janela de uma lista (aberto)
C-b s    	   			Escolha uma sessão de uma lista (fechado)
	setas				Ocultar/mostrar
	(#)				Escolha o número para ir a janela
	q				Sair (q = quit, sair)

C-b i       				Informações da janela de exibição
C-b c       				Criar uma nova janela (c = create, criar)	
C-b ,       				Renomear a janela atual
C-b &       				Matar a janela atual	

C-b n       				Selecione a próxima janela (n = next, próximo)
C-b p       				Selecione a janela anterior (p = preview, pré-estréia)
C-b l       				Selecione a janela atual (*) anterior (-)
C-b q <índice>				Vai para a janela de índice 'n' (vermelho = ativo)

C-b DC      				Redefinir para que a parte visível da janela siga o cursor
C-b Seta    				Move para a janela/painel da direção da seta

# Divisão de janelas em painéis

C-b %					Divide o painel verticalmente
C-b "					Divide o painel horizontalmente

# Redimensionamento entre painéis

C-b M-setas				Redimensiona os painéis verticalmente
C-b M-Up    				Redimensione o painel para cima
C-b M-Down  				Redimensione o painel para baixo
C-b M-Left  				Redimensione o painel à esquerda
C-b M-Right 				Redimensione o painel direito

C-b C-setas				Redimensiona os painéis horizontalmente
C-b C-Up    				Redimensionar o painel para cima
C-b C-Down  				Redimensionar o painel para baixo
C-b C-Left  				Redimensionar o painel esquerdo
C-b C-Right 				Redimensionar o painel direito

C-b E					Retorna ao tamanho original

# Movimentação entre os painéis

C-b o 		      			Selecione o próximo painel
C-b ;					Volta ao último painel pativo
C-b {					Trocar a posição do painel para a esquerda
C-b }					Trocar a posição do painel para a direita
	
C-b q <índice>				Vai para o painel de índice 'n'

C-b z					Zoom in/out nos painéis
	
# Destruindo painéis

C-b x					Pede confirmação

C-b f       				Procurar um painel
C-b C-o     				Gire pelos painéis	
C-b m       				Marcar o painel
C-b M       				Limpar o painel marcado
C-b !       				Converte o painel para uma nova janela

# Copiar e colar no buffer 

A rigor, o modo buffer é o 'modo cópia':

C-b : setw -q mode-keys vi		Ativar o modo de cópia do vi
Enter					Sai copiando a seleção

C-b [					Entre no modo de cópia
C-Barra espaço				Entra no modo seleção
Setas					Movimenta para selecionar
C-w					Copia para o buffer
C-b ]   	   			Cola o buffer mais recente

C-b Page   				Entre no modo de cópia e role para cima

# Copia e cola com ajuda do terminal 

Shift					Arraste o mouse para marcar o texto
Shift-Bd				Botão direito para opções do terminal (copy, etc)

Para sair do modo buffer, basta teclar 'q'.

# Gerenciador de clipboard ------------------------------------------------------------ # 
	
C-b =					Menu com todas as cópias
<numero>				Retorna e cola a escolha (funciona com Enter)
C-b #					Mostra todas as cópias 
Barra espaço				Entra no modo seleção
Enter					Sai copiando a seleção
C-b [					Cola o que foi selecionado

# Miscelânea -------------------------------------------------------------------------- # 

C-b C-b     				Envie a chave de prefixo
C-b /       				Descrever a vinculação de teclas

C-b #       				Listar todos os buffers de colagem
C-b -       				Excluir o buffer de colagem mais recente
C-b =       				Escolha um buffer de colagem de uma lista

C-b (       				Mudar para cliente anterior
C-b )       				Mudar para o próximo cliente
C-b L       				Mudar para o último cliente
C-b r       				Redesenhar o cliente atual
C-b d       				Desanexar o cliente atual
C-b C-z     				Suspender o cliente atual
C-b D       				Escolha um cliente de uma lista

C-b t       				Mostrar relógio
C-b ~       				Mostrar mensagens

C-b M-1     				Defina o layout horizontal uniforme
C-b M-2     				Defina o layout vertical uniforme
C-b M-3     				Defina o layout horizontal principal
C-b M-4     				Defina o layout vertical principal
C-b M-5     				Selecione o layout lado a lado
C-b Space   				Selecione o próximo layout

C-b M-n     				Selecione a próxima janela com um alerta
C-b M-p     				Selecione a janela anterior com um alerta

C-b M-o     				Gire pelos painéis ao contrário

# Busca ------------------------------------------------------------------------------- # 
	
Tecla '/'				Inicia busca após o cursor
Tecla '?'				Inicia busca antes do cursor
Tecla 'n'				Próxima ocorrência
Tecla 'm'				Ocorrência anterior

C-s					Busca buffer cursor para baixo (/ quando no modo cópia)
C-r					Busca buffer cursor para cima (? quando no modo cópia)

# Ajuda ------------------------------------------------------------------------------- # 

C-b ?					Lista atalhos e comando
man tmux				Páginas man
tmux info				Mostre todas as sessões, janelas, painéis, etc
tmux list-keys			 	Listar associações de teclas	
C-b : list-keys				Listar associações de teclas	

# Movimentação de janelas ------------------------------------------------------------- #

C-b :					Solicita um comando
	swap-window -s 2 -t 1 		Janela de reordenação, janela de troca número 2 (src) e 1 (dst)
	swap-window -t -1		Mova a janela atual para a esquerda em uma posição
	set mouse on			Ativa o modo mouse
