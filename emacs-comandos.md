# emacs: atalho (em revisão)
2022.09.09 14:07


# Iniciando o Emacs --------------------------------------------- #

emacs	      	    	 	 Iniciando o emacs

# Saindo do Emacs ----------------------------------------------- #

C-z	    	  	 	 Suspende ou minimiza
C-x C-z           	 	 Encerra

# Arquivos ------------------------------------------------------ #

C-x C-f	   		 	  Abre um arquivo
C-x C-s                       	  Salva um arquivo
C-x s             	       	  Salva todos os arquivos abertos
C-x i             	       	  Insere outro arquivo neste buffer
C-x C-v           	 	  Substitui este arquivo por outro
C-x C-w		  	 	  Salva o buffer em um arquivo especificado
C-x C-q           	       	  Alterna o estado de somente leitura do buffer

# Ajuda --------------------------------------------------------- #

C-h (ou F1)			  Tecle e siga as instruções
C-x 1             	       	  Remove a janela de ajuda
C-M-v             	 	  Rola a janela de ajuda
C-h a                  	      	  Apropos: mostra comandos que casam com a string
C-h k             	 	  Descreve função associada a teclas
C-h f             	 	  Descreve uma função
C-h m		  	 	  Busca informações específicas do modo

# Recuperando-se de erros --------------------------------------- #

C-g		    	  	  Aborta uma operação
M-x recover-session 	 	  Recupera arquivos após crash
C-x u, C-_, C-/		 	  Desfaz uma alteração
M-x revert-buffer	 	  Restaura um buffer para o arquivo
C-1 			 	  Redesha a tela

# Busca incremental --------------------------------------------- #

C-s		    	 	  Busca para frente
C-r 			       	  Busca para trás
C-M-s 			       	  Busca por expressão regular
C-M-r			       	  Busca por expressão regular para trás

M-p 			       	  Seleciona a string de pesquisa anterior
M-n 			 	  Seleciona a string de pesquisa seguinte
RET 			 	  Sai da busca incremental
DEL 			     	  Desfaz o efeito do último caracter
C-g 			 	  Encerra a busca

C-s, C-r		 	  Novamente para repetir a busca
C-g  			 	  Cancela apenas o que ainda não foi feito

# Movimentação --------------------------------------------------- #

Trás        Frente
C-b 	    C-f			  Um caracter
M-b	    M-f			  Uma palavra
C-p	    C-n			  Uma linha
C-a	    C-e			  Para início ou fim da linha
M-a	    M-e		     	  Sentença
M-{	    M-}			  Parágrafo
C-x [	    C-x ]		  Página
C-M-b	    C-M-f		  Sexp
C-M-a	    C-M-e		  Função
M-<	    M->			  Para início ou fim do buffer

C-v	 		     	  Rolar para próxima tela
M-v			      	  Rolar para tela anterior
C-x <			      	  Rolar para esquerda
C-x >			      	  Rolar para direita
C-u C-1			      	  Rolar a linha corrente para ocentro da tela

# Cortando e apagando --------------------------------------------- #

Trás	    Frente		  Entidade a cortar
DEL	    C-d			  Caracter (apaga, não corta)
M-DEL	    M-d			  Palavra
M-0 C-k	    C-k			  Linha (até o final)
C-x DEL	    M-k		          Sentença
M-- C-M-k   C-M-k		  Sexp

C-w				  Cortar região
M-w				  Copiar a região
M-z char			  Cortar até a próxima ocorrência de char

C-y 			       	  Colar a última coisa cortada
M-y			      	  Substitui a última colagem pela cópia anterior

# Marcando -------------------------------------------------------- #

C-@, C-SPC 			  Posiciona a marca aqui
C-x C-x				  Troca a marca pelo ponto e vice-versa

M-@ 			      	  Coloca a marca arg palavras adiante
M-h			          Marca o parágrafo
C-x C-p				  Marcar a página
C-M-@			          Marca a sexp
C-M-h				  Marca uma função
C-x h			      	  Marca todo buffer

# Busca e substituição -------------------------------------------- #

M-%				  Substitui interativamente uma string
M-x query-replace-regexp	  Usando expressão regularg

Respostas válidas no modo de busca e substituição

SPC	  	     	     	  Substitui esta e prossegue
,				  Substitui esta e entrada e não avança
DEL				  Pula para a próxima sem substituir
!				  Substitui em todo o texto restante
^				  Volta para a palavra anterior
RET				  Encerra
C-r				  Entra na edição recursiva
C-M-c				  Sair da edição recursiva

# Múltiplas janelas ----------------------------------------------- #

Quando forem mostrados dois comandos, o segundo tem comportamento similar para frame.

Janela 	     Frame
C-x 1	     C-x 5 1		  Elimina todas outras janelas/frames
C-x 2	     C-x 5 2		  Divide a janela/frame acima e abaixo
C-x 0	     C-x 5 0		  Elimina esta janela/frame
C-x 3	     	   		  Divide a janela, lado a lado
C-M-v				  Rola a outra janela
C-x o	     C-x 5 o		  Leva o cursor para outra janela/frame
C-x 4 b	     C-x 5 b		  Seleciona um buffer em outra janela
C-x 4 C-o    C-x 5 C-o		  Mostra um buffer em outra janela
C-x 4 f	     C-x 5 f		  Busca um arquivo em outra janela
C-x 4 r	     C-x 5 r		  Busca arquivo (ro) em outra janela
C-x 4 d	     C-x 5 d		  Executa Dired em outra janela
C-x 4 .	     C-x 5 .		  Busca tag em outra janela

C-x ^ 	     	   		  Aumenta a janela na vertical
C-x {				  Estreita a janela
C-x }				  Alarga a janela

# Formatando ------------------------------------------------------ #

TAB	     			  Identa a linha corente (modo)
C-M-\				  Identa a região (modo)
C-M-q				  Identa a sexp (modo)
C-x TAB				  Identa região rigidamente arg colunas

C-o 				  Insere uma nova linha após o ponto
C-M-o				  Move o restante da linha para baixo
C-x C-o				  Apaga linhas em branco em torno do ponto
M-^ 				  Junta a linha com a anterior
M-\				  Apaga todos brancos em torno do ponto
M-SPC				  Insere um espaço em branco

M-q				  Preenche o parágrafo
C-x f				  Define a coluna limite de preenchimento
C-x .				  Define um prefixo para cada linha

# Maiúsculas e minúsculas ------------------------------------------ #

M-u	       		  	  Palavra para maiúsculas
M-l				  Palavra para minúsculas
M-c				  Primeira letra maiúscula (capitalize)

C-x C-u				  Região para maiúsculas
C-x C-l				  Região para minúsculas

# O minibuffer ----------------------------------------------------- #

As teclas seguintes são definidas no minibuffer.

TAB	  	    		  Complete o máximo possível
SPC				  Complete até uma palavra
RET				  Complete e execute
?				  Mostre as opções para completar
M-p				  Busca a entrada anterior no minibuffer
M-n				  Busca a próxima entrada no minibuffer ou o default
M-r				  Busca regexp no histórico para trás
M-s				  Busca regexp no histórico para frente
C-g				  Encerra o comando

C-x ESC ESC			  Para repetir o último comando utilizado
F10 				  Ativa o menu

# Buffers ---------------------------------------------------------- #

C-x b				  Seleciona outro buffer
C-x C-b				  Lista todos buffers
C-x k				  Mata um buffer

# Transposição ----------------------------------------------------- #

C-t 	       			  Transpõe caracteres
M-t				  Transpõe palavras
C-x C-t				  Transpões linhas
C-M-t				  Transpões sexps

# Verificação ortográfica ------------------------------------------ #

M-$	      		  	  Verifica a palavra corrente
M-x ispell-region		  Verifica todas palavras de uma região
M-x ispell-buffer		  Verifica todo o buffer

# Tags ------------------------------------------------------------- #

M-.    				  Busca uma tag (uma definição)
M-x visit-tags-table		  Especifica um novo arquivo de tags
M-x tags-search			  Busca por regexp em todos arquivos
M-x tags-query-replace		  Busca e substitui em todos arquivos
M-, 				  Continua a última busca ou busca e substituição

# Shells ----------------------------------------------------------- #

M-!	 			  Executa um comando do shell
M-|				  Executa um comando do shell na região
C-u M-|				  Filtra uma região por um comando do shell
M-x shell			  Inicia um shell na janela *shell*

# Retângulos ------------------------------------------------------- #

C-x r r	     			  Copia o retângulo para o registrador
C-x r k				  Corta o retângulo
C-x r y				  Cola o retângulo
C-x r o				  Abre o retângulo, movo o texto para direita
C-x r c				  Troca por espaços o conteúdo do retângulo
C-x r t				  Antepões uma linha a string

# Abreviaturas ------------------------------------------------------ #

C-x a g        			  Adiciona uma abreviatura global
C-x a l				  Adiciona abreviatura ao modo local
C-x a i g			  Adiciona globalmente expansão de abreviatura
C-x a i l			  Adiciona localmente expansão de abreviatura
C-x a e 			  Explicitamente expande uma abreviatura

M-/   				  Completa com base em palavras anteriores

# Expressões regulares ---------------------------------------------- #

. (dot)    	       		  Qualquer caracter exceto nova linha
* 				  Zero ou mais repetições
+				  Uma ou mais repetições
?				  Zero ou uma repetição
zc				  Protege o caracter especial c
\|				  ("or")
|( ...\)			  Agrupamento
\n 				  Mesmo texto que n-ésimo grupo
\b				  Quebra de palavra
\B				  Sem quebra de palavra

Casa início	Casa fim	  Entidade
^    		$    		  Linha
\<		\>		  Palavra
\´		\`		  Buffer

Casa esses	Casa os outros	  Classe de caracteres
[ ... ]		[^ ... ]	  Conjunto explícito
\w    		\W     		  Caracter de sintaxe de palavra
\sc		\Sc		  Caracter de sintaxe de c

# Conjutnos de caracteres internacionais ---------------------------- #

C-x RET l      		  	  Espedifica uma língua principal
M-x list-input-methods		  Mostra todos métodos de inserção
C-\ 				  Habilita/desabilita um método de inserção
C-x RET c			  Determina o sistema de condificação
M-x list-coding-systems		  Mostra sistemas de codificação
M-x prefer-coding-system	  Escolhe a codificação preferida

# Info -------------------------------------------------------------- #

C-h i  				  Entrada no leitor de Info
C-h S				  Busca função ou arquivo no Info

Movimentação em um modo:
SPC				  Rola para frente
DEL				  Rola para trás
. (dot)				  Início do noto

Movimentação entre nodos:
n				  Próximo nodo
p				  Nodo anterior
u				  Mover cima cima
m				  Seleciona item do menu pelo nome
n				  Seleciona n-ésimo item do menu
f				  Segue referência cruzada (retorna com l)
l				  Retorna último nodo visitado
d				  Retorna ao diretório de nodos
t				  Ir para o topo do arquivo Info
g				  Ir para qualquer nodo por nome

Outros:
h				  Executar tutorial do Info
i				  Busca pelo assunto no índice
s				  Busca por expressão regular
q				  Sair Info

# Registrador ------------------------------------------------------- #

C-x r s	      			  Salva região em um registrador
C-x r i				  Insere o conteúdo do registrador no buffer

C-x r SPC			  Salva valor do ponto no registrador
X-x r j				  Salta para o ponto salvo no registrador

# Macros de teclado ------------------------------------------------- #

C-x (	    	    		  Inicia a definição de uma macro
C-x )				  Encerra a definição de uma macro
C-x e				  Executa a última macro definida
C-u C-x (			  Adiciona a última macro definida
M-x name-last-kbd-macro		  Nomeia a última macro definida
M-x insert-kbd-macro		  Insere uma definição em Lisp

# Lidando com Emacs List --------------------------------------------- #

C-x C-e	      	    	 	  Avalia sexp antes do ponto
C-M-x				  Avalia a defun corrente
M-x eval-region			  Avalia a região
M-: 				  Lê e avalia o minibuffer
M-x load-library		  Carrega do diretório padrão do sistema

# Personalização simples --------------------------------------------- #

M-x customize	 	 	  Personaliza variáveis e fontes

Fazendo teclas de atalho globais em Emacs Lisp (exemplos):

(global-set-key "C-cg" ´goto-line)
(global-set-key "M-#" ´query-replace-regexp)

# Escrevendo comandos ------------------------------------------------ #

(defun command-name (args)
  "domentation" (interactive "template")
  body)

Um exemplo:

(defun this-line-to-top-of-window (line)
  "Repositon line point is on to top of window.
With ARG, put point on line ARG."
  (interactive "p")
  (recenter (if (null line)
  	    	0
	      (prefirx-numeric-value line))))

A espedificação interative explica como ler interativamente argumentos.

C-h f interactive	   	  Detalhes sobre "interactive"


# Copyright --------------------------------------------------------- #

2022 Free SOftware Foundation, Inc.
For GNU Emacs version 28
Designed by Stephen Gildea
Translated by Rodrigo Real

Released under the terms of the GNU General Public License version 3 or later

For more Emacs documentation, and the TEX source for this card, see the Emacs
distribution, of https://www.gnu.org/software/emacs

