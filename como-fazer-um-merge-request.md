<!-- TITLE: Como Fazer Um Merge Request -->
# Fazer Rebase da sua branch com a Master

Para fazer um Merge-Request será necessário converter todos os commits presentes na sua branch, em apenas um commit.
Isto evita a poluição na branch master e nos obriga  a desenvolver pequenas partes na branch de trabalho para que não se perca a rastreabilidade.

Para fazer o rebase com a master será necessário executar o seguinte comando:

```shell
$ git rebase -i master
```

Isto abrirá um documento para que o rebase possa ser feito de forma interativa, similar ao conteúdo abaixo.

```
pick 1fc6c95 Patch A
pick 6b2481b Patch B
pick dd1475d something I want to split
pick c619268 A fix for Patch B
pick fa39187 something to add to patch A
pick 4ca2acc i cant' typ goods
pick 7b36971 something to move before patch B
```

O primeiro commit deverá ser selecionado com `pick` e os demais deverão ter a sua mensagem de commit descartada com a opção `fixup`.

```
pick 1fc6c95 Patch A
fixup 6b2481b Patch B
fixup dd1475d something I want to split
fixup c619268 A fix for Patch B
fixup fa39187 something to add to patch A
fixup 4ca2acc i cant' typ goods
fixup 7b36971 something to move before patch B
```

Ao sair do modo interativo, todos os commits se tornarão apenas um.
# Reescrevendo a mensagem de commit

Para  facilitar a rastreabilidade devemos escrever uma boa mensagem de commit como cita Chris Beams em [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/), e seguindo os padrões devemos então rescrever a mensagem de commit.

Para tal faça:


```shell
$ git commit --amend
```

# Sincronizando as alterações

Ao finalizar a reescrita da mensagem de commit será necessário sincronizar o repositório local com repositório remoto, porém haverá diferenças entre as histórias e não será possível fazer o `push` do modo convencional, portanto será necessário utilzar:

```shell
$ git push --force
```

**Use `--force` com sabedoria**

# Abrindo o Merge-Request

O abertura do MR ocorre no Gerenciador Visual do Repositório remoto.

No Gitlab, acesse a página do projeto, então acesse a branch desejada. Clique no botão de Criação de Merge Request, altere as opções se necessário.
