# tmuxinator

gem install tmuxinator - instalação
mux version - mostra a versão

alias mux="tmuxinator" - crie um alias no .bashrc
source ~/.bashrc - atualizar o arquivo .bashrc
export DISABLE_AUTO_TITLE=true - inclua no .bashrc se o nome das janelas não estão sendo exibidos corretamente

mux help - mostra a ajuda

mux new <nome-projeto> - cria um projeto (script)
mux new ~/.config/tmuxinator <nome-projeto> - cria um projeto no local determinado
mux edit <nome-projeto> - editar o script
mux open <nome-projeto> - editar o script
mux <nome-projeto> - executa o script

mux copy [existente] [novo] - copia um projeto existente
mux list - lista todos os projetos
mux delete <nome-projeto> - apaga um projeto

mux implode - remove todas as configurações, aliases e scripts

mux doctor - examina seu ambiente e identifica problemas
mux debug <nome-projeto> - Mostra os comandos do shell que são executados para um projeto
mux debub <nome-projeto> > test.sh - redireciona o debug para ´test.sh

## Exemplo de script .yml

```
# ~/.tmuxinator/monitor.yml

name: nome-projeto
root: ~/

windows:
  - janela-1:
      layout: main-horizontal
      panes:
        - top
        - uptime
        - whoami
  - janela-2:
      layout: tiled
      panes:
        - lsof
        - iostat -w 10
        - netstat
        - vim
  - janela-3:
      layout: main-vertical
      panes:
        - is_my_machine_alive:
          - ping localhost
        - run_several_commands:
          - cd /
          - cd var
          - cd log
          - ls
```
