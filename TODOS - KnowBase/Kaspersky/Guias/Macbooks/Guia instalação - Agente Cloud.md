
#### 1- Baixar o arquivo _klnagentmac.sh_. 
![[Pasted image 20250717173754.png]]

#### 2- Copiar o arquivo _klnagentmac.sh_ para a pasta publica do usuário titodos
- Para abrir a pasta de usuários (win/cmd + espaço -> pesquisar "**Users**").
	![[Pasted image 20250717173848.png]]
- Acessar pasta _titodos_
	![[Pasted image 20250717174023.png]]
- Acessar a pasta Pública
	![[Pasted image 20250717174053.png]]
- Colar o arquivo
	![[Pasted image 20250717174118.png]]
- Após isso pode fechar a pasta
#### 3- Abrir o terminal
- (win/cmd + espaço -> pesquisar "**Terminal**")
	![[Pasted image 20250717174414.png]]


#### 4- Navegar até a pasta Pública do usuário titodos
- Comandos:
	- cd ..
	- cd titodos/
	- cd Public/

#### 5- Executar o instalador
- Comandos:
	- su titodos
		_senha do usuário admin da máquina_
	- sudo chmod +x klnagentmac.sh
	- sudo ./klnagentmac.sh

Finalizado