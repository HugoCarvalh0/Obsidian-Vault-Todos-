#Guias 
# 🛠️ Guia: Corrigir erro de SSL no AWS CLI com Kaspersky no macOS

Este guia mostra como configurar o AWS CLI no macOS para funcionar corretamente mesmo com antivírus Kaspersky interceptando conexões HTTPS, evitando o erro:

```
SSL validation failed for https://sts.us-east-1.amazonaws.com/ [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed: self-signed certificate in certificate chain (_ssl.c:1028)
```

---

## ✅ Objetivo

Configurar a variável de ambiente `REQUESTS_CA_BUNDLE` com o caminho para o certificado `.pem` do Kaspersky, tornando o uso do `awscli` funcional e seguro.

---

## 🔹 Pré-requisito

Você deve ter o certificado do Kaspersky salvo em um caminho acessível pelo seu usuário. 

[[Exportar Certificado Kaspersky]]

Exemplo usado neste guia:
```bash
/Users/Matheus/Documents/certs/kaspersky-ca.pem
```

---

## 🔸 Passo a Passo

### 1. Abra o terminal

Use o Spotlight (`Cmd + Espaço`) e procure por “Terminal”.

---

### 2. Verifique se o certificado está acessível

Rode:

```bash
ls /Users/Matheus/Documents/certs/kaspersky-ca.pem
```

Se o caminho estiver correto, o arquivo será exibido.

---

### 3. Edite o arquivo de configuração do shell

#### Se estiver usando Zsh (padrão no macOS moderno):

```bash
nano ~/.zshrc
```

#### (ou para usuários Bash):

```bash
nano ~/.bash_profile
```

---

### 4. Adicione a variável `REQUESTS_CA_BUNDLE`

No final do arquivo aberto, adicione a linha:

```bash
export REQUESTS_CA_BUNDLE=/Users/Matheus/Documents/certs/kaspersky-ca.pem
```

---

### 5. Salve e feche o arquivo

- Pressione `Control + O` → depois `Enter` para salvar
- Pressione `Control + X` para sair

---

### 6. Aplique a configuração imediatamente

Rode o comando abaixo para carregar a configuração na sessão atual:

```bash
source ~/.zshrc
```

_(ou `source ~/.bash_profile` para bash)_

---

### 7. Verifique se a variável está ativa

Rode:

```bash
echo $REQUESTS_CA_BUNDLE
```

A saída deve ser:

```
/Users/Matheus/Documents/certs/kaspersky-ca.pem
```

---

### 8. Teste o AWS CLI

Rode:

```bash
aws sts get-caller-identity
```

✅ Se não houver erro de SSL, a configuração está funcionando corretamente!

---

## ℹ️ Observações

- Esta configuração é **permanente para o seu usuário**.
- Ela será carregada automaticamente toda vez que o terminal for iniciado.
- Se você mudar o local do arquivo `.pem`, atualize o caminho no `~/.zshrc`.

---

## 🧪 Dica Extra: Validar o certificado

Para inspecionar o conteúdo do `.pem` e confirmar que está correto:

```bash
openssl x509 -in /Users/Matheus/Documents/certs/kaspersky-ca.pem -text -noout
```

---

## 🧠 Conclusão

Você configurou corretamente o ambiente para que o AWS CLI funcione em um sistema com inspeção HTTPS ativa via Kaspersky. Com isso, conexões seguras são aceitas sem abrir mão da segurança SSL.

---
