#GitBasico
Este repositório terá alguns comandos básicos do git, apenas para possíveis consultas. :smile:  

##Instalação
Para iniciar a utilização do git, vamos primeiro instalá-lo. Escolha o seu Sistema Operacional abaixo e siga as intruções.

###Distribuições Linux
Via terminal, apenas atualize sua lista de pacotes e em seguida execute a instalação:
```
sudo apt-get update
sudo apt-get install git
```
Para verificar se a instalação foi bem sucedida:
```
git --version
```
O resultado deve ser algo como:
```
git version 2.x.x
```

###Windows
Acesse o [git-for-windows] e faça o download.  
Após o download, execute e instale com as opções padrão.  
Se tudo correu bem, agora você tem o **git bash** em seu computador.

##Começando Utilizar o Git
Se você está no Linux, tudo será feito via **terminal**. Já no windows você deve utilizar o **git bash**.
###Novo Repositório  
Primeiro, através do git bash ou do terminal, navegue até a pasta do projeto que você quer tornar um repositório.
Caso você ainda não tenha nenhum projeto, apenas crie uma pasta e navegue até ela.  
Já dentro da pasta do seu projeto, inicialize seu repositório, para isso:
```
git init
```
O resultado deve ser algo semelhante a isso:
```
Initialized empty Git repository in C:/umDiretorioQualquer/seuProjeto/.git/
```
Com esse comando, nós acabamos de iniciar um novo repositório.

###Status  
No git nós temos dois estados básicos para um arquivo:
+ Working Directory
   Arquivos que ainda estão sendo editados. São exbibidos na cor vermelha.
+ Staging Area
   Arquivos que já foram editados, mas estão aguardando um commit. São exibidos na cor verde.

Para verificar nossos arquivos, utilize:
```
git status
```

###Stage Area  
Se você já editou seu arquivo e quer adicioná-lo ao Stage Area para futuramente incluir ele em um commit, execute:
```
git add meuarquivo.java
```
Agora seu arquivo está no Stage e está pronto para receber commit.

###Fazer um Commit
Você só pode fazer commit de arquivos que estão no Stage Area.  
Para fazer o commit de um arquivo, esse é o comando:
```
git commit meuarquivo.java -m "Minha mensagem"
```
Pronto, seu primeiro commit foi feito!  
Para verificar seus commits, utilize o comando:
```
git log
```
O comando vai retornar uma lista com seus commits. Nessa lista vai conter o autor, a data e a mensagem que você colocou.

[git-for-windows]: https://git-for-windows.github.io/