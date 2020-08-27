# Curso de Git (Alura)

![screenshot-main](https://github.com/guiemi/Curso-Git-Alura/blob/master/assets/Screen%20Shot%202020-08-26%20at%2014.01.44.png)

## Curso de Git (Parte 1/2)

### Conceitos que eu não conhecia

#### log

* Para listar menos informações no log: `git log --online`
* Para listas mais informações: `git log -p` (mostra alterações)

#### diff

* Visualizando as alterações/diferenças entre um commit e outro: `git diff <hash_1>..<hash_2>`.

#### tags

* `git tag -a v0.1.0 -m "Mensagem da tag"`
* `git push origin v0.1.0`

#### Outros conceitos

* Site que mostra várias formatações interessantes para você personalizar seu `git log`: https://devhints.io/git-log-format
* Bare repositories 

## Curso de Git (Parte 2/2)
### forks

* Num fork, você adiciona como origin o origin do próprio fork
* ~~Você adiciona como upstream o origin do repositório de onde você forkou~~

### squash commits

Para unir commits, usamos o `git rebase`:

* `git rebase -i HEAD~3`, em que o `-i` significa **interativo** e `HEAD~3` significa três *commits* anteriores ao **HEAD**, incluindo ele próprio.
* `git rebase -i 9ee44a8`: você passa o hash do commit a partir do qual você irá juntar commits em um só (**excluindo ele próprio**).
* Na tela do Vim que se abrirá, você seleciona `pick` ou `s` (**squash**), em que o `pick` será o commit escolhido como o único reduzido resultante e os marcados com `s` serão mesclados entre si e ao `pick`.
* Na próxima tela, informe uma nova mensagem de *commit*.

### cherry pick

Significa selecionar a dedo apenas um commit para uma branch

1. Copie o hash do commit que você deseja trazer
2. Dê `checkout` na **master** e rode `git cherry-pick <hash_do_commit>`

### bisect + show

* `git bisect start`: inicia a busca
* `git bisect good/bad`
* `git bisect reset`: encerra a busca

* `git show`: mostra todas as alterações que um commit fez

### blame

Encontrar o responsável por uma alteração em uma determinada linha de um arquivo

`git blame <arquivo>`

### Git Flow

* A `master` só serve para receber **merges/rebases** da `develop` e das `hotfixes`. A partir das atualizações da `master` é que são geradas novas *tags*.
* A partir da branch `develop` são criadas todas as branches de `feature`. Todas as alterações dessas branches são mergeadas de volta na `develop`.
  * **feature** --> **develop** --> (**release** -->) **master**
* Na `release` começa o processo de lançar uma nova versão. Sempre que um *bug* for corrigido na `release`, as alterações voltam para a `develop`, pois outras *features* podem se aproveitar dessa correção. Quando tudo estiver corrigido, a `release` é mergeada na `master` para receber uma **tag**
  * **release** --> **master**
* Quando um *bug* for encontrado na `master`, é criada uma `hotfix` cujas alterações são mergeadas diretamente na `master`, mas também na `develop`, pois a `develop` precisa se aproveitar dessa correção

### Eventos (Git Hooks)

 

