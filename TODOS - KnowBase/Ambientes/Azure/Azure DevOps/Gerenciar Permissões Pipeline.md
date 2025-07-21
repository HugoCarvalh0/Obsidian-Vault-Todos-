#Guias
# 🔐 Guia: Gerenciar Permissões de Pipeline no Azure DevOps

## 📌 Objetivo
Este guia tem como objetivo ensinar como visualizar e gerenciar as permissões de um pipeline no Azure DevOps, garantindo segurança e controle sobre quem pode executar, editar ou excluir pipelines.


---
## 📁 1. Acessar o Projeto no Azure DevOps

1. Acesse: https://dev.azure.com
2. Selecione a **Organização** e o **Projeto** desejado.
3. Vá até o menu lateral e clique em `Pipelines > Pipelines`.

---

## 🔎 2. Selecionar o Pipeline

1. Localize o pipeline que deseja configurar.
2. Clique nos `três pontinhos (⋯)` ao lado do nome do pipeline.
3. Selecione **Segurança**.

---

## 🛡️ 3. Gerenciar Permissões

Na tela de permissões, você verá uma lista de usuários e grupos com permissões no pipeline.

### 🔄 Permissões Comuns
| Permissão             | Descrição                                        |
| --------------------- | ------------------------------------------------ |
| View builds           | Ver execuções passadas do pipeline               |
| Edit build pipeline   | Editar configurações e YAML do pipeline          |
| Delete build pipeline | Excluir o pipeline                               |
| Queue builds          | Disparar novas execuções do pipeline             |
| Manage build queue    | Cancelar execuções em andamento                  |
| Retain indefinitely   | Manter execuções específicas indefinidamente     |
| Manage permissions    | Gerenciar permissões de outros usuários e grupos |

### 🧑‍🤝‍🧑 Recomendações
- **Desenvolvedores**: `View builds`, `Queue builds`
- **Administradores de DevOps**: todas as permissões
- **Stakeholders**: apenas `View builds`

---

## 🧩 4. Adicionar Usuários ou Grupos

1. Clique em **Add**.
2. Digite o nome do usuário ou grupo (ex: `Project Contributors` ou `username@empresa.com`).
3. Clique em **Add** novamente para confirmar.
4. Após adicionar, configure as permissões desejadas.

---

## 📋 5. Herança de Permissões

Os pipelines herdam permissões do projeto e do repositório Git vinculado. Para controle mais granular:

- Vá até `Project settings > Repositories`
- Escolha o repositório
- Acesse `Security` para ajustar permissões gerais do repositório

---

## 🔄 6. Auditoria de Permissões

Para verificar se um usuário tem ou não permissão:

1. No painel de segurança do pipeline, clique em **Check access**.
2. Digite o nome do usuário.
3. O Azure DevOps exibirá o resumo das permissões efetivas (herdadas ou diretas).

---

## 🧠 Dicas Finais

- Use **Grupos** sempre que possível para facilitar o gerenciamento.
- Evite dar permissões elevadas diretamente a usuários individuais.
- Documente as permissões concedidas e revise periodicamente.
- Cuidado com a permissão **Manage permissions**, pois ela permite controle total.

---

## 📚 Referências Oficiais

- [Gerenciar permissões de pipelines - Microsoft Docs](https://learn.microsoft.com/azure/devops/pipelines/security/permissions)
- [Permissões e grupos no Azure DevOps](https://learn.microsoft.com/azure/devops/organizations/security/permissions)

---


