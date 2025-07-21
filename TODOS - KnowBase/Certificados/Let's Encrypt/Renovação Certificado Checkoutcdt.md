#Guias 
# Renovação de Certificado SSL (PFX) - App Service `checkoutcdt`

## Descrição
Este documento descreve o processo de renovação do certificado SSL (PFX) utilizado no App Service **checkoutcdt** no Azure.

---

## Passo a Passo

### 1. Acessar a VM responsável pela geração do certificado:

```bash
ssh titodos@192.168.254.43
```
Senha: **(inserir senha)**

![[Pasted image 20250715150809.png]]

---
### 2. Elevar privilégios:

```bash
sudo su
```
Senha: **(inserir senha)**

![[Pasted image 20250715150901.png]]

---
### 3. Verificar certificado próximo do vencimento no App Service

- Acesse o Azure e navegue até o App Service **[checkoutcdt - Microsoft Azure](https://portal.azure.com/#@cartaodetodos.com/resource/subscriptions/440a9868-153b-451a-899b-8fb121e26f1d/resourceGroups/gotcha/providers/Microsoft.Web/sites/checkoutcdt/certificatesReact)**
- No menu **Certificates**, confira qual certificado está próximo do vencimento.


![[Pasted image 20250715150933.png]]

> **Observação:** Os certificados destacados como "vencidos" e referentes a times descontinuados **não precisam de ação**.

![[Pasted image 20250715151028.png]]

---

### 4. Solicitar novo certificado via Certbot:

```bash
certbot certonly --manual --email infraestrutura@cartaodetodos.com --domains vendas.cartaodetodosnautico.com.br
```
Substitua o domínio se necessário.

![[Pasted image 20250715171009.png]]

---

### 5. Gerar arquivo `.well-known`

- O Certbot irá gerar um código **acme-challenge**.

![[Pasted image 20250715171044.png]]

- Crie um arquivo **sem extensão** no Notepad++ com esse código.
- Nome do arquivo: **última parte da URL gerada após `/acme-challenge/`**.

![[Pasted image 20250715171214.png]]

- Exemplo

![[Pasted image 20250715171245.png]]

---

### 6. Acessar o SFTP do App Service

- No Azure, baixe o **Publish Profile** do App Service `checkoutcdt` (contém as credenciais SFTP).

![[Pasted image 20250715171317.png]]

---

### 7. Conectar via Filezilla ou similar

- Utilize as credenciais do **Publish Profile**.

![[Pasted image 20250715171336.png]]

---

### 8. Navegar até o diretório:

```
/site/wwwroot/.well-known/acme-challenge
```
- Cole o arquivo gerado no passo 5.

![[Pasted image 20250715171409.png]]

---

### 9. Voltar para a VM e pressionar `Enter` no Certbot

- O Certbot irá validar o arquivo.

![[Pasted image 20250715171435.png]]

---

### 10. Após a validação, a mensagem de sucesso será exibida.

![[Pasted image 20250715171453.png]]

---

### 11. Navegar até o diretório dos certificados:

```bash
cd /etc/letsencrypt/live/vendas.cartaodetodosnautico.com.br
```

![[Pasted image 20250715171513.png]]

---

### 12. Remover o certificado antigo:

```bash
rm certificado.pfx
```

---

### 13. Criar novo arquivo PFX:

```bash
openssl pkcs12 -export -out certificado.pfx -inkey privkey.pem -in fullchain.pem
```

![[Pasted image 20250715171543.png]]

---

### 14. Definir a senha do certificado.

- Crie uma senha

![[Pasted image 20250715171629.png]]
- Confirmar a senha

![[Pasted image 20250715171725.png]]

> **Importante:** Memorizar a senha criada, pois será usada no Azure.

---

### 15. Copiar o certificado gerado para a pasta Home:

```bash
cp certificado.pfx /home/certificados/nautico/certificado.pfx
```

![[Pasted image 20250715171808.png]]

> **Atenção:** Altere o nome da pasta caso o time não seja o Nautico.

---

### 16. Ajustar permissões:

```bash
chmod 777 /home/certificados/nautico/certificado.pfx
```

![[Pasted image 20250715171829.png]]

---

### 17. Transferir o certificado para a máquina local:

No **PowerShell**:

```powershell
scp titodos@192.168.254.43:/home/certificados/nautico/certificado.pfx C:/comum
```
Senha da VM será solicitada.

![[Pasted image 20250715171903.png]]

> **Observação:** Se necessário, altere o caminho `C:/comum`.

![[Pasted image 20250715171922.png]]

![[Pasted image 20250715171938.png]]

---

### 18. Acessar o Azure e ir para o menu **Certificates** do App Service `checkoutcdt`

- Clique em **Bring Your Own Certificate**.

![[Pasted image 20250715172008.png]]

---

### 19. Adicionar o certificado:

- Clique em **Add Certificate**.
- Selecione o arquivo **PFX** gerado.

![[Pasted image 20250715172037.png]]

- Insira a senha criada no passo 14.

![[Pasted image 20250715172215.png]]

- Clique em **Validate** e depois em **Add**.

![[Pasted image 20250715172225.png]]

---

### 20. Atualizar o binding no App Service

- Acesse o menu **Custom Domains**.
- Filtre pelo domínio do time.
- Clique em **Update Binding** (Ou nos 3 pontinhos em Actions).

![[Pasted image 20250715172247.png]]

---

### 21. Selecionar o novo certificado

- Verifique a validade do certificado (deve ser de 3 meses).

![[Pasted image 20250715172353.png]]

- Marque a opção **SNI/SSL** e 

![[Pasted image 20250715172512.png]]

- Clique em **Update**.

![[Pasted image 20250715172502.png]]

---

### 22. Confirmar se o domínio está como **Secured**

![[Pasted image 20250715172532.png]]

---

### 23. Remover o certificado antigo:

- Vá novamente em **Bring Your Own Certificate**.
- Localize o certificado antigo e clique em **Delete**.

![[Pasted image 20250715172548.png]]

---

### 24. Processo finalizado.

---

## Observação

Repita o processo para cada certificado prestes a expirar.

> **Importante:** Atenção às datas de vencimento de cada certificado.

---
