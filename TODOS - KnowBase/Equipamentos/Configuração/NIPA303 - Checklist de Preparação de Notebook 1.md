#Guias 
# Checklist de Preparação de Notebook - Colaboradores

Os procedimentos descritos abaixo seguem o padrão de preparação de notebooks da empresa, visando segurança e eficiência.

## 1. Procedimento para Máquinas Windows

### 1.1. Formatação e Configuração de Senha no Setup
- [x] Configurar senha de administrador na BIOS/UEFI
- [x] Realizar formatação completa do sistema se for equipamento já utilizado

### 1.2. Definição e Registro do Nome da Máquina
- [ ] Conferir número de série na planilha de controle
    - [ ] Se já registrado, usar o nome correspondente
    - [ ] Se não registrado, criar novo nome no padrão NIPA00
- [ ] Alterar o nome da máquina no sistema operacional

### 1.3. Etiquetagem do Notebook e Carregador
- [x] Colar etiquetas com o nome da máquina no notebook e carregador

### 1.4. Inserção no Domínio
- [x] Adicionar a máquina no domínio todos.net  
  Caminho: Configurações > Sistema > Sobre > Domínio ou grupo de trabalho
### 1.5. Ingressar no Domínio com Usuário da Rede
- [x] Fazer login com um usuário de rede para acessar os instaladores

### 1.6. Ativação do BitLocker
- [x] Mover o notebook da unidade "Computers" para "OU Bitlocker\note-bitlocker"
- [x] Rodar o comando: `gpupdate /force`
- [x] Verificar ativação do BitLocker e chave salva no AD
- [x] Mover o notebook da OU "note-bitlocker" para a unidade "Computadores" do TI

### 1.7. Ativação da Descoberta de Rede
- [x] Ativar a descoberta de rede:
    - [x] Configurações > Rede e Internet > Configurações Avançadas de Rede > Configurações de Compartilhamento Avançadas
    - [x] Ativar descoberta de rede e compartilhamento de arquivos e impressoras

### 1.8. Desativação da Experiência de Usuário
- [x] Desativar o serviço "Experiências do Usuário Conectado e Telemetria" via `services.msc`

### 1.9. Instalação do Antivírus e Agente de Gerenciamento
- [ ] Acessar a pasta de instaladores da TI
- [ ] Instalar antivírus corporativo
- [ ] Instalar agente de gerenciamento
- [ ] Verificar comunicação com o servidor

### 1.10. Instalação da VPN
- [x] Instalar o OpenVPN com túneis 1193 e 1194

### 1.11. Configuração da Pasta HOME
- [x] Copiar a pasta HOME da rede para `C:\HOME`
- [x] Manter apenas:
    - [x] Script de mapeamento de unidade de rede
    - [x] Script de conexão Wi-Fi externa

### 1.12. Instalação de Aplicativos Padrões
- [ ] Instalar os seguintes aplicativos:
    - [x] AnyDesk
    - [x] Google Chrome
    - [x] Microsoft Teams (College and Work)
    - [x] Pacote Office

### 1.13. Instalação de Aplicativos para Equipe de Tecnologia (se aplicável)
- [ ] Instalar:
    - [ ] Visual Studio Code (VSCode)
    - [ ] SQL Server Management Studio (SSMS)

### 1.14. Atualização da Planilha “CONTROLE_ESTOQUE_ATIVOS_TI”
- [ ] Preencher os seguintes campos:
    - [ ] NOME DA MÁQUINA (NIPA)
    - [ ] ATRIBUÍDO A
    - [ ] SETOR ATUAL
    - [ ] MODALIDADE
    - [ ] ATRIBUIÇÃO ANTERIOR
    - [ ] SETOR ANTERIOR
    - [ ] REGIME DE TRABALHO ANTERIOR
    - [ ] Nº DE SÉRIE
    - [ ] PROCESSADOR
    - [ ] MEMÓRIA RAM

### 1.15. Criação de Usuário Admin de Backup (Suporte)
- [ ] Criar usuário local: `Suporte`
- [ ] Definir senha forte e segura
- [ ] Atualizar a planilha "usuarios-equipamentos" com:
    - [ ] HOSTNAME
    - [ ] USUÁRIO de Segurança
    - [ ] SENHA
    - [ ] RESPONSÁVEL
    - [ ] USER Local (se aplicável)
    - [ ] SETOR
- [ ] Marcar "Senha nunca expira"

### 1.16. Criação de Usuário Local para Home Office (se aplicável)
- [ ] Criar usuário local com primeiro nome do colaborador (Primeira letra maiúscula)
- [ ] Definir senha padrão temporária
- [ ] Orientar o colaborador sobre primeiro login e troca de senha

### 1.17. Configurações de Comunicação para Home Office (se aplicável)
- [ ] Executar o script "Altera Server" na pasta HOME
- [ ] Verificar comunicação com servidor externo via painel do antivírus

### 1.18. Atualização do Notion
- [ ] Atualizar o quadro Kanban do Notion com:
    - [ ] NIPA
    - [ ] Número de Série
    - [ ] Outras informações relevantes

### 1.19. Verificação e Atualização do Windows
- [ ] Acessar: Configurações > Windows Update
- [ ] Verificar e instalar atualizações disponíveis
- [ ] Reiniciar o notebook se necessário

---

> **Observação:** Marque cada etapa concluída para garantir a conformidade do processo.


