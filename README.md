# Guia de estudo para a certificação  LPIC-1 V5

Estou criando esse Guia com intuito de organizar as minhas ideias enquanto vou estudando os tópicos referente a LPIC-1

Obs: Irei atualizar esse guia de acordo com o a medida dos topicos que irei estudar.

## O que é LPIC-1? 

LPIC-1 É a primeira certificação profissional Linux multinivek do LPI. O LPIC-1 irá validar a capacidade do candidato para executar tarefas de manutenção na linha de comando com Linux e configurar a rede basica.

### Para se tornar LPIC-1 o candidato deve ser capaz de:

* Compreender a arquitetura de um sistema Linux;
* Instalar e manter uma estação de trabalho Linux, incluindo X11 e configurar-lo como um cliente de rede;
* Trabalhar na linha de comando Linux, incluindo GNU comum e comando Unix;
* Lidar com arquivos e permissões de acesso, bem como a segurança do sistema;
* Executar tarefas de manutenção simples;
* Ajudar os usuarios, adicionar usuários a um sistema mais amplo, backup e restauração, desligamento e reinicialização.

## Divisão do exame

O exame é dividido em duas partes, com 60 questões e 

### LPIC-1: Exame 101-500

* Tópico 101: Arquitetura do Sistema;
* Tópico 102: Instalação do Linux e Gerenciamento de Pacotes;
* Tópico 103: Comandos GNU e Unix;
* Tópico 104: Dispositivos, Sistemas de Arquivos e FHS

### LPIC-1: Exame 102-500

* Tópico 105: Shells e scripts do shell
* Tópico 106: 
* Tópico 107: 
* Tópico 108: 
* Tópico 109: 
* Tópico 110:


# Exame 101-500

## Tópico 103: Comandos GNU e Unix.
OBS: Estou começando a estudar por este topico por ser o mais basico dentre todos os topicos, já que ele ensina comandos de navegação, gerenciamento de arquivos, historicos, filtros, redirecionamento, pesquisa por expressões regulares  e etc.

Abaixo segue os subtopicos da secção 103 e o seu peso na prova, o numero dentro do () significa a quantidade de questões que cai na prova.

* 103.1 Trabalhando na linha de comando(4);
* 103.2 Aplicando filtros a textos e arquivos(2);
* 103.3 Gerenciamento basido de arquivos(4);
* 103.4 Fluxos, Pipes e Redicionamentos(4);
* 103.5 Criar, Monitorar e encerrar processos(4);
* 103.6 Modificar a prioridade de execução de processos(2);
* 103.7 Pesquisar arquivos de texto usando expressões regulares(3);
* 103.8 Edição básica de arquivos(3);
  

### 103.1 Trabalhando na Linha de comando

#### Tipos de shell

* sh - Bourne Shell: É o shell padrão para Unix, ou seja, a matriz dos outros Shells. É representado por "sh". Foi desenvolvido por Stephen Bourne, por isso Bourne shell.
* ksh - Korn Shel: Este shell é o Bourne shell evoluído, portanto todos os comandos que funcionavam no Bourne shell funcionarão neste com a vantagem de ter mais opções. É representado por "ksh"
* csh - C Shell: É o shell mais utilizado em BSD, e possui uma sintaxe muito parecida com a linguagem C. Este tipo de shell já se distancia mais do bourne shell, portanto quem programa para ele terá problemas quanto a portabilidade em outros tipos. É representado por "csh"
* bash - Bourne Again Shell: É o shell desenvolvido para o projeto GNU usado pelo GNU/Linux, é muito usado pois o sistem que o porta evolui e é adotado rapidamente. Possui uma boa portabilidade, pois possui caracteristicas do Korn Shell e C Shell. É representado por "bash".
  
#### echo
Retorna o que é escrito após o comando. 

```
$ echo oi
oi
```
quanto a variaveis do sistema:
```
$ echo $SHELL
/bin/bash
```
podendo até colococar a saida para um arquivo.
```
$ echo "oi" >> teste.txt
```
#### type 
Informa se o comando é interno, esterno ou se é um comando customizado.

```
$ type echo
echo is a shell builtin
```
```
$ type tar
tar is /bin/tar
```
```
$ type clear
clear is hashed (/usr/bin/clear)
```
#### PATH
O PATH serve para indicar para o sistema o caminho dos comandos externos dentro
do Linux. Quando damos o comando abaixo ele nos mostra os diretorios em que os programas e comandos estão localizados.

```
$ echo $PATH
/home/test.rvm/gems/ruby-2.7.0/bin:/home/teste/.rvm/gems/ruby-2.7.0@global/bin:/usr/share/rvm/rubies/ruby-2.7.0/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/usr/share/rvm/bin
```

```
$ echo PATH
/home/lpic1
```
Infomou o diretorio onde estava.

#### ls
Lista os arquivos/diretorios contidos no diretorio

```
$ ls
```

#### Variaveis
Como declarar variavel no Linux

```
$ NOME_VARIAVEL=valor
```
Para retornar o valor contido na variavel
```
$ echo $NOME_VARIAVEL
valor
```
#### export
Serve que os processos filhos consigam ver variaveis(globais), sendo possivel todos os processo filhos criados poderão vê a variavel

```
$ export NOME_VARIAVEL
```

#### set
O comando set irá mostrar todas as variaveis, as locais e as globais declaradas no bash atual

```
$ set
```

#### env
O comando env irá mostar apenas as variaveis globais

```
$ env
```
Outro uso pro env é que, ele pode alterar o valor de uma variavel de forma temporaria
```
$ env TESTE=Windows ./Script_Variavel
```
##### Diferenças entre set e env
o set é um comando de origem bash, já o env é um comando de aplicação externa, por isso ele enxerga somente as variaveis globais

#### unset
Para excluir uma variavel usamos o comando unset

```
$ unset Teste
```

#### Variaveis de ambiente que é importante saber

* HISTFILE=/HOME/lpi1 .bash_history - caminho onde armazena os comandos feitos no terminal.
* HISTFILESIZE=2000 - Tamanho maximo que o arquivo terá.
* HISTSIZE=1000 - Limite maximo de linha(comandos) no arquivo.
* HOME=/home/lpi1 - Mostra o home do usuario atual.
* LOGNAME=lpi1 - Mostra o nome do usuario que fez o login na seção atual.
* PATH= - Mostra todos os caminhos dos programas no sistema.
* PWD=/home/lpi1/Exercicios - Mostra o diretorio atual.
* SHELL - Vai mostrar o tipo atual do shell
* TERM=xterm - Mostra qual terminal estamos usando, no caso estamos usando interface gráfica. Caso optemos por logar sem passar por interface gráfica, aparecerá TERM=tty
* USER=lpi1 - Mostra o nome do usuario atual

Existem algumas variaveis que são definidas dinamicamente pelo SHELL, é importante que conheçamos elas. Elas são identificadas pelo cifrão($) no inicio.

* $ echo $$ - Mostra o PID do processo atual
* $ echo $! - Mostra o PID do ultimo processo que executamos em background
* $ echo $? - Mostra o codigo de saida(exit code) do ultimo processo execultado.
* $ echo ~USUARIO - mosta o /home do usuario, seja ele qual for

### Execução de comandos em sequencia

#### Separador ";"
O ";" é possivel de executar um comando atrás do outro, ele tem uma particularidade que é, independente se o comando está certo ou errado ele é executado.

```
$ clear; date; ls
```

#### &&
ele para a execução se algum dos comandos estiverem errados. Por exemplo: ser o primeiro comando for executado com sucesso ele parte para o segundo comando, caso contraio ele para a execução acusando erro.

```
$ ls /tmp/teste && echo linux
```

#### || (Pipe)
O separador pipe faz o inverso do &&, ele executa o segundo comando caso o primeirto comando falhe, sendo assim, qualquer um dos comandos que tenham sucesso importas pelo || ele encerra a execução.

```
$ ls /tmp/teste || echo linux
```

#### !!
O comando !! repete o ultimo comando executado no bash

```
$ !!
```
#### history
O comando history lista todos os ultimos comandos digitados no bash, cada usuario tem o seu arquivo de historico.
```
$ history
```
Se observamos na listagem dos comandos executados, antes de cada comando existe um numero. Outra forma que podemos executar novamente o comando é da seguinte forma:
```
$ !26
```
Sendo assim ele repitirá o comando 26, conforme a lista do history.
Uma outra forma ainda, é o "!" seguindo da string, por exemplo:
```
$ !uname
```
Dessa forma ele buscará o comando com a string após o "!" e o executará da forma que foi executado pela ultima vez.

#### Como limpar o arquivo de Historico 
Os comandos digitados ficam armazenados no arquivo ".bash_history", estes arquivo é encontrado dentro da pasta do usuario /home/USER
Para limparmos o arquivo de historico da memoria do nosso usuarop executamos o comando:
```
$ history -c
```
OBS:. Quando fazemos o login, o que está no .bash_history é carregado em memoria, e o comando history funciona com o que está na memoria, quando fazemos p lougout é feito um append do que há de novo na memoria para o arquivo .bash_history. Quando usamos o history -c, os comandos do history em memoria é limpo, e quando você faz o logout, é feito um append de nada no .bash_history, ou seja, ele não é alterado.

Então para realizar a limpeza definitivamente há duas opções, forçando que o history em memoria, em branco seja refletido no .bash_history
```
$ history -c && history -w
```
Ou simplesmente limpar manualmente o arquivo.
```
$ history -c
$ cat /dev/null > ~/bash_history
```

#### Pesquisando comandos digitados
No bash temos a possibilidade de buscar comandos que já digitamos anteriormente, para abrir a caixa de pesquisa basta prescionar o "*Ctrl + R*" Este procura os comandos digitados dentro do seu history.

#### Auto Completar.
Essa função se dá quanto digitamos um comando seja ele para arquivos ou diretorios, ele completa o comando quando pressionamos a tecla "*tab*".

### Comandos de ajuda
Um dos recursos muito importantes do shell são os comandos para obter ajuda.

#### man
O comando "man" mostra o manual de ajuda do comando, basicamente todos os comandos tem o seu manual de referencia, e eles são acesados pelo "*man*" exmplo:

```
$ man ls
$ man bash
```
Outra forma de usar o man é com o parametro "-k"
```
$ man -k "system information"
```
Dessa forma o comando traz qualquer referencia que contenha o conteudo "system information" e retorna o comando do conteudo informado.

#### info
É basicamente um "man" de forma reduzida, tando que o "man" quanto o "info" são comandos para buscar ajuda sobre determinados comandos.
```
$ info ls
```

#### "whatsis" e "apropos"
O comando "*whatis*" faz a busca baseado na descrição do comando e traz o comando referente a ela.
```
$ whatis fwupdate
```

O comando "*apropos*" consulta a descrição do comando, assim como o "man -k" faz a pesquisa do comando e traz a sua descrição
```
$ apropos "update system"
```
#### "uname" e seus parametros
O comando "*uname*" imprime na tela informações do sistema. Desde a versão atual do kernel, sua release, sistema operacional e etc. Para entender detelhadamente basta executar o comando:
```
$ uname --help
```

#### alias
Um alias, é uma forma de criar atalho para algum comando, quando digitamos alias no terminal, ele nos mostra alguns que já estão criados:
```
$ alias
```

Para criar um alias de algum comando de forma temporaria, basta digitamos no bash da seguinte forma:
```
$ alias lt='ls /tmp'
```

#### unalias
O comando "*unalias*" pode ser utilizado para remover um "alias" ativo.
```
$ unalias lt
```
#### which
Server para localizar onde está o comando.
```
$ which echo
/usr/bin/echo
```

#### Quoting
O comando a seguir vai executar echo em *(todos os arquivos contidos na pasta)
```
$ echo *
```

Já os comandos a seguir vão fazer que o "*" seja entendido como caractere normal pelo sistema
```
$ echo '*'
$ echo "*"
```
Obs: A "" protege todos os caracteres com exeção do ```$ ` \``` 

O "$" é responsavel por declarar variaveis ou usalas;
O "`" é responsavel por utilizar subcomandos;
A "\" vai proteger apenas o caractere seguinte; 

## 103.2 Aplicando filtros a textos e arquivos.
Enviar arquivos de texto e fluxos de saída através de filtros de utilitário de texto para modificar a saída usando comandos UNIX padrão encontrados no pacote GNU textutils

























