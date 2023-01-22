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

O comando `git log --oneline` exibe cada commit em **uma única linha**.

## IGNORANDO ARQUIVOS

Para que o Git ignore um determinado arquivo, devemos criar o arquivo `.gitignore`. O Git lerá esse arquivo e **ignorará todos os nomes dos arquivos que estiverem nas linhas desse arquivo**, por exemplo:

```
node_modules
```

No exemplo acima, estamos adicionando a pasta `node_modules` no arquivo `.gitignore`, assim, o Git não versionará essa pasta.

# AULA 03 - COMPARTILHANDO O TRABALHO

Para criarmos um repositório que só contém as alterações dos arquivos, e não a cópia física deles, podemos utilizar o comando `git init --bare`. Com isso, podemos adicionar esse repositório como um repositório remoto em outro. O repositório que foi criado com o comando `git init --bare` não possui a `working tree`, ou seja, não conterá uma cópia dos arquivos. Ele é utilizado para **pouparmos espaço de armazenamento**.

Se utilizarmos o comando `git remote`, serão listados **todos os repositórios remotos que o repositório local, atual, conhece**.

Se utilizarmos o comando `git remote add nome-do-repositorio-remoto endereco-do-repositorio-remoto`, adicionaremos esse repositório remoto ao repositório local.

Se utilizarmos o comando `git remote -v`, teremos acesso ao endereço dos repositórios remotos. Nesse comando, temos o `fetch`, que é o repositório remoto onde o Git vai **puxar os dados**, e o `push`, que é o repositório remoto onde o Git vai **enviar os dados**.

## CLONANDO UM REPOSITÓRIO

Para obtermos todos os dados de um repositório remoto em nosso repositório local, podemos utilizar o comando `git clone endereco-do-repositorio-remoto-que-sera-clonado-localmente nome-do-diretorio`.

## SINCRONIZANDO OS DADOS

Para enviarmos as alterações do repositório local para o repositório remoto, podemos utilizar o comando `git push repositorio-remoto-em-que-enviaremos-as-alteracoes branch-remoto-em-que-enviaremos-as-alteracoes`, assim, enviaremos os dados locais para o repositório remoto.

Para obtermos as alterações que estão na nuvem para o repositório local, podemos utilizar o comando `git pull nome-do-repositorio-remoto-em-que-os-dados-serao-puxados nome-da-branch-remota`.

Se utilizarmos o comando `git remote rename nome-remoto-antigo nome-remoto-novo`, podemos renomear o servidor remoto que temos acesso.

## GITHUB

O [GitHub](https://github.com) é um site para compartilharmos os nossos repositórios remotamente.

Podemos criar um repositório remoto no GitHub. Para adicionarmos esse repositório remoto, que foi criado, como um repositório local, podemos utilizar o comando `git remote add origin endereco-do-repositorio-remoto`.

O comando `git push -u nome-do-repositorio-remoto-que-enviaremos-as-alteracoes nome-da-branch-local-que-as-alteracoes-serao-enviadas` permite que, por causa do parâmetro `-u`, sempre que digitarmos `git push` e estivermos na `master`, vamos mandar para o `origin`.

# AULA 04 - TRABALHANDO EM EQUIPE

## BRANCHES

As `branches` são galhos, assim, podemos fazer uma ramificação de um código para trabalharmos com o Git.

O comando `git branch` exibe as `branches` locais.

Podemos utilizar o comando `git branch titulo`, assim, criaremos a branch `titulo`.

Para mudarmos de `branch`, podemos utilizar o comando `git checkout nome-da-branch`.

A ferramenta [Visualizing Git](https://git-school.github.io/visualizing-git) serve para visualizarmos, de forma lúdica, o comportamento do Git.

Se estivermos na branch `titulo` e quisermos mover o código da branch `titulo` para a branch `master`, podemos, dentro da branch `master`, utilizar o comando `git merge titulo`, assim, o código da branch `titulo` será enviado para a branch `master`, assim, será realizado um `commit` de `merge` na branch `master`.

## GIT REBASE

Se estivermos na branch `master` e quisermos pegar o código que está na branch `titulo` e inserir na branch `master`, ou seja, atualizar o código da branch `master` com o código da branch `titulo` sem criarmos um commit de `merge`, podemos utilizar o comando `git rebase titulo`, assim, o Git trará todos os commits da branch `titulo` para a branch `master`, e, depois disso, adicionará o commit da branch `master` na frente dos commits da branch `titulo`.

![[Pasted image 20230121095921.png]]

Na imagem acima, podemos visualizar os comandos e os fluxos.

Basicamente, o comando `git rebase branch-que-tera-o-codigo-movido-para-antes-do-codigo-da-branch-atual` inserirá o commit da branch que foi passada como argumento para o comando `git rebase` antes do commit que foi realizado na branch `master`.

Em suma, o comando `git rebase` atualiza a branch atual, mas mantém o trabalho dela como o **último trabalho que foi feito**.

## DIFERENÇA ENTRE GIT REBASE E GIT MERGE

O comando `git merge` junta os trabalhos e gera um `merge commit`. O comando `git rebase` **aplica os commits de outra branch na branch atual**.

## RESOLVENDO CONFLITOS

Se tentarmos realizar um `merge` em uma linha de um arquivo que foi alterada por duas pessoas diferentes, teremos um conflito de `merge`.

Se estivermos na branch `master` e utilizarmos o comando `git merge lista`, sendo que tanto na branch `master` como na branch `lista`, a mesma linha foi modificada, teremos um erro de `merge`.

Se abrirmos o VSCode após esse erro de `merge`, o código abaixo será gerado

```
<<<<<< HEAD
	<li>Docker: Criando containers sem dor de cabeça</li>
======
	<li>Testando</li>
>>>>>>
```

Entre o `HEAD` e o `======`, temos os dados que estão no **commit atual**, ou seja, que estão na branch `master`. Entre o `======` e o `>>>>>>`, temos os dados que queremos trazer da branch `lista` para a branch `master`.

Para resolvermos esse conflito, precisamos **remover as informações que não queremos, deixando apenas uma única versão**.

Dessa forma, se quisermos apenas a linha `<li>Docker: Criando containers sem dor de cabeça</li>`, devemos **apagar** a linha `<li>Testando</li>`, por exemplo:

```
	<li>Docker: Criando containers sem dor de cabeça</li>
```

Após isso, basta utilizarmos o comando `git add index.html` e realizarmos o commit de `merge`, através do comando `git commit`.

# AULA 05 - MANIPULANDO AS VERSÕES

## REVERTENDO ALTERAÇÕES

Para desfazermos uma modificação em um arquivo que ainda não foi commitado, podemos utilizar o comando `git checkout -- index.html`.

Para desfazermos uma alteração que já foi marcada para ser commitada, ou seja, que já sofreu o comando `git add`, podemos utilizar o comando `git reset HEAD nome-do-arquivo`, assim, o arquivo voltará para o `HEAD`, ou seja, para o status de trabalho. As alterações nesse arquivo não serão perdidas, mas o arquivo será retirado da área em que o `git add` o colocou. Após isso, para excluirmos as modificações desse arquivo, podemos utilizar o comando anterior, que é o `git checkout -- nome-do-arquivo`.

Para **desfazermos um commit que já foi realizado**, podemos utilizar o comando `git revert hash-do-commit-que-queremos-desfazer`, assim, será criado um novo commit revertendo as alterações do commit que teve o hash definido.

## GUARDANDO PARA DEPOIS

Para guardarmos uma modificação para depois, sem precisarmos realizar o commit dela, podemos utilizar o comando `git stash`, dessa forma, salvaremos os dados que foram alterados.

Podemos utilizar o comando `git stash list` para listarmos todas as modificações que foram salvas através do comando `git stash`.

Podemos utilizar o comando `git stash apply numero-da-stash`, assim, aplicaremos as modificações que estão na `stash` na branch atual. O `numero-da-stash` é o valor que aparece quando utilizamos o comando `git stash list`.

Se utilizarmos o comando `git stash apply numero-da-stash`, as mudanças serão aplicadas, porém, a stash **não será removida**, dessa forma, teríamos que utilizar o comando `git stash drop numero-da-stash`.

Para aplicarmos e removermos o `stash`, devemos utilizar o comando `git stash pop numero-da-stash`.

## VIAJANDO NO TEMPO

Podemos utilizar o comando `git checkout hash-do-commit` para modificarmos o código atual até o código do commit específico. Ao fazermos isso, estaremos no estado `detached HEAD`, assim, tudo o que commitarmos aqui, será **ignorado**. Para conseguirmos fazer as alterações, devemos criar uma `branch` nesse `commit` em que voltamos, e, dessa forma, realizarmos as alterações e os commits desejados.

# AULA 06 - GERANDO ENTREGAS

## VISUALIZANDO DIFERENÇAS

Podemos utilizar o comando `git diff hash-do-primeiro-commit..hash-do-segundo-commit` para visualizarmos as alterações do **primeiro até o segundo commit**. O símbolo `..` representa o **"até"**.

O comando `git diff` exibe as modificações no arquivo atual que **ainda não foram adicionadas para serem commitadas**.

## TAGS E RELEASES

Uma `tag` no Git marca um **ponto fixo na aplicação**, ou seja, é um ponto que **não pode ser modificado**. Podemos acessar esse ponto fixo e ter a **certeza** que o código estará no estado em que essa tag representa.

Podemos utilizar o comando `git tag -a v0.1.0 "Lançando a primeira versão (BETA) da aplicação de cursos."`, dessa forma, criaremos uma versão específica para essa aplicação.

Podemos enviar a versão que uma `tag` representa, para o servidor, através do comando `git push nome-da-branch-remota nome-da-tag`.

É possível visualizarmos as tags no GitHub, também.

Ao criarmos uma `tag`, teremos criado uma `release`, assim, qualquer pessoa poderá baixar o projeto nessa `release` e utilizar ele no formato em que ele foi definido quando a `tag` foi atribuída para ele.
