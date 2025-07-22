#Guias 
# 🧾 Guia: Como Exportar o Certificado do Kaspersky no macOS

Este guia mostra como exportar o certificado raiz usado pelo Kaspersky para interceptação SSL, de modo que ele possa ser confiavelmente utilizado com ferramentas como o AWS CLI no macOS.

---

## ✅ Objetivo

Exportar o certificado raiz da autoridade intermediária criada pelo Kaspersky para inspeção HTTPS, e usá-lo com a variável de ambiente `REQUESTS_CA_BUNDLE`.

---

## 🔹 Método 1: Exportar via Navegador (Google Chrome ou Firefox)

### 🔸 Passo a Passo:

1. **Abra o navegador (Chrome ou Firefox)**

2. Acesse um site que passe por interceptação do Kaspersky (por exemplo):
   ```
   https://sts.amazonaws.com
   ```

3. Clique no **cadeado 🔒** na barra de endereços → **"Certificado (válido)"** → **"Detalhes"**.

4. Vá até a aba **"Cadeia de Certificação"**.

5. Selecione o **primeiro ou último item da cadeia**, geralmente com nome como:
   ```
   Kaspersky Security Center Root Certificate
   ```

6. Clique em **"Exportar"** (ou "Salvar como", dependendo do navegador).

7. Salve o arquivo como:
   ```
   kaspersky-ca.pem
   ```

8. Mova o certificado para um local seguro:
   ```bash
   mkdir -p ~/Documents/certs
   mv ~/Downloads/kaspersky-ca.pem ~/Documents/certs/kaspersky-ca.pem
   ```

---

## 🔹 Método 2: Exportar via chaveiro do macOS (Keychain Access)

1. Abra o **Acesso às Chaves** (`Keychain Access`) pelo Spotlight (`Cmd + Espaço`).

2. Vá em:
   ```
   Sistema → Certificados
   ```

3. Localize o certificado com nome relacionado a **Kaspersky**.

4. Clique com o botão direito e selecione **"Exportar"**.

5. Escolha o formato **.pem** ou **.cer**, e depois converta:

   ```bash
   openssl x509 -in arquivo.cer -inform DER -out kaspersky-ca.pem
   ```

---

## 🧪 Validação do certificado exportado

Depois de exportar, valide com:

```bash
openssl x509 -in ~/Documents/certs/kaspersky-ca.pem -text -noout
```

Você deve ver o nome "Kaspersky" no campo `Issuer` ou `Subject`.

---

## 🧠 Dica

Use o certificado `.pem` exportado para configurar a variável `REQUESTS_CA_BUNDLE`, como mostrado no guia principal.

---

## ✅ Resultado esperado

Você terá um arquivo em:

```
~/Documents/certs/kaspersky-ca.pem
```

Pronto para ser usado com ferramentas Python e AWS CLI.

---
