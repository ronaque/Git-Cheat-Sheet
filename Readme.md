- Git Status: $${\color{SEMPRE USAR}Red}$$

# Branches
- Listar: 
    - Branches locais e remotas: git branch -a
    - Branches locais: git branch -l
    - Branches remotas: git branch -r 
- Remover:
    - Local Soft: git branch -d \<nome-da-branch>
    - Local Force: git branch -D \<nome-da-branch>
    - Remoto: git push origin -d \<nome-da-branch>
- Criar: git branch checkout -b \<nome-da-branch>
- Mudar de branch: git checkout \<nome-da-branch>
    - Se houver modificações não commitadas, pode dar erro (ver git stash)

# Versionamento
### Conceitos:
    O Git mantém os arquivos em diferentes estágios:
        Untracked: O arquivo foi criado e ainda não rastreado.
        Unstaged(Modified): Arquivos que foram modificados, mas as mudanças ainda não foram adicionadas ao índice 
        Staged: Arquivos que foram modificados e adicionados ao índice, ou seja, prontos para serem commitados.
        Commited: Arquivos que foram commitados, ou seja, as alterações foram registradas no repositório local.
        Stashed: Permite que você salve temporariamente mudanças não commitadas para que possa trabalhar em outra coisa e depois retornar a elas.
    
    HEAD é um ponteiro que indica a branch e o commit que você está no momento.
    Modificado no git checkout. 

- Adicionar modificações(Untracked/ Unstaged -> Staged): 
    - Adicionar todas modificações: git add .
    - Adiciona um arquivo especifíco: git add \<nome-do-arquivo>
    - Adiciona todos os arquivos e subdiretórios de um diretório: git add \<nome-do-diretorio>

- Remover modificações(Staged -> Unstaged/Untracked):
    - Remover todas modificações: git restore --staged .
    - Remover um arquivo especifíco: git restore --staged \<nome-do-arquivo>
    - Remover todos os arquivos e subdiretórios de um diretório: git restore --staged \<nome-do-diretorio>

- Commitar arquivos (Staged -> Commited): git commit -m \<mensagem>

- Desfazer commits(Commited -> Unstaged):
    - Desfaz o último commit: git reset HEAD~1
    - Desfaz *n* commits : git reset HEAD~*n*
    - Desfaz um commit específico (cria um novo commit): git rever \<id-do-commit>

- Enviar commits para o repositório remoto: 
    - Primeiro envio de uma branch local: git push origin \<nome-da-branch>
    - Branch local já está trackeada no remoto: git push

- Puxar modificações do repositório remoto:
    - Puxar informações de novas branches e tags: git fetch
    - Puxar informações de uma branch: git pull origin \<nome-da-branch>

- Juntar modificações entre a branch em HEAD com outra branch: git merge \<nome-da-branch>

- Guardar informações temporariamente(Unstaged <-> Stashed)
    - Guarda as informações: git stash
    - Guarda as informações com uma mensagem: git stash push -m \<mensagem>
    - Listar as modificações guardadas: git stash list
    - Recuperar as últimas informações armazenadas: git stash apply
    - Recuperar as informações de um stash especifico: git stash apply \<index>

# Fluxos parão:

### Criação de nova branch(main -> ex1)
```
git checkout main
git pull
git checkout -b ex1
```
### Envio de modificações
```
git status
git add .
git status
git commit -m \<mensagem>
git push origin \<nome-da-branch>
```

### Resolução de pull request com conflito (ex1 -> main)
```
git checkout main
git pull
git checkout ex1
git merge main
(resolução dos conflitos nos arquivos)
git add .
git commit -m "Merge main"
git push origin ex1
```
