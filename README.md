# Introdução ao Git e ao Controle de Versão

Este tutorial é voltado para os alunos de cursos na [Founders & Coders](http://foundersandcoders.org/). Feedback or Suggestions in the format of an issue or contributions as a pull request are appreciated.

Comentários ou sugestões, no formato de Issue ou contribuições em forma de Pull Request são bem-vindos.

Como estudante, se você ficar preso em qualquer ponto, por favor, abra uma Issue e eu vou tentar voltar para você o mais rapidamente possível. Se você preferir, sinta-se livre para contactar-me em Gitter. Quando a Issue for resolvida, faça uma Pull Request para o projeto.

A introdução ao Git visa a primeira semana do período integral do curso Founders & Coders, ou para quem está começando com git. A expectativa é que esta introdução ensine o que você precisa saber para começar a colaborar em código com os seus companheiros de time.

Git for Collaboration visa os alunos do segundo semana do curso, ou aqueles que têm dominado a primeira seção. Mesmo que a maioria do conselho neste tutorial vai demorar um pouco para digerir - e na prática é essencial. Uma boa meta é compreender todos estes conceitos, e implementar, pelo menos, a maioria dessas dicas em seus projetos de colaboração antes de terminar o seu tempo como estudante de Founders & Coders.


# Conteúdo
#### [Introdução](#introduction)
1. [Precisamos saber as terminologias](#terminology)
2. [Por que Controle de Versão?](#version-control)
3. [Tutorial](#tutorial)
	* [Começando](#getting-started)
	* [Ramificando (Branch)](#branching)
	* [Fazendo Mudanças](#changes)
	* [Mesclando com Master](#merging)
	* [Mesclando Conflitos](#conflicts)
	* [Mudando a Estrutura do Arquivo](#changing-file-structure)
4. [Iniciando com Github Flow](#github-flow)

#### [Git for Collaboration](#git-collaboration)
1. [Mais algumas terminologias](#further-terminology)
2. [A Linha do Tempo](#timeline)
3. [Commitando](#commits)
    * [Quando você precisa usar o commit](#when-commit)
    * [Commitando Mensagens](#commit-message)
    * [Mesclando commits](#merging-commits)

#### [Resources](#resources)



<a id="introduction" name="introduction"></a>
# Introdução

A introdução ao Git é voltada a primeira semana do período integral do curso Fundadores & Codificadores, ou para quem está começando com o git. Espero que esta introdução cubra tudo o que você precisa saber para começar a colaborar com o código dos seus companheiros do time.

<a id="terminology" name="terminology"></a>
## Terminologia

##### *Repositório (repo)*
Simplesmente coloque-o na pasta do seu projeto. Esse repositório pode ser localizado localmente (nos seus arquivos do sistema no seu computador), ou remotamente(no Github). De qualquer forma, é o mesmo repositório.

##### *Controle de Versão*
Nós usaremos o Git para isso. É uma maneira de observar as mudanças no código o que possibilita trabalhar com multiplos desenvolvedores no mesmo repositório.

##### *Git*
Um sistema de controle de versão.

##### *Github*
Um local remoto onde você pode armazenar o seu código, e onde todos os membros da equipe têm acesso. Pense nisso como um dropbox para o código. Uma das grandes diferenças, no entanto, é que a maioria dos repositórios no GitHub são públicos. Qualquer um pode ver seu código.

##### *Commit*
Uma maneira de salvar seu código em diferentes pontos ao longo do projeto. Ao contrário de muitas ferramentas que você pode ter usado no entanto, todos os commits são salvos. Isso cria um histórico do projeto e uma maneira de acompanhar as mudanças.

##### *Ramificações (Branches)*
Enquanto você trabalha em um repositório git o primeiro ramo em que está geralmente é a ramificação padrão. Ela é muitas vezes chamada de `master`. Se você começar a trabalhar em uma seção do site (por exemplo a estilização do rodapé), a melhor prática é você criar a sua própria ramificação para esse recurso. Criar a sua própria ramificação é como fazer uma cópia da `master` e renomeá-la. Quando você fizer um commit, suas mudanças agora estarão apenas nessa nova ramificação.

Nas seções a seguir vamos mostrar como fazer isso. Por enquanto, apenas observe que você sempre tem uma ramificação padrão, e pode ter tantos outros ramos quanto for preciso.

<a name="version-control" id="version-control"></a>
## Por que o Controle de Versionamento

##### Histórico do Código Base
Git pode lhe fornecer um histórico completo de cada commit feito em um projeto. Os seus benefícios incluem:

* Ser capaz de ver quais as diferenças nos arquivos do sistema você fez antes de você ter commitado.

* Ser capaz de ver quais as diferenças existentes entre commits.

* Ser capaz de se mover entre diferentes commit (ou lugares no tempo). Isto é especialmente útil se algo ficou quebrado enquanto você estava trabalhando nisso e você precisa começar de novo .

Na seção de introdução deste tutorial, não vamos ser capazes de cobrir todos estes benefícios na prática extensivamente. No entanto, pretendemos dar-lhe toda a informação que você precisa saber até o final.

##### Multiplas pessoas trabalhando nos mesmos arquivos
O controle de versão torna isso possível. Se você trabalhar em um arquivo e eu trabalhar no mesmo arquivo ao mesmo tempo, quando quisermos combinar as nossas mudanças o git nos permitirá manter ambas as versões salvas para podermos compará-las. Isso nos permite integrar as nossas mudanças mais rapidamente.

Nós vamos praticar isso mais a frente.

##### Ramificações (Branching)
Um bom fluxo de trabalho com o git sempre envolve ramificaçôes. Ter ramos ajuda a organizar o código e manter o controle de quem está trabalhando em quê.

<a name="tutorial" id="tutorial"></a>
## Tutorial

Antes de começarmos, se você não tem uma conta no Github, por favor crie uma.

Agora, por favor, faça o 'fork' (a "bifurcação) deste repositório.

![fork button on github](./img/fork.png)

Na sua máquina local, por favor tenha certeza que você tenha o git instalado.

Se você está usando um Mac, a maneira mais fácil é instalar o git com [Homebrew](http://brew.sh/). Quer saber mais sobre o Homebrew? Confira só esse link [tutorial](http://computers.tutsplus.com/tutorials/homebrew-demystified-os-xs-ultimate-package-manager--mac-44884).

Para Windows use http://git-scm.com/download/win. e para Linux instale usando estas instruções http://git-scm.com/download/linux.


<a name="getting-started" id="getting-started"></a>
### Começando
O próximo passo é clonar a versão bifurcada (forked) deste repositório. Na página principal do repositório, copie a URL mostrada aqui:

![where to copy url on github](./img/git-clone.png)

E então use o comando no seu terminal:

```
git clone https://github.com/Grrrls/learn-git-basics.git
```

Agora você deve ser capaz de redirecionar para o diretório recém criado usando a linha de comando.

Em seguida, é bom adquirir o hábito de, depois de cada comando, utilizar o `git status`. Vamos usá-lo agora.

```
git status
````

Agora, verifique em qual ramo (branch) você está:

```
git branch
```

Você só deve ver `master` que é o ramo padrão neste repositório.

Quando existirem outros ramos da sua repo o ramo verde é o atual, o que você se encontra.


<a name="branching" id="branching"></a>
### Ramificação (Branching)
O próximo passo é criar seu próprio ramo de trabalho, tente o seguinte:

```
git branch new-branch
```

É melhor tentar nomear seus ramos tão específico quanto possível, de modo a não confundi-los com os outros. Há muitas convenções de nomenclatura para ramos por ai, mas para esta semana simplesmente tente nomeá-los a partir de um recurso. Por exemplo (`navbar-collapse` ou `sass-file-structure`). Para ver todos os seus ramos:

```
git branch
```

Como você pode ver, você criou o seu ramo, mas não estão atualmente nele. Para navegar para ele digite:

```
git checkout new-branch
git branch
```

Agora você pode ver que você está naquele ramo. Volte para o master e agora vamos excluir `new-branch`.

```
git checkout master
git branch -d new-branch
git branch
```

Como você pode ver, seu ramo sumiu.


<a name="changes" id="changes"></a>
### Fazendo Mudanças
Agora é hora de fazer algumas mudanças no projeto. Faça um novo ramo chamado `update-cheatsheet` e vá para ele. Abra o aruivo cheatsheet.md no seu editor de texto preferido.

Como você pode ver, este contém todos os comandos que você precisa para começar a usar git. Continue adicionando nele todos os novos comandos que você aprender. Para começar, aqui é um comando que tanto cria uma filial quanto te move para ele ao mesmo tempo:

```
git checkout -b <new branch name>
```

Adicione esse comando e a sua descrição para cheatsheet.md e salve-o. Agora em seu terminal:

```
git status
```

Você verá algo assim:

![git status example](./img/git-status.png)

Você verá as alterações em vermelho. Agora precisamos adicioná-las para a área de git 'staging'. Fazer isso é como dizer ao git para prestar atenção a esses arquivos e começar a monitorar as suas alterações. Para fazer este comando este digite:

```
git add cheatsheet.md
git status
```

Agora você pode ver que o nome do arquivo ficou verde. Agora, para confirmar as suas alterações:

```
git commit -m 'adding new command in the cheatsheet'
git status
```

A mensagem pode ser qualquer coisa, mas o melhor é fazer algo que descreva o que você fez. Você também pode usar o comando `git commit` sem `-m '<message'`, no entanto cuidado que ele vai mandar você para um editor de texto chamado Vim. Embora aprender a usar o Vim é importante, não é necessário nesta fase. Digitando `:q` vai te tirar dela e commitar novamente com uma mensagem.


<a name="merging" id="merging"></a>
### Integrando as Alterações com o Master
Agora que você fez e commitou as alterações, é hora de integrar (merge) o seu ramo com o master. Mesmo que você não esteja trabalhando com mais ninguém neste repositório, é sempre uma boa prática se certificar de que o seu ramo atual está completamente atualizado com o master. Imagine se você estivesse trabalhando com uma equipe e alguém já fez um push no master. Se você e esse alguém tiverem alterado o mesmo arquivo, é bastante provável que as suas alterações não serão compatíveis com a deles. Para evitar isso, você mescla as suas alterações com a deles para evitar problemas futuros. Faça o chekout de volta para o master e de um pull. Estes comandos são assim:

```
git checkout master
git pull origin master
```

Fazer um Pull significa que você está recebendo todas as mudanças recentes do branch master remoto, que está localizado no Github. Em seguida volte ao seu ramo (`update-cheatsheet`) e mesclar (merge) com o master.

```
git merge master
```

Mesmo que nesta situação não há qualquer alteração para integrar, o melhor é adquirir o hábito de passar por essas etapas em seu fluxo de trabalho. Integrar assim significa tomar quaisquer eventuais alterações no master e mescla-las com o ramo que você está atualmente.

Após mesclar com o master que você tem que fazer um push das alterações no repositório remoto (Github).

```
git push origin update-cheatsheet
```

Quando você fizer o pull ou push você está se referindo ao seu repo remoto, ou origem. No exemplo `git push origin <nome do ramo>` você está dando um push nas suas alterações locais para um ramo remoto que vocês dois estão criando e nomeando. Como você está criando este ramo a partir do seu local é muito mais simples usar o mesmo nome tanto para o local quanto para o remoto.

Para mais informações em push veja [here](https://help.github.com/articles/pushing-to-a-remote/)

Vá para o seu navegador e abra este repositório no github. Pressione o botão de branch.

![branches button in gitub](./img/github-branch.png)

E, em seguida, faça uma solicitação (Pull request) para o master.

![viewing all your branches on github](./img/view-github-branches.png)

Depois disso, você verá um botão de integração (merge). Pressione-o e exclua o seu ramo. Agora, o seu master remoto está completamente atualizado com as suas últimas alterações.

Volte para o seu terminal e navegue para o seu ramo master local. Faça um Pull. Você vai ver o seu ramo atualizar (fast-forward). Exclua o ramo `update-cheatsheet`.


<a name="conflicts" id="conflicts"></a>
### Conflitos de Integração
Verifique todos os ramos sobre deste repositório, mesmo os remotos. Para fazer este comando este uso :

```
git branch -a
```

Você deve ver algo assim:

![see all branches in github](./img/git-branch-a.png)

Execute o comando:

```
git checkout merging-experiments
```

Abra o git cheatsheet, como você pode ver, existem algumas diferenças entre este e master. Para ver essas diferenças use o comando:

```
git diff master
```

As diferenças em verde são as adições neste ramo, que não existem no master. As diferenças em vermelho são as coisas que estão no master e não existem neste ramo.

Integre com o mestre. Você deve ter um conflito git que é algo assim:

![git merge conflict example](./img/merge-conflict.png)

Você vê as linhas no topo? A primeira seção é rotulada `HEAD`, essa é a partir deste ramo. A próxima seção é do master. Exclua as linhas e qualquer outro código que você queira até que o cheatsheet pareça como você deseja.

Depois do `git status`, adicione os arquivos em vermelho, commite, e realize o pull. Em seguida, faça uma solicitação (PR) como antes e integre-os. Não se esqueça de atualizar o seu ramo master local e excluir o ramo resultante da integração Github em seu repositório local. É bom para manter seu ambiente de trabalho limpo e organizado.


<a id="changing-file-structure" name="changing-file-structure"></a>
### Mudando a Estrutura de Arquivos
Imagine que você está trabalhando em um projeto que está ficando cada vez maior em tamanho. À medida que novos arquivos são adicionados, faz sentido para agrupar alguns em pastas. Por exemplo, é uma boa idéia para manter todos os arquivos CSS em uma pasta e os arquivos JS em outra etc.

Vamos supor que você acabou de clonar um repositório estruturado assim:
```
index.html
stylesheet.css
script.js
```

No entanto, você prefere separá-los em pastas assim:
```
css/stylesheet.css
js/script.js
index.html
```

A fim de conseguir isso, o commando `git mv` vem a calhar. Usá-lo para mover arquivos *garante preservação do histórico* dos arquivos que você trabalha. Para alterar a estrutura de arquivos como acima (e criar novas pastas ao mesmo tempo) use o comando:
```
mkdir css && git mv stylesheet.css ./css
mkdir css && git mv script.js ./js
```
(Esse trecho junta o `mkdir` e o `git mv` usando o operador `&&`).

A utilização da função básica é
```
git mv <source> <destination>
```
O comando também usa parâmetros opcionais. Para saber mais, consulte [documentation](http://git-scm.com/docs/git-mv).


<a name="github-flow" id="github-flow"></a>
## Fluxo Github
Fluxo Github é o que a maioria das equipes na Founders & Coders segue. É simples e eficaz.

Para um guia visual e algumas dicas úteis:
https://guides.github.com/introduction/flow/

Para descobrir o por quê o Github utiliza o fluxo Github:
http://scottchacon.com/2011/08/31/github-flow.html



<a name="git-collaboration" id="git-collaboration"></a>
# Git para a Colaboração

Git para a colaboração visa os alunos da segunda semana do curso, ou aqueles que dominaram a primeira seção. Mesmo que a maioria dso conselhso neste tutorial vai demorar um pouco para digerir - e prática é essencial. Uma boa meta é compreender todos estes conceitos, e implementar, pelo menos, a maioria dessas dicas em seus projetos de colaboração antes de terminar o seu tempo como estudante da Founders & Coders.


<a name="further-terminology" id="further-terminology"></a>
## Further Terminology

##### Commit Hash:
![commit hash picture](./img/commit-hash.png)

##### HEAD
Simplificando, a HEAD é uma referência a um commit object. Para mais informações consulte:
http://eagain.net/articles/git-for-computer-scientists/


<a name="timeline" id="timeline"></a>
## A Linha do Tempo (Timeline)

Como discutido anteriormente o Git armazena todos os commits no projeto. Você pode usá-los como um cronograma e viajar para qualquer ponto no tempo. Esta seção vai te mostrar uma forma simples de trabalhar em projetos com sua equipe.

Antes de começar verifique se você está com um terminal aberto na cópia local deste repo. O mesmo que foi utilizado para o primeiro tutorial. Faça um novo ramo chamado `timeline-practice` e navegar nele.

Passo 1) Crie um novo diretório no projeto através da linha de comando. Vamos chamá-lo `time`.

```
mkdir time
```

Passo 2) Faça também um novo arquivo no diretório e chame-o do que quiser. Um arquivo de texto simples deve suficiente. Depois que você terminar, abra-o.

```
touch time/newfile.txt
open time/newfile.txt
```

Escreva a data e hora atual e uma mensagem curta para o seu futuro eu. Salve isso. Em seguida adicione e commite as suas mudanças. Sua mensagem de commit deve ser uma descrição do que você acabou de fazer.
Repita o passo 2 mais duas vezes, excluindo a mensagem de tempo anterior e adicionando uma mensagem de tempo diferente. Certifique-se de adicionar e commitar em cada vez. Certifique-se de suas mensagens de commit são únicas e que você poderá dizer qual foi a primeira, a segunda e a terceira.

Passo 3) Em seguida digite o comando:

```
git log
```

Você deve ver algo assim:

![git log example](./img/git-log.png)

Escolha o segundo commit de tempo que você fez e copie o hash. Use `q` para sair do log e faça o checkout para o commit.

Passo 4) 
```
git checkout <commit hash>
git status
```

![git detached head warning](./img/detached-head.png)

Como você pode ver após você checkout será exibida uma mensagem informando o que você está em um 'detached HEAD', o que significa a sua não estão trabalhando em qualquer ramo atual. Abra o arquivo na pasta de tempo e olhe para a mensagem e para o tempo. Deve ser o segundo que você escreveu.

Repita o passo 4, e use o hash do primeiro commit que você fez. Abra o arquivo e veja que o tempo do seu primeiro commit, e sua mensagem para si mesmo. Isto vai voltar no tempo. Você pode facilmente ir para trás tanto o quanto você gostaria no projeto e ver iterações anteriores deste tutorial!

Em seguida, devemos voltar para o futuro. A maneira mais rápida e mais fácil é fazer o checkout para o ramo `timeline-practise` e você deve estar atualizado. No entanto, você também pode navegar de volta para o último commit a partir de onde você está agora. Primeiro, verifique o `git log`. Você vai notar que os seus últimos commit não estão mais lá. Este é o lugar onde outro comando é útil. `git reflog` usado para encontrar commits recentemente "perdido", você deve ver algo como:

![git reflog example](./img/git-reflog.png)

Encontre o nome do último commit que você fez (a terceira vez que você gravou) e copie o hash curto em amarelo. Volte para esse commit e use o `git diff timeline-practise`. Não deve haver nenhuma diferença.
Volte para o `timeline-practise` e faça o push para o Github para fazer uma Pull Request no master. Certifique-se de verificar primeiro que ele está atualizado com o master localmente.


<a name="commits" id="commits"></a>
## Commitando


<a name="when-commit" id="when-commit"></a>
### Quando você deve Commitar?

Você deve visar para que cada commit seja uma versão "segura" do projeto. Isto significa que se você fizer o checkout para qualquer commit em sua linha do tempo, ele deve refletir onde o projeto estava nesse ponto e deve ser funcional .

Tendo em conta, que quando você commita é muito importante, tenho ouvido duas orientações muito úteis.

A primeira é que, conforme você for completando a tarefa, você fará vários commits em diferentes momentos durante a tarefa. No final você junta todos os commits para fazer um commit muito informativo dessa tarefa. Vou falar sobre maneiras de integrar commits juntos em uma seção posterior.

O segundo método é o que você trabalha através da sua tarefa e a concluí antes de adicioná-la ou commita-la. Em seguida, você verificar o status do repo e olha todos os arquivos que foram alterados. O próximo passo é adicionar e commitar seletivamente.

Através da minha pesquisa eu encontrei muitas metodologias diferentes e, acima de tudo, você deve tentar fazer o que parece ser o mais natural para você. Eu uso ambas as metodologias, dependendo da extensão da tarefa. A melhor coisa é manter sempre em mente o que você e seus colegas vão, inevitavelmente, precisar voltar para seus commits e vai ajudar a todos se os commits estiverem nomeados apropriadamente.

Da mesma forma, mesmo em Pull Requests, você deve visar fazer dos seus commits um resumo claros e concisos de quais tarefas foram concluídas em que ramo. Dessa forma, a pessoa que rever a sua solicitação entenderá o que eles irão rever antes mesmo de olhar para o próprio código.


<a name="commit-message" id="commit-message"></a>
### Commit messages

Just like choosing when to commit, and what to commit, it is also important to think about your naming. It is always good to be as descriptive as possible with your commit messages.

Also consider:
* Present tense for your commit messages
* If related to an issue on github, should contain issue number
* The first line should be 50 characters or less. Your message should be brief and to the point.
* Focus on why you did something, not how you did it
* Avoid `ands`. If you find yourself wanting to write `and`, you should probably break up that commit into multiple ones.

Remember that the purpose of this commit is to be a message for future you, or your colleagues who may not have known what you are working on. Try to think about your message with this in mind.

Many development teams take it one step further and turn their commit messages into change logs. These change logs may be used for user consumption making it all the more important to have clear messages of what was done for that commit.

I tend to favour one line commits for simplicity, but many schools of thought out there prefer multiline commit messages. For examples of "best practice" formats for this see:
* [Commit message guidelines Angular](https://github.com/angular/angular.js/blob/master/CONTRIBUTING.md#commit-message-format)
* [Informative guidelines, and a cute cat filled slideshow](http://www.slideshare.net/TarinGamberini/commit-messages-goodpractices)


<a id="merging-commits" name="merging-commits"></a>
### Merging Commits

Often you will find yourself wanting to merge commits, or organising your early commits slightly differently on a branch to better demonstrate what you worked on. I will briefly go through one easy way to do this.

#### Reset Soft
This is my preferred method of merging commits together. It leaves you with lots of flexibility.

To begin, make a new branch and make some new files and commit regularly (at least twice).

Next `git log` and pick the 3rd most recent hash. Copy it and:

```
git reset --soft <commit hash>
git status
git log
```

Your working directory shouldn't changes, but all the files that you changed should be in green. Your log should have the newest commit as the hash you copied. Even though all your work is still the same as before the reset, the commits are different. Then you can commit again and this is an easy way to replace 2 or more commits with one commit.


For more information and techiques see:

* [What to learn more about reset?](https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting/commit-level-operations)
* [Only want to ammend the previous commit?](https://www.atlassian.com/git/tutorials/rewriting-history/)
* [The Golden Rule of Rebasing](https://www.atlassian.com/git/tutorials/merging-vs-rebasing/the-golden-rule-of-rebasing)



<a name="resources" id="resources"></a>
# RESOURCES [![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/NataliaLKB/learn-git-basics/issues)

> Have you ***found a useful Git or GitHub resource or tutorial? Please let us know*** by creating an issue

* For generating ssh keys https://help.github.com/articles/generating-ssh-keys/
* CodeSchool "Git Real" tutorial: http://gitreal.codeschool.com/
* Atlassian (makers of *SourceTree*) Git Tutorials: https://www.atlassian.com/git/tutorials/
* Git Branching: https://github.com/pcottle/learnGitBranching
+ Interactive tutorial: http://gitimmersion.com
+ Build Podcast (intro to Git) Video: http://build-podcast.com/git/
+ Git User Manual: https://www.kernel.org/pub/software/scm/git/docs/user-manual.html
+ GitHub's Treasure Trove of Video Tutorials: https://www.youtube.com/user/GitHubGuides (channel) and *specifically*: https://www.youtube.com/watch?v=FyfwLX4HAxM
+ The *simple* guide to git: http://rogerdudler.github.io/git-guide/
+ Jeff Schomay's Git-Fu presentation: http://slides.com/jschomay/git-fu
+ Git Pretty: http://justinhileman.info/article/git-pretty/ (anything visual makes learning git much easier...)
+ Intermediate: http://www.raywenderlich.com/74258/git-tutorial-intermediate
+ Visualize your Git with **SourceTree**: http://www.sourcetreeapp.com/
