# Mês 01 - Fundamentos transversais

## Dia 01 - Segunda
Vi um pouco sobre como é o funcionamento do Git por debaixo dos panos, vendo o que significa fazer um commit, entender que o commit de fato é apenas um snapshot do momento em que aquele código estava, armazenando um hash e assim sendo possivel voltar para esse momento do código.
Vi sobre branches que também são commits onde fazem o track da HEAD, tendo como ponto inicial o ultimo commit da branch que ela foi criada.

[Link explicando diferença de worktree e branch](https://stackoverflow.com/questions/67995725/what-is-the-difference-between-a-new-working-tree-and-a-branch)

## Dia 02 - Terça
Começamos vendo sobre como destruir alguns commits que foram feitos usando git reset --hard e depois disso vimos como era possivel recuperar esses commits usando git reflog e resetando o HEAD para o commit desejado. Os commits ficão disponiveis no reflog por ~90 dias.
No primeiro desastre nos fizemos 5 commits e depois usamos git reset --hard HEAD~3 para destruir os ultimos 3 commits e depois usamos git reflog para recuperar os commits destruidos.
No segundo desastre nos criamos uma nova branch, fizemos um commit dentro dela e depois voltamos para a main e deletamos essa branch com o commit nela. Usamos git reflog para achar o hash do commit e usamos git switch -c <nome-branch> <hash-commit> para recuperar ele.
No terceiro desastre ele traz formas de corrigir a mensagen do ultimo commit com git commit --amend, como remover arquivos que estão em staged com git restore --staged <nome-arquivo> e como deletar alterações não commitadas de arquivos usando o git restore <nome-arquivo>.

## Dia 03 e 04 - Quarta e Quinta
Na aula de quarta vimos primeiro um pouco como funciona o rebase interativo do git, `git rebase -i <hash-commit | HEAD>` onde criamos alguns commits e depois usando o editor interativo vimos como escolher um commit com pick, remover com drop, usar squash para combinar o commit atual com o anterior, pickup onde também comina o commit com o anterior porém mudando o do commit, reword para mudar a mensagem do commit. Vimos também como cuidar de merge conflicts durante o rebase interativo.

Na aula de quinta vimos um pouco do bisect e como ele é feito, `git bisect start` onde iniciamos o bisect, podendo passar um hash de commit ou o HEAD como argumento para começar, sendo o primeiro argumento o hash de commit onde o bug foi introduzido e o segundo argumento o hash de commit onde o bug foi corrigido ou no momento atual. Depois de iniciar o bisect, o git irá testar automaticamente os commits intermediários até encontrar o commit que introduziu o bug. Após encontrar o commit, o bisect irá mostrar o hash do commit e a mensagem do commit, permitindo que você corrija o bug e faça o commit corrigido.

# Exemplo
## Semana 1 — 2026-XX-XX — Git profundo
**Estudei:** modelo de objetos, reflog, rebase interativo, bisect.
**O que quebrou:** conflito no rebase que eu não sabia resolver; descobri `git checkout --ours/--theirs`.
**O clique:** branch é só um ponteiro. Deixei de ter medo de criar/apagar branch.
**Ainda não entendi:** quando exatamente `rerere` ajuda.
**Aplicação no trabalho:** usei bisect para achar quando a formatação de data quebrou. Levou 4 min em vez de 1h.
