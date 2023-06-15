# git: comandos

## Glossário
- Staged: fase, preparado, montado, organizado, encenado, por fases, por etapas
- Stash: esconderijo, armazenamento, guardar. Arquiva (ou faz o stash) de alterações que você fez na cópia de trabalho 
durante um determinado período, para que você possa trabalhar em outra coisa, depois voltar e fazer a reaplicação mais tarde. 
O stashing é útil quando você precisa alternar com rapidez o contexto e trabalhar em outra coisa, mas está no meio da alteração de código e 
não está pronto para fazer commit (que fica suspenso para os arquivos em stash).
- `commithash` são os primeiros 7 caracteres do hash do commit que encontramos no `log`
- `origin` é um alias que o Git criou para substituir o URL remoto de um repositório remoto.
 
- Branch: é um ponteiro móvel que leva a um commit:
-- Pode modificar sem alterar o local principal (main)
-- Facilmente "desligável"
-- Múltiplas pessoas trabalhando
-- Evita conflitos

==Observação:== No GitHub para visualizar as modificações: <arquivo>: Edit > Preview.

## Fluxo do GitHub
- Criar um novo branch (ramificação)
- Fazer alterações e adicionar commits
- Abrir uma Pull Request
- Análisar (Review)
- Implantar (Deploy)
- Merge (Mesclar)

## Ciclo de vída dos status dos arquivos
1. Untracked: `git status`: inserido no repositório porém não monitorados.
2. Staged: `git add`: inicia o monitoramento, inserindo em Staged, e aguarda `git commit -m` 
   (que gera um snapshot com hash, ou seja, gera uma versão); após `git commit -m` é classificado como "unmodified". 
3. Unmodified: `git status`: sem modificação desde a última versão criada (com `git add`, `git commit -m`). 
4. Modified: modificado, aguarda `git add` para retornar ao Staged.

## Ajuda do Git
Se estiver tendo problemas para lembrar comandos ou opções de comandos, você pode usar o Git help.

Existem algumas maneiras diferentes de usar o comando help na linha de comando:
`git <comando> -help` ou `--help` (extensivo): Veja todas as opções disponíveis para o comando específico
`git help --all`: Veja todos os comandos possíveis numa lista longa

## Configuração
Use global para definir o nome de usuário e o e-mail para cada repositório em seu computador.

Remova `global`se você deseja definir o nome de usuário/e-mail apenas para o repositório atual.

Alterações são gravadas em `~/.gitconfig`
```
git config --global user.name "pi"
git config --global user.email "pi@raspberrypi"
git config --global core.editor nano
```

## Mostra a configuração
```
git config user.name
git config user.email
git config --list
```
## Iniciando o repositório
`git init`

## Básico
`git status`: o estado dos arquivos
`git status --short`: ver as alterações de forma compacta

Nota: Os sinalizadores de status curtos para a `git status --short` são:

?? - Arquivos não rastreados (Untracked)
A - Arquivos adicionados ao palco (Stage) 
M - Arquivos modificados (Modified)
D - Arquivos excluídos (Deleted)

`git add`: adiciona um arquivo para ser monitorado
`git add .`, `git add -A` ou `git add -all`: adiciona todos os arquivos para serem monitorados
`git commit -a -m "<comentario>"`: para arquivos em Modified, adiciona para Staged e faz o commmit
`git commit -m ",comentario>"`: faz um commit do arquivo (snapshot)

### commit --ammend 
`commit --amend`: é usado para modificar o arquivo `commit`.

Ele combina as mudanças no `staging environment` com o mais recente `commit` e cria um novo arquivo `commit`.
Este novo `commit` substitui `commit` inteiramente o mais recente.

## Log
`git log`
`git log --decorate`: mais detalhado
`git log --graph`: em forma gráfica o que acontece com os branchs e versões
`git log author="<pi>"`: filtra todos os logs do autor "pi"
`git shortlog`: em ordem alfabética, quais os autores, quais e quantos os commits
`git shortlog -sm`: quantidade de commit por pessoa
`git show <hash>`: mostra as alterações sofridas pela hash

## Diferenças entre versões
`git diff`: mostra as mudanças antes de um commit (use antes de fazer um commit)
`git diff --name-only`: mostra somente o nome do arquivo que foi modificado

## Desfazer 
### checkout
`git checkout <hash>`: antes de `git add` desfaz a edição (permanece em Unmodified)

### Revert
Usamos quando queremos pegar um `commit` anterior e adicioná-lo como um novo `commit`, mantendo o `log` intacto.

`git revert <commithash>`: reverte as mudanças mas mantêm o comite revertido (anterior)

1. `log --oneline` para localizar o `commit` que desejamos reverter
2. `git revert HEAD --no-edit`: reverter a última alteração e fazer o commit
2.2 opção `--no-edit`: ignora o editor de mensagens do commit
3. `log --oneline`: para confirmar a reversão

==Observação:== 
`git revert HEAD~x`: para reverter para comits anteriores (x é número = volta 1, volta 2, etc)

### Reset
Usamos quando queremos mover o repositório de volta para um commit anterior, descartando qualquer alteração feita depois desse commit.

Mesmo que os commits não estejam mais aparecendo no `log` (registro), eles não foram removidos do Git.
Se você souber o `hash` do commit, poderá desfazê-lo

`git reset <commithash>`: reverte para o commit indicado pelo `commithash`

`git reset HEAD <commithash>`: depois de `git add`, remove de Staged sem desfazer a modificação (retorna para  Modified)
`git reset --soft <commithash>`: depois de `git commit`, desfaz apenas o commit (permanece em Staged aguardando commit)
`git reset --mixed <commithash>`: depois de `git commit`, remove do Staged desfazendo `git add` e commit (portanto retorna para Modified)
`git reset --hard <commithash>`: desfaz tudo o que foi feito depois da hash indicada (altera o histórico do commit)

## Repositório remoto
>OBS: [Gerando uma nova chave SSH e adicionando-a ao agente SSH](https://is.gd/54VUmt)
>Origin: nome default para a origem do remoto. Pode ser alterado

### Adicionar repositório remoto ao repositório local
`git remote add origin git@github.com:estanislau/manual.git` 

`git remote`: mostra os remotes cadastrados
`git remote -v`: mostra o endereço dos remotes cadastrados

`git push --set-upstream origin master`: envia nossa ramificação master para a url origin e define-a como a branch remota padrão

### Clone de repositório remoto
A clone é uma cópia completa de um repositório, incluindo todos os logs e versões de arquivos

`git clone git@github.com:estanislau/tmp.git <nome-local>`: se deseja alterar o nome inclua <nome-local>, que é opcional

### Fork no GitHub
1. Acesse a página que deseja o fork em GitHub: clique em Fork

### Clone de Fork
1. Acesse o repositório do qual desejamos o fork
2. Clique em "Code" e copie o SSH. 
3. No terminal: `git clone git@github.com:w3schools-test/w3schools-test.github.io.git`
4. Confirme a pasta do repositório clonado com `ls` e acesse-a com `cd`
5. Confirme as condições com `git status`
6. Confirme os registros com `log`
7. Confirme os remotes com `git remote -v`
8. Renomeie o original `origin remote` para `upstream` com `git remote rename origin upstream`
9. Confirme a alteração com `git remote -v`
10. Em GitHub busque a URL do nosso próprio fork
11. Adicione como `origin`. Ex.: `git remote add origin git@github.com:estanislau/w3schools-test.github.io.git`

Agora temos dois repositórios remotos:

- `origin`: nosso próprio fork, onde temos acesso de leitura e gravação
- `upstream`: o original, onde temos acesso somente para leitura

==Observação:== 
- Para especificar uma pasta específica para clonar, adicione o nome da pasta após o repositório URL:
`git clone https://github.com/<nome-pagina>/<nome-repo>.git <nome-folder>`
- De acordo com as convenções de nomenclatura do Git, é recomendável nomear seu próprio repositório como `origin` e aquele para o qual você fez o fork como `upstream`

12. Acesse a pasta e confirme a condição com `git status`
13. Confirme se temos todos os registros com `git log`

### Enviar mudanças para o GitHub Fork
1. Commit as mudanças
2. Envie as mudanças com `git push origin`
3. GitHub: confirme o novo commit e envie um Pull Request

## Branch
É uma versão nova/separada do repositório principal (main)

`git fetch -p`: sincroniza a lista de branches 

A flag `-p` significa "prune" (remover). Depois de fazer o fetch, os branches 
que já não existem mais remotamente serão excluídos.

`git branch`: mostra todas as ramificações locais.
`git branch -r`: mostra todas as ramificações remotas.
`git branch -a`: mostra todas as ramificações locais e remotas (recomendado efetuar um "git pull" antes).

==Observação:== se <nome-branch> estiver apenas remota, no próximo `git pull` ela será puxada mas só poderemos visualizá-la localmente após `git checkout <branch-remota)`

### Indicando o branch principal
`git branch -M main`

### Branch: trabalhando com branches
1. Criamos um outro branch (secundário) para trabalhar localmente 
2. Posteriormente unimos com o principal (main, master)
3. Excluimos o branch secundário com `git branch -d <nome-branch>

`git branch`: lista os branchs existentes e sinaliza o ativo (na cor verde)
`git checkout <nome-branch>`: alterna para o branch indicado para o local.
`git checkout -b <nome-branch>`: Criar um branch. Usar opção `-b` em `checkout` criará uma nova ramificação e moverá para ela, se ela não existir

### Branch: excluir um branch
- A opção `-d` excluirá o branch somente se você já fez o `push` e o `merge` com o branch remoto. 
- Use a opção `-D` se quiser forçar a exclusão do branch, mesmo que você ainda não tenha feito o `push` e o `merge` com ele.

`git branch -d <nome-branch>`: apaga o branch <nome-branch> Geralmente utilizado quando (merge) mesclamos o branch secundário ao principal 

`git push origin --delete <nome-branch>`: apaga o branch remoto
`git push <remote> :<branch>`: um comando menor para excluir um branch remotamente

### Branch: unindo com merge
- Pró:
-- Operação não destrutiva
-- Indicado quando inserindo new feature
- Contra:
-- Commit extra
-- Histórico poluído

`git merge <nome-branch>`: Une dois branches

### Branch: conflitos após merge
Use `git status` para mais detalhes sobre o conflito. Abra o arquivo com o editor e procure pela linha iniciada com `<<<<<<< HEAD` e edite o arquivo para resolver o conflito.

### Branch: unindo com rebase
- Pró
-- Evita commits extras
-- Histórico linear
-- Indicado para o dia a dia
- Contra
-- Perde ordem cronológica

## Atualizando o repositório local 
É assim que você mantém seu Git local atualizado a partir de um repositório remoto:

### Fetch
`fetch` obtém todo o histórico de alterações de um branch/repositório rastreado. 

==Observação:== Use `git pull` se você quiser apenas atualizar seu repositório local, 
sem passar por todas essas etapas.

Esses são os passos que devemos fazer:

`git fetch origin`: atualiza para ver o que mudou no GitHub
`git status`: confirmamos por quantos commits estamos atrás de `origin/master` 
`git log origin/master`: confirmamos o que foi alterado 
`git diff origin/master`:  mostra as diferenças entre nosso `master` local e `origin/master`

`git merge origin/master` podemos mesclar nossa ramificação atual `master` com `origin/master`
`git status`: novamente para confirmar se estamos atualizados.

### Pull
É uma combinação de dois comandos diferentes: `fetch` e `merge`.

`git pull origin`: atualiza o nosso git local a partir do remoto, "puxando-o".

### Push
`git push origin`: empurrando as alterações para a nossa origem remota
`git push origin <local-branch>`: envia uma branch do repositório local para o repositório GitHub
`git push -u origin main`: publicando no branch principal (main) do repositório remoto 

## Stash
`git stash`: arquiva as alterações que você fez na cópia de trabalho durante um determinado período, para que você possa trabalhar em outra coisa 
`git stash apply`: aplicar mais uma vez as alterações à cópia de trabalho e manter no stash 
`git stash list`: lista todos os `stash`
`git stash clear`: exclui todos os `stash`, portanto perde as alterações efetuadas nos arquivos em stash

## Alias (atalhos)
`git config --global alias.<alias> <comando>`: ex.: `git config --global alias.s status`

## Tags
`git tag -a <tag> -m <mensagem-tag>`: cria uma tag
`git tag`: lista as tags
`git push <origin> <nome-tag>`: envia para GitHub as tags
`git tag -d <nome-tag>`: apaga a tag local
`git push <origin> :<nome-tag>`: apaga a tag remota

## Gitignore
O Git pode especificar quais arquivos ou partes do seu projeto devem ser ignorados pelo Git usando um arquivo `.gitignore`.

Neste caso, usamos um único `.gitignore` que se aplica a todo o repositório.
Também é possível ter arquivos `.gitignore` adicionais em subdiretórios. Eles se aplicam apenas a arquivos ou pastas dentro desse diretório.

### Regras locais e pessoais para ignorar Git
Também é possível ignorar arquivos ou pastas, mas não mostrá-los no arquivo `.gitignore` distribuído.

Esses tipos de ignorados são especificados no arquivo `.git/info/exclude` . Funciona da mesma forma que `.gitignore`, mas não é exibido a mais ninguém.

## Páginas GitHub
1. GitHub: crie um repositório de página GitHub como: `<username>.github.io`
2. `git remote add <nome-repo> git@gitbub.com:estanislau/estanislau.github.io.git`: envia o repositório local para as páginas do GitHub
3. `git push <nome-repo> master`: envia o branch local para o novo remote
4. GitHub: Repositório > Settings > Pages > Visit Site

## SSH
Se você usa `SSH`, não precisa adicionar nome de usuário e senha a cada vez, ao contrário do `HTTPS`.

`ssh -T <email@cadastrado>`: teste de acesso SSH

### Alterar o Remote de HTTPS para SSH
```
$ git remoto -v
origem http://github.com/{USERNAME}/{PROJECTNAME}.git (fetch)
origem http://github.com/{USERNAME}/{PROJECTNAME}.git (push)
```

Você pode alterar `HTTPS` para `SSH` usando o seguinte comando :
```
$ git remote set-url origin git@github.com:{USERNAME}/{PROJECTNAME}.git
```

## Erros
1. 
```
fatal: The current branch teste has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin teste
```

2.
`error: failed to push some refs to [remote repo] error`
Esse erro ocorre principalmente quando você tenta enviar as alterações locais ao GitHub enquanto o repositório local (repo) ainda não foi atualizado com as alterações feitas no repo remoto.

Portanto, o Git está tentando pedir para você atualizar o repo local com as alterações atuais no controle remoto antes de pressionar suas próprias alterações. Isso é necessário para que você não substitua as alterações feitas por outras pessoas.

git pull origin main git push -u origin main

`fatal: refusing to merge unrelated histories`
git pull --rebase origin main
git push -u origin main

Informa que não há um branch remoto chamado "teste" e indica o comando para a sua criação.
