#Guias 
# Como Exportar E-mails para um PST no Microsoft 365

Este documento detalha o processo de exportação de e-mails para um arquivo **PST (Personal Storage Table)** diretamente pela **Central de Conformidade do Microsoft 365**, com base no procedimento demonstrado pela Ravel Tecnologia.

---

## 🛠️ Pré-requisitos

- Acesso ao **Painel de Administração do Microsoft 365**
- Utilizar o **navegador Edge** (recomendado para evitar problemas com o cliente de exportação)

---

## 📋 Passo a Passo

### 1️⃣ Acesso Inicial

1. Acesse o **Painel de Administração** do Microsoft 365.
2. Navegue até a **Central de Conformidade** (_Compliance Center/Microsoft Purview_).

### 2️⃣ Criar Pesquisa de Conteúdo

3. No menu lateral, selecione **Descoberta Eletrônica** 
4. Selecione **Pesquisa de Conteúdo** (_Content Search_).
5. Clique em **Criar uma Pesquisa** (_New Search_).

#### Definição da Pesquisa:

5. Insira um **nome** e uma **descrição** para a pesquisa.
6. Adicione uma fonte (Caixa de correio a realizar o backup)
7. Selecione as **Somente caixas de correio**.
8. Clique em **Salvar** 
9. _(Opcional)_ Adicione **condições de filtro** como:
   - Intervalo de datas
   - Remetente
   - Assunto

5. Clique em **Executar Consulta**.
6. Aguarde o status mudar para **Concluído** (_Completed_).

---

### 3️⃣ Exportar Resultados

10. Após a conclusão, clique em **Ações** (_Actions_) → **Exportar Resultados** (_Export Results_).

![[Pasted image 20250714162704.png]]

#### Opções de Exportação:

- **Exportar todos os itens** (ignorar erros eventuais).
- **Exportar para arquivo PST** (recomendado).

11. Clique em **Exportar** (_Export_).

---

### 4️⃣ Download do PST

12. Vá até a aba **Exportar** (_Export_) e acompanhe o status.
13. Quando o status estiver **Concluído**, copie a **Chave de Exportação**.

14. Clique em **Baixar Resultados** (_Download Results_).

#### Instalação do Cliente eDiscovery:

15. Se for a primeira vez, será necessário instalar o **eDiscovery Export Tool**.
   - **Importante:** Use o navegador **Edge**.

16. No aplicativo de exportação, cole a **chave copiada**.
17. Escolha o **local de salvamento** do arquivo PST (recomenda-se criar uma pasta específica).
18. Clique em **Iniciar** (_Start_) para baixar.

---

### 5️⃣ Finalização

19. Ao concluir, verifique se o status é **Concluído com êxito** (_Completed successfully_).
20. O arquivo será salvo em uma subpasta chamada **Export** com a data/hora da exportação.

#### Nome padrão do arquivo:

- **Exchange.pst**  
- Sugestão: renomeie para algo mais descritivo, ex: `backup_email_usuario.pst`

---

## 📌 Observações Finais

- O arquivo PST pode ser:
   - Armazenado em nuvem.
   - Importado em outro cliente **Outlook** para consulta.
- Outros arquivos da pasta de exportação são apenas para controle da Microsoft e podem ser ignorados para uso no Outlook.
- Após concluir, feche todas as telas de exportação.

---

## 🔗 Referências

- Vídeo da Ravel Tecnologia sobre exportação de PST
- Documentação oficial da Microsoft sobre [Exportação com eDiscovery](https://learn.microsoft.com/pt-br/microsoft-365/compliance/export-search-results?view=o365-worldwide)

