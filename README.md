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
### Merging Changes with Master
Now that you have made and committed your changes, it is time to merge your branch with master. Even though you are not working with anyone else on this repository, it is always good practice to make sure your current branch is completely up to date with master. Imagine if you were working with a team. Someone else has already pushed up changes to master. If that someone else and yourself have changed the same file, it is quite likely that your changes will not be compatible with theirs. To avoid this, you want to merge your changes with theirs to avoid future problems. Checkout back onto master and pull down. These commands look like this:

```
git checkout master
git pull origin master
```

Pulling down means that you are getting any recent changes from the remote master branch which is located in Github. Next go back to your branch (`update-cheatsheet`)  and merge with master.

```
git merge master
```

Even though in this situation there isn't any changes to merge, it is best to get in the habit on going through these steps in your work flow. Merging like this means taking any possible changes in master and merging them with the branch you are currently on.
After you merge with master you have to push your changes to the remote repo (Github).

```
git push origin update-cheatsheet
```

When you pull or push you are referring to your remote repo, or origin. In the example of `git push origin <branch name>` you are pushing your local changes to a remote branch that you are both creating, and naming. Since you are creating this branch from your local one it makes things much simpler if you use the same name for your remote branch, as your local one.

For more information on pushing, see [here](https://help.github.com/articles/pushing-to-a-remote/)

Go to your browser and open up this repository in github. Press the branches button

![branches button in gitub](./img/github-branch.png)

And then make a pull request  to master

![viewing all your branches on github](./img/view-github-branches.png)

Afterwards you will see a merge button. Press it and delete your branch. Now your remote branch master is completely up to date with your latest changes.

Return to your terminal and navigate to your local master branch. Pull down. You will see your branch update (fast-forward). Delete the branch `update-cheatsheet`.


<a name="conflicts" id="conflicts"></a>
### Merge Conflicts
Check all the branches on this repository, even the remote ones. To do this use this command:

```
git branch -a
```

You should see something like this:

![see all branches in github](./img/git-branch-a.png)

Run the command:

```
git checkout merging-experiments
```

Open up the git cheatsheet, as you can see there are some differences between this and master. To see these differences use command:

```
git diff master
```

The differences in green and the additions on this branch, that don't exist on master. The red are the things that are on master, that don't exist on this branch.

Merge with master. You should have a git conflict that looks something like this:

![git merge conflict example](./img/merge-conflict.png)

Do you see the lines at the top. The first section is labelled `HEAD` those are from this branch. The next section is from master. Delete the lines, and any other code you want until the cheatsheet looks like how you want it to look.

Afterwards git status, add the files in red, commit, and push. Then make a pull request to master like before and merge. Don't forget to update your local master branch, and delete the merged branch in Github and in your local repo. It is good to keep your working environments clean and organised.


<a id="changing-file-structure" name="changing-file-structure"></a>
### Changing File Structure
Imagine you're working on a project that's getting bigger in size. As new files are added, it makes sense to group some of them into folders. For example, it's a good idea to keep all CSS files in one folder, JS files in another etc.

Let's assume you've just cloned a repository structured like this:
```
index.html
stylesheet.css
script.js
```

However, you'd prefer to split these into folders like:
```
css/stylesheet.css
js/script.js
index.html
```

In order to achieve this, `git mv` command comes in handy. Using it to move files *ensures preserving history* of the files you work on. To change file structure like above (and create new folders at the same time) use command:
```
mkdir css && git mv stylesheet.css ./css
mkdir css && git mv script.js ./js
```
(This glues `mkdir` and `git mv` commands together with `&&` operator).

Basic function usage is
```
git mv <source> <destination>
```
The command also takes optional parameters. To find out more, refer to [documentation](http://git-scm.com/docs/git-mv).



<a name="github-flow" id="github-flow"></a>
## Github Flow
Github flow is what most teams at Founders & Coders follow. It is simple and effective.

For a visual guide, and some helpful tips:
https://guides.github.com/introduction/flow/

To find out why Github uses Github flow:
http://scottchacon.com/2011/08/31/github-flow.html



<a name="git-collaboration" id="git-collaboration"></a>
# Git for Collaboration

Git for Collaboration is aimed at the second week students of the course, or those that have mastered the first section. Even though most of the advice in this tutorial will take a while to digest - and practise is essential. A good goal is to understand all these concepts, and implement at least most of these tips in your collaborative projects before finishing your time as a student at Founders & Coders.


<a name="further-terminology" id="further-terminology"></a>
## Further Terminology

##### Commit Hash:
![commit hash picture](./img/commit-hash.png)

##### HEAD
Simply put, the HEAD is a reference to a commit object. For more information see: http://eagain.net/articles/git-for-computer-scientists/


<a name="timeline" id="timeline"></a>
## The Timeline

As discussed previously git stores all the commits on the project. You can use them as a timeline and travel back and forth in time. This section shows you a simple way of doing that which will come in handy as you work in projects with your team.

Before we start make sure you have a terminal open located at the local copy of this repo. The same one that was used for the first tutorial is essential. Make a new branch called `timeline-practice` and navigate onto it.

Step 1) Make a new directory in the project via the command line. Lets call it `time`.

```
mkdir time
```

Step 2) Also make a new file in that directory and call it whatever you like. A simple text file should be fine. After you are done, open it.

```
touch time/newfile.txt
open time/newfile.txt
```

Write the current time stamp, and a short message to your future self. Save it. Next add and commit your changes. Your commit message should be descriptive of what you just did.
Repeat step 2 twice more, deleting the previous time and message, and adding the new time and a different message. Make sure you add and commit each time. Make sure your commit messages are unique, and you can tell which one was first, second, and third.
Step 3) Next type in this command:

```
git log
```

You should see something like this:

![git log example](./img/git-log.png)


Pick the second time commit that you made and copy the hash. Use `q` to exit the log and checkout to your commit.
Step 4) 
```
git checkout <commit hash>
git status
```

![git detached head warning](./img/detached-head.png)


As you can see after you checkout a message appears informing your that you are in a 'detached HEAD' state, meaning your are not working on any current branch. Open up the file in the time folder and look at the time and message. It should be the 2nd one that you wrote.

Repeat step 4, and use the hash of the first time commit you made. Open the file and see that the time of your first commit, and your message to yourself. This is going back in time. You can easily go back as far as you like in the project and see older iterations of this tutorial!

Next, we should go back to the future. The quickest and easiest way is to checkout onto the`timeline-practise` branch and you should be back up to date. However, you can also navigate back to the latest commit from where you are now. First, check `git log`. You will notice your latest commits are no longer on there. This is where another command is handy. `git reflog` is best used to find recently "lost" commits. you should see something like:

![git reflog example](./img/git-reflog.png)

Find the commit name of the last commit you did (the third time that you recorded) and copy the short hash in yellow. Checkout back to that commit, and `git diff timeline-practise` there should be no difference.
Checkout back to `timeline-practise` and push up to Github to make a pull request to master. Make sure you first check that
it is up to date with master locally.


<a name="commits" id="commits"></a>
## Committing


<a name="when-commit" id="when-commit"></a>
### When should you commit?

You should aim each commit to be a "safe" version of the project. This means that if you checkout to any commit in your timeline, that should reflect where the project was at that point, and be functional.

Given that, when you commit is very important. I have heard two very useful guidelines.

The first, is that as you complete the task assigned to you, you make several commits at different times during that task. In the end you merge all those commits together to make one very informative commit of that task. I will talk about ways to merge commits together in a later section.

The second method is you work through your task and complete it before adding or committing at all. Then you check the status of the repo and see all the files you have changed. The next step is selectively adding and committing

Through my research I have come across many different methodologies, and ultimately you should try to do what seems the most natural to you. I use both of these methodologies depending on the extent of the task before me. The best thing is to always keep in mind that you and your colleagues will inevitably need to go back to your commits and it will help everyone if commits are aptly named.

Likewise, even in pull requests, you must aim to make your commits a clear and concise summary of what tasks where completed on that branch. That way the person reviewing your pull request understands what they will be reviewing before looking at the code itself.


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
