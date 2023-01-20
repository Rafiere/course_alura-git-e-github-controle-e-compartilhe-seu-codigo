# AULA 01 - O QUE É GIT

O Git é um **sistema de controle de versões**.

Ele permite que os desenvolvedores que estão em um projeto consigam versionar o código entre eles mesmos, gerando um histórico das diferentes versões da aplicação.

Existem vários sistemas de controle de versão, como o `CVS`, o `SVN`, o `Mercurial` e o `Git`, porém, dentre eles, o Git é o mais recomendado.

## INSTALANDO O GIT

Basta acessarmos o site do [Git](git-scm.com/download) e realizarmos o download.

O Git Bash fornece comandos do Linux no Windows, assim, a utilização dele é muito recomendada.

O comando `git --version` exibe a versão do Git que estamos utilizando.

## INICIALIZANDO O GIT

O comando `git init` permite que o Git inicialize um repositório. Ao utilizarmos esse comando, o Git cria a pasta `.git`.

## MAIN VS MASTER

Desde o final de 2020, não é mais utilizado o termo `master` para se referir ao repositório principal, e sim o termo `main`. Essa nomenclatura é mais inclusiva.

## CONFIGURAR O USUÁRIO DO GIT

Podemos configurar o nome e o email do Git que será utilizado no repositório local. Para isso, devemos utilizar os comandos `git config --local user.name "nome"` e `git config --local user.email "email"`.

# AULA 02 - INICIANDO OS TRABALHOS

Para o Git monitorar um determinado arquivo, devemos utilizar o comando `git add nome-do-arquivo`.

Um `commit` é um determinado momento do código que foi salvo, assim, se necessário, podemos voltar esse código para os commits anteriores.

Para criarmos um commit, devemos utilizar o comando `git commit -m "feat: Criando o arquivo index.html com listas de curso."`

Com o comando `git log`, podemos ter acesso à diversas informações dos commits do projeto.

O `HEAD` é o local onde estamos no código. Todas as alterações realizadas serão feitas no `HEAD`.

O comando `git config` permite a definição de configurações do Git. As configurações com o `--local` serão efetuadas apenas no projeto atual, enquanto que as configurações com o `--global` serão realizadas globalmente, em **todos os projetos**.
