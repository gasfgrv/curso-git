- [1. Curso de git](#1-curso-de-git)
  - [1.1. Principais Conceitos](#11-principais-conceitos)
  - [1.2. Serviços Fundamentais](#12-serviços-fundamentais)
  - [1.3. Níveis de Configuração](#13-níveis-de-configuração)
  - [1.4. Workflow](#14-workflow)
  - [1.5. Estados dos Arquivos](#15-estados-dos-arquivos)
  - [1.6. Comandos](#16-comandos)
    - [1.6.1. Configuração Básica](#161-configuração-básica)
    - [1.6.2. Comandos Básicos](#162-comandos-básicos)
    - [1.6.3. Histórico e Conflitos](#163-histórico-e-conflitos)
    - [1.6.4. Branching, Merge e Rebase](#164-branching-merge-e-rebase)
    - [1.6.5. .gitignore](#165-gitignore)

# 1. Curso de git

## 1.1. Principais Conceitos

- **Commit:** Realiza uma mudança no projeto; mais específicamente, armazena uma mudança no banco de dados de uma forma que possa ser incorporada em versões futuras.
- **Update:** Solicitar que as mudança dos demais commits sejam incorporadas em sua cópia local do projeto. 
- **Branch (Ramo):** Uma cópia do projeto, porém isolada de uma maneira que as mudanças realizadas no branch não afetem o resto do projeto e vice-versa, *exceto quando as mudanças são delibaradamente mescladas*
- **Repositório:** Onde armazena-seo histórico do projeto.
- **Diretório de Trabalho:** É um diretório monitorado pelo controle de versão que contém os arquivos do projeto.
- **Configuração:** É o estado dos arquivos do projeto.
- **Revisão:** É uma configuração registrada no 
- repositório.
- **Rastreabilidade:** É poder seguir o trajeto de uma solicitação de mudança desde que foi proposta até o momento que voi implementada.
- **Changeset:** Diferença entre duas configurações.
- **Versão:** Revisão usada em produção.
- **Merge:** Aplica os commits de uma branch para a branch atual, encontra um commit em comum entre as branches (base) e adiciona os commits que a branch atual não posui (caso não existam) em um commit de merge.
- **Rebase** É semelhante ao merge porém é diferente no modo em que os commits são aplicados. No rebase, os commits a frente da base são temporariamente removidos e os commits da outra branch são aplicados, por os commits da branch são adicionados. 
- **Fetch:** Baixa as atualizações do remoto, mas não aplica elas.
- **Tags:** Uteis para definir versões do projeto, semelhante as branches porém não recebe mais commits, guardando um estado do repositório.

## 1.2. Serviços Fundamentais

- Registro da evolução do projeto;
- Controle de concorrência;
- Variações do projeto.

> É uma das ferramentas mais importantes do desenvolvimento de software.

Serve para:
1. Manter histórico do projeto;
2. Controlar a concorrência de edição;
3. Manter váriações do projeto.

## 1.3. Níveis de Configuração

- **Sistema:** É o mais abrangente vale para todos os usuários e repositórios, geralmente é usado em servidores de repositórios.
- **Global:** Vale para todos os repositórios do usuário, a configuração deste nível sobreescreve a configuração de sistemas.
- **Local:** É o mais específico e vale apenas para o repositório que está sendo usado, sobreescrevendo as configurações dos outros níveis. A configuração do nível local costuma ser gerada automaticamente durante a clonagem ou inicialização do repositório, geralmente contém o caminho original para o repositório que é usado na sincronização de repositórios e etc.

> **Arquivos de configuração (Linux)**
> - **Local:** `repositório/.git/config`
> - **Global:** `$HOME/.gitconfig`
> - **Local:** `/etc/gitconfig`

## 1.4. Workflow

- Editar
- Commitar
- Sincronizar com o repositório

## 1.5. Estados dos Arquivos

| Estado         | Stage     |
|:--------------:|:---------:|
| Não Monitorado | Untracked |
| Modificado     | Modifield |
| Preparado      | Staged    |
| Consolidado    | Commited  |

## 1.6. Comandos

### 1.6.1. Configuração Básica

- `git config --global user.name nome` Definir nome do usuário.
- `git config --global user.email email@email.com` Definir e-mail do usuário.
- `git config --global core.editor editor` Definir editor de texto.
- `git config --list` Listar todas as configurações
- `git config --list --global` Lista todas as configurações globais.
- `git config --global --edit` Abre o arquivo de configurações para edição.

### 1.6.2. Comandos Básicos

- `git init <repositório>` Inicializa um novo repositório.
- `git status` Mostra o estado dos arquivos dentro do repositório.
- `git log` Lista todos commits feitos no repositório.
- `git log --graph` Lista todos commits feitos no repositório junto com a reprentação dos branches.
- `git show commit` Mostra as informaçãoes do commit.
- `git add` Adiciona arquivos para o estado de staged.
- `git commit` Guarda uma versão para o repositório.
- `git commit --amend` Altera o último commit, tanto a mensagem de commit quanto a adição de arquivos.
- `git push` Envia os commits para um repositório remoto.
- `git diff` Apresenta as diferenças entre commits.
- `git diff HEAD~1` Mostra as diferenças da versão atual (HEAD) com a versão anterior.
- `git blame <arquivo>` Mostra as alterações feitas em um arquivo linha por linha. Mostra o autor e o commit onde foi feita aquela linha.

### 1.6.3. Histórico e Conflitos

- `git clone https://github.com/usuario/repositorio.git` Baixa o repositório remoto, serve como uma maneira alternativa de inicializar um repositório e já vem com o remote configurado.
- `git pull` Baixa as alterações do repositório remoto que não se encontram no repositório local. *mantem o repositório sincronizado com os ultimos commits de uma branch*.
- `git checkout <commit> --arquivo` Permite ver o estado de um arquivo ou todo o diretório em um determinado commit.
- `git checkout --arquivo` Ignora as mudanças feitas no arquivo *que não estejam em staged*.
- `git checkout HEAD --arquivo` Desfaz todas as alterações até o ultimo commit *incluindo os arquivos em staged*.
- `git revert <commit>` Cria um novo commit desfazendo as alterações de um commit específico.
- `git reset` Reseta o repositório para um determinado commit (por padrão, usa-se --soft).
  - `git reset --soft` Ignora o commit, mas as modificações no arquivo continuarão e o mesmo se encontra no estado de staged.
  - `git reset --mixed` Ignora o commit, mas o arquivo estará no estado de modified
  - `git reset --hard` Ignora tudo no commit.

### 1.6.4. Branching, Merge e Rebase
  
- `git branch` Lista todas as branches.
- `git branch <nome>` Cria uma nova branch.
- `git branch -d <nome>` Remove uma branch.
- `git checkout <branch>` Altera para uma branch.
- `git merge <branch>` Faz o merge entre as branches.
- `git rebase <branch>` Faz o rebase entre as branches.
- `git fetch` Faz o fetch no repositório.
- `git tag [nome tag]` Cria uma tag.
- `git push <remoto> <tag>` Envia a tag para o repositório remoto.
- `git fetch origin pull/<ID>/head:<branch>` faz o checkout de um PullRequest.
- `git stash` Guarda as alterações do _Working Directory_. Permite fazer o rebase, marge e trocar de branch sem a necessidade de fazer um commit.
- `git stash list` Lista os stashes.
- `git stash pop` Aplica o último stash.
- `git cherrypick <commit>` Aplica as alteraçlões de um commit na branch atual.

### 1.6.5. .gitignore

- Configura os arquivos que devem ser ignorados.
- Contém arquivos, caminhos e patterns.
  - `.project, .jar, .zip` Ignora arquivos com uma determinada extenção.
  - `.[jw]ar` Usa uma expressão regular para ignorar arquivos de uma determinada extenção.
  - `dist/` Ignora diretórios.
  - `**/log/` Ignora qualquer diretório que tenha um subdiretório semenhante ao específicado.
  - `**/*.css` Ignora qualquer caminho que termina com um arquivo de uma determinada.