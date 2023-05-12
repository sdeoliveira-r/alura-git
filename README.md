======================= Início ======================= 
cd 4_git-github 
git config --local user.name "Seu_Nome" 
git config --local user.email "Seu_Email" 
git init 
git status 
git add .
git commit -m "First base commit" 

======================= Git log (Registros) ======================= 
Mais informações  <https://devhints.io/git-log> 
git log 
git config --local user.name "Rafael" 
git log --oneline 
git log -p 

git log --pretty="format:%H" 
git log --pretty="format:%h %s" 

git add .gitignore 
git commit -m "Adicionando .gitignore" 
git log --pretty="format:%h %s %ae" 

======================= Criando Repositório Local ======================= 
cd .. 
mkdir 4_servidor_local 
git init --bare 
cd ../4_git-github 
git remote add repositorio-local /home/rafael/Documentos/4_servidor_local/ 
git remote 
git remote -v (buscar local para fetch e push) 

======================= Criando usuario1 e clonando projeto ======================= 
cd .. 
cd mkdir usuario1 
cd usuario1 
git clone /home/rafael/Documentos/4_servidor_local/ folder.usuario1 

======================= Enviar projeto p/ repositorio-local ======================= 
cd ../4_git-github/ 
git push repositorio-local main 

======================= Renomear e sicronizar dados no rep. local ======================= 
cd ../usuario1/folder.usuario1 
git remote 
git remote rename origin servidor_local 
git remote rename servidor_local repositorio-local 
git pull repositorio-local main 

======================= Usuário1 fazendo alterações ======================= 
Depois de fazer modificações no index.html ... 
git status
git add index.html
git commit -m "Modificações realizadas"
git remote
git push 4_servidor_local main

======================= Trazer alterações feitas pelo usuario1 que estão no repositório-local ======================= 
git pull repositorio-local main 

======================= Enviar para o Github ======================= 
Criar um novo repositório ... 
git remote add origin https://github.com/sdeoliveira-r/alura-git.git
git push origin main

======================= Git Branch(Ramos) ======================= 
git branch 
git branch header (criar a branch header)
git checkout header (ir para branch header)
git checkout -b section (criar branch section e ir para branch section)

======================= Atribuir nome de usuário p/ uma branch ======================= 
cd /home/rafael/Documentos/usuario1/folder.usuario1/
git checkout main
git config --local user.name "usuario1"

======================= Desfazer modificações ======================= 
git checkout -- <file> (desfazemos uma alteração que ainda não foi adicionada, ou seja, antes do git add .)
git reset HEAD <file> (desfazemos uma alteração depois do git add .)
git revert <hash commit number> (desfazemos uma alteração depois do git commit)

======================= Salvar alterações p/ retomar posteriormente ======================= 
git stash
git stash list (lista stash)
git stash apply number << stash@{number} >>
git stash drop (remove a stash)
git stash pop (traz e remove a stash)

=======================* Viajando no tempo *======================= 
git log --oneline
git checkout <commit number hash>
git checkout main (voltar à linha principal de desenvolvimento)

======================= Git diff exibir todas as mudançãs entre um commit e qualquer outro ======================= 
git diff
git diff hash_commit_inicial..hash_commit_final 

*** É possível comparar as alterações entre duas branches com git diff <branch1>..<branch2> ***

======================= Git merge ======================= 
cd ..
cd usuario1
cd folder.usuario1
git branch
git checkout main (ir para branch main)
git status
git merge section (trazer as alterações da branch section p/ branch main)

*** O merge junta os trabalhos e gera um merge commit. ***

======================= Git rebase ======================= 
(Traz os commits de uma branch p/ outra; o git rebase não gera commit de merge, isso simplifica os logs)
cd ..
cd .. 4_git-github
git log --graph
git branch
git checkout header
git add .
git commit -m "Alterações"
git checkout main
git branch
git rebase header
git push repositorio-local main

*** O rebase aplica os commits de outra branch na branch atual. ***

Fazendo alterações na branch section:
git branch section
Faça alterações no projeto ...
git status
git add .
git commit -m "Alterações na branch section"
git checkout main
git branch
git merge section (Execute o comando git merge section p/ trazer o trabalho feito na branch section p/ a branch main

*** Antes de enviar modificões para o repositorio local ***
git pull repositorio-local main (trazer dados do repositório local)
git push repositorio-local main (depois, enviar alterações p/ o repositório repositorio-local)

======================= Checkpoint (tag) em uma release e/ou em uma versão =======================
git tag -a v0.1.0 -m "Primeira versão (BETA) da aplicação"
git tag
git remote
git push repositorio-local v0.1.0 (enviando p/ o repositorio-local)
git remote -v
git push origin main (enviando p/ o github)
git push origin v0.1.0 (enviando tag v0.1.0 p/ o github)