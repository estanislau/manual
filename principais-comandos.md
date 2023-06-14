# Principais comandos

## tmux
### Copiar e colar no buffer
C-b [                                   Entre no modo de cópia
Barra espaço                            Entra no modo seleção
Setas                                   Movimenta para selecionar
Enter                                   Copia para o buffer
C-b ]                                   Cola o buffer mais recente
q					Sai do modo cópia

### Gerenciador de clipboard
C-b =                                   Menu com todas as cópias
C-b #                                   Mostra todas as cópias
<numero>                                Retorna e cola a escolha (funciona com Enter)

## Bash
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


