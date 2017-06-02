# GitBasico
Este repositório terá alguns comandos básicos do git, apenas para possíveis consultas. :smile:  

## Instalação
Para iniciar a utilização do git, vamos primeiro instalá-lo. Escolha o seu Sistema Operacional abaixo e siga as intruções.

### Distribuições Linux
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

### Windows
Acesse o [git-for-windows] e faça o download.  
Após o download, execute e instale com as opções padrão.  
Se tudo correu bem, agora você tem o **git bash** em seu computador.

## Começando Utilizar o Git
Se você está no Linux, tudo será feito via **terminal**. Já no windows você deve utilizar o **git bash**.
### Novo Repositório  
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

### Configurar Usuário
Para configurar um usuário global para seus repositórios:
```
git config --global user.name "usernameGithub"
git config --global user.email "email.github@email.com"
```
Recomendo utilizar o mesmo username e email que está na sua conta do github, ou seus commits não serão atrelados ao seu perfil.  

Para colocar um usuário e email somente em um repositório específico, faça isso dentro dele:
```
git config user.name "usernameGithub"
git config user.email "email.github@email.com"
```
Pronto, seu usuário já está configurado.  
Caso queira ver qual usuário está configurado em seu projeto, execute:
```
git config user.name
git config user.email
```

### Configurar PROXY
Para configurar a utilização de um proxy insira:  
```
git config --global http.proxy http://proxyuser:proxypwd@proxy.server.com:8080
```
- Mude o 'proxyuser' para seu usuário de proxy
- Mude o 'proxypwd' para a sua senha de proxy
- Mude o 'proxypwd@proxy.server.com' para a URL do proxy
- Mude o '8080' para a porta do proxy

**Atenção!** Essa configuração utiliza URL Enconding, se sua senha possui caracteres especiais (!, $, #) você deve inserir a URL
Encoding referente a eles. 

Para verificar as atuais configurações de proxy, insira: 
```
git config --global --get http.proxy
```
Caso queira zerar as configurações de proxy ~~parar de ser espionado~~:
```
git config --global --unset http.proxy
```

### Status  
No git nós temos dois estados básicos para um arquivo:
+ **Working Directory** - Arquivos que ainda estão sendo editados. São exbibidos na cor vermelha.
+ **Staging Area** - Arquivos que já foram editados, mas estão aguardando um commit. São exibidos na cor verde.

Para verificar seus arquivos, utilize:
```
git status
```

### Stage Area  
Se você já editou seu arquivo e quer adicioná-lo ao Stage Area para futuramente incluir ele em um commit, execute:
```
git add meuarquivo.java
```
Caso queira adicionar todos os arquivos de uma só vez, execute:
```
git add --all
```

Agora seu arquivo está no Stage e está pronto para receber commit.

### Fazer um Commit
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
O comando vai retornar uma lista com seus commits. Essa lista vai conter o autor, a data e a mensagem que você colocou.  

### Desfazer Último Commit
Para desfazer o último commit que ainda não recebeu push, você pode optar por uma das duas opções:
```
git reset HEAD~1 --hard

git reset HEAD~1 --soft
```
No **hard** suas alterações são todas descartadas, enquanto que no **soft** os arquivos apenas voltam para o stage area.

Para desfazer o último commit que já recebeu push:
```
git revert HEAD~1
```
### Git e GitHub  
Crie em seu github um repositório com o mesmo nome da pasta de seu projeto.  
Feito isso, para vincular o projeto local e o remoto:
```
git remote add origin https://github.com/seuUsuarioGitHUB/seurepositorio.git
```
Agora seu repositório local já sabe que existe um repositório remoto pra onde ele pode enviar as mudanças.  

Se você quer subir seus commits para o repositório remoto, faça:
```
git push origin master
```
Após isso, o terminal ou gitbash irá pedir seu usuário e senha do github. Se ambos estiverem corretos, o push será feito
e o repositório remoto atualizado.

### Atualizar seu Repositório Local
Para atualizar o reposósitório local em relação ao remoto:
```
git pull
```
Após isso, seu repositório será atualizado.

# Trabalhando com Branch
Branch são ramos que você pode criar dentro do seu repositório, por padão o git cria um repositório chamado "master" onde fica os seus arquivos.

## Como trabalhar com Branch?
Em projetos o padão é criar um Branch para cada nova funcionalidade que será desenvolvida no sistema. Por exemplo, você está criando uma aplicação Web e vai começar a desenvolver um sistema de Login, vamos começar criando um novo branch.
```
git branch sistemaLogin
git checkout sistemaLogin
```
O primeiro comando vai criar um novo ramo que é uma cópia do branch principal (master) e vamos chamar de "sistemaLogin", e no comanto seguinte vamos mudar para o branch que acabamos de criar.

A partir desse momento você pode trabalhar normalmente no seu projeto que não ira atrapalhar o desenvolvimento de outros ramos do projeto. Porem o branch foi criado localmente e está disponivel apenas para você, caso queira disponibilizar o branch para sua equipe de desenvolvimento, execute:
```
git push origin sistemaLogin
```
O comando acima vai criar o branch no repositório remoto, e disponivel para que outros membros da equipe trabalhem nele.

Após desenvolver a nova funcionalidade é necessario atualizar o branch principal com as novas modificações, então vamos lá.
```
git checkout master
git merge sistemaLogin
```
Para mesclar a nova funcionalidade para o "master", precisamos retornar para o branch principal e fazer o "merge" com o branch "sistemaLogin".

Depois de atualizar o branch master você pode deletar o branch em que estava sendo desenvolvido a funcionalidade antiga, para isso basta executar:
```
git branch -d sistemaLogin
```
O comando acima deleta o branch local, caso queira deletar um branch remoto, execute:
```
git push origin :sistemaLogin
```
----
Mais conteúdo:  
http://schacon.github.io/git/git.html  
https://git-scm.com/book/pt-br/v1

[git-for-windows]: https://git-for-windows.github.io/