#Guias 
# Como Resolver o Erro de Execução de Scripts no PowerShell

## Problema

Ao tentar executar qualquer script no PowerShell, você pode se deparar com o seguinte erro:

```
<nome_do_script>.ps1 não pode ser carregado porque a execução de scripts foi desabilitada neste sistema.
```

Esse erro acontece porque o PowerShell está configurado para **bloquear a execução de scripts por padrão**.

---

## Solução

### 1️⃣ Abra o PowerShell como Administrador

- No menu iniciar, procure por **PowerShell**.
- Clique com o botão direito e selecione **Executar como administrador**.

---

### 2️⃣ Altere a Política de Execução

Digite o seguinte comando no PowerShell:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

---

### 3️⃣ Confirme a Alteração

Quando o PowerShell perguntar se deseja alterar a política, digite:

```
S
```

(e pressione **Enter**) para confirmar.

---

### 4️⃣ Execute o Script

Agora você pode executar qualquer script `.ps1` normalmente:

```powershell
.\seu_script.ps1
```

---

## 🔄 Como Reverter a Política de Execução

Se quiser voltar ao padrão de segurança mais restritivo, execute:

```powershell
Set-ExecutionPolicy Restricted
```

---

## ℹ️ O que significa `RemoteSigned`?

- **RemoteSigned** permite executar scripts locais sem assinatura.
- Scripts baixados da internet exigirão assinatura.
- É recomendado para **desenvolvimento local**.

---

## Outras Políticas de Execução

| Política          | Descrição                                           |
|------------------|-----------------------------------------------------|
| **Restricted**    | Não permite a execução de scripts. (padrão)         |
| **AllSigned**     | Todos os scripts precisam ser assinados digitalmente|
| **RemoteSigned**  | Scripts locais não precisam de assinatura           |
| **Unrestricted**  | Todos os scripts podem ser executados sem restrições|

---

## Links úteis

- [Documentação oficial do PowerShell - Execution Policies](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies)
