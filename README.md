# Curso de git
****
## Principais Conceitos

- **Commit:** Realiza uma mudança no projeto; mais específicamente, armazena uma mudança no banco de dados de uma forma que possa ser incorporada em versões futuras.
- **Update:** Solicitar que as mudança dos demais commits sejam incorporadas em sua cópia local do projeto. 
- **Branch (Ramo):** Uma cópia do projeto, porém isolada de uma maneira que as mudanças realizadas no branch não afetem o resto do projeto e vice-versa, *exceto quando as mudanças são delibaradamente mescladas*
- **Repositório:** Onde armazena-seo histórico do projeto.
- **Diretório de Trabalho:** É um diretório monitorado pelo controle de versão que contém os arquivos do projeto.
- **Configuração:** É o estado dos arquivos do projeto.
- **Revisão:** É uma configuração registrada no repositório.
- **Rastreabilidade:** É poder seguir o trajeto de uma solicitação de mudança desde que foi proposta até o momento que voi implementada.
- **Changeset:** Diferença entre duas configurações.
- **Versão:** Revisão usada em produção.

## Serviços Fundamentais

- Registro da evolução do projeto;
- Controle de concorrência;
- Variações do projeto.

> É uma das ferramentas mais importantes do desenvolvimento de software.

Serve para:
1. Manter hsitórico do projeto;
2. Controlar a concorrência de edição;
3. Manter váriações do projeto.

## Níveis de Configuração
- **Sistema:** É o mais abrangente vale para todos os usuários e repositórios, geralmente é usado em servidores de repositórios.
- **Global:** Vale para todos os repositórios do usuário, a configuração deste nível sobreescreve a configuração de sistemas.
- **Local:** É o mais específico e vale apenas para o repositório que está sendo usado, sobreescrevendo as configurações dos outros níveis. A configuração do nível local costuma ser gerada automaticamente durante a clonagem ou inicialização do repositório, geralmente contém o caminho original para o repositório que é usado na sincronização de repositórios e etc.

> - **Local:** `repositório/.git/config`
> - **Global:** `$HOME/.gitconfig`
> - **Local:** `/etc/gitconfig`

## Workflow
- Editar
- Commitar
- Sincronizar com o repositório

## Estados dos Arquivos
| Estado         | Stage     |
|:--------------:|:---------:|
| Não Monitorado | Untracked |
| Modificado     | Modifield |
| Preparado      | Staged    |
| Consolidado    | Commited  |