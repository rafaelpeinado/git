# Using GitFlow
## Introduction
### Git Branching Models
* **Centralized:** onde mantemos tudo em um servidor centralizado
* **Feature branch:** onde cada desenvolvedor cria sua própria branch para o trabalho que está fazendo atualmente
* **GitFlow** 
* **There are others** 

#### Centralized
* Temos um repositório centralizado
* Os usuários finais simplesmente clonam esse repositório
* Dá pull todas as suas alterações daquele repositório central para a sua máquina local
* Quaisquer alterações feitas são salvas locamente e, em seguida, essas alterações locais são enviadas (push) de volta ao repositório central
Ou seja, na verdade estão todos trabalhando no mesmo repositório, em uma ramificação desse repositório
Esse modelo é muito semelhante ao SVN ou CVS. Nesses sistemas de controle de source (origem), a branch é muito cara. Então as pessoas tendem a trabalhar em uma única branch.

##### Centralized Workflow
Temos um repositório central, alguém faz uma mudança nesse repositório. Podemos dar pull do repositório para a máquina local, fazer alterações nele e, em seguida, dar push dessas alterações locais de volta para o repositório central. Mas há apenas um repositório. Apenas uma branch nesse repositório. Um modelo muito simples. Se estamos trabalhando com equipes pequenas ou talvez trabalhando sozinho, este modelo é perfeitamente aceitável.

#### Feature Branch Workflow
Temos um repositório central e as pessoas ainda fazem alterações nesse repositório. Portanto, as alterações são mescladas em uma branch nesse repositório. No entanto, para qualquer feature em que estejamos trabalhando, quaisquer alterações que queremos fazer em nosso código, criamos uma feature branch (git checkout -b my-feature master). Fazemos as alterações nessa branch. Outros push de mudanças estão sendo feitos de volta para o repositório central enquanto estamos desenvolvendo nossa feature. Eventualmente, o nossa feature está concluída e desejamos mesclar essa feature de volta para o repositório central. Isso tem o benefício de ser razoavelmente simples. E também tem o benefício de manter as nossas alterações isoladas de outros desenvolvedores, de quaisquer alterações que possam estar fazendo, até que estejam prontas para ser feito push e mergeadas de volta para um repositório central.


### What Is GitFlow
* É mais complicado que o feature branch, pois criamos mais branches e há mais coisas para gerenciar.
* Temos duas branches que registram o histórico do projeto: a master (hoje é usado main) e a develop
* Todas a features, assim como o modelo de feature branch, terão suas próprias branches
* Também colocamos hotfixes em suas próprias branches
    * quando tivermos problemas com o código ativo e tivermos que criar uma correção, criaremos uma branch de hotfix para isso, fazemos as alterações na branch do hotfix e, em seguida, garantiremos que essas alterações sejam mescladas tanto na master quanto na develop
* Quando queremos fazer um lançamento (release), criamos um branch de release a partir da develop. Nesse ponto, mais correções para essa release vão para essa branch. Além disso, quaisquer correções que entrarem nessa branch precisam ser mescladas de volta para develop. Em seguida, a release é feita fora da branch de release. Então, quando o lançamento é feito, esta branch pode ser excluída.


#### Gitflow Model
Temos um commit na branch master, a partir disso criamos a branch develop. A partir da branch develop, criamos branches de features que trabalharemos. Todo o trabalho deve ir realmente para o ramo de feature, mas haverá ocasiões que desejamos fazer pequenas alterações, e essas pequenas alterações podem ir simplesmente para a branch develop. Então o trabalho continua nas features. Supomos que identificamos um bug na branch master, então criamos uma branch hotfix a partir da branch master e podemos fazer a correção para essa branch. Assim que a correção foi feita, devemos mergear com a branch master e a develop. Continuamos trabalhando na branch de feature e quando este for finalizado, deve ser mergeado com a develop. Em algum ponto decidimos que estamos prontos para fazer uma release e a criamos a partir da branch develop. Podemos fazer mais alterações nessa branch de release. Por exemplo, se estamos testando e esses testes aparecem bug, nós podemos consertar os erros na branch de release. Depois que a release estiver em funcionamento, essas alterações devem ser mergeadas nas branches master e develop para não perdermos nenhuma dessas mudanças. A segunda feature continua sendo desenvolvida. E assim que finalizada, é mergeada na develop também, criamos release e quando estiver em produção, é mergeada na master.

### Installing GitFlow
* Gitflow é um conjunto de scripts que estendem do Git e, para usá-lo, precisamos instalar na máquina local.
    * é possível usar os comandos padrão do Git. Os scripts apenas executam um conjunto de comandos padrão, mas tornam o fluxo mais fácil.
* Esses scripts precisam ser instalados separadamente no Git. 
    * (Installing git-flow)[https://github.com/nvie/gitflow/wiki/Installation]

Precisamos clonar o instalador com **git clone --recursive git://github.com/nvie/gitflow.git**
Entrar na pasta com **cd gitflow** e no próximo passo instalar o Gitflow com **contrib\msysgit-install.cmd "[path to git installed folder]"** no caso do curso, "c:\Program Files\Git\".


### Setting Up a Repository to use GitFlow
* git init
* git flow init



