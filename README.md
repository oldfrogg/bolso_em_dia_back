# API BOLSO EM DIA

A API a seguir é uma uma API RESTful desenvolvida para cumprimento de um projeto acadêmico para finalizar o Hackaton final da Pós Graduação da turma de Dev Foundations da FIAP, feita para gerenciar o BD do projeto Bolso em Dia.
O projeto foi desenvolvido utilizando Node.JS, Express e Sequelize.
Também há um Front End desenvolvido em React, que pode ser utilizado em conjunto com este Back End, que você pode encontrar clicando [Aqui](https://github.com/oldfrogg/bolso_em_dia_front).

---


## Pré-requisitos
- Node.JS 20.9.0 (Deve ser baixado e instalado)
- NPM (Já está incluso no Node.JS)
- MySQL Server 8.4.6 (Deve ser baixado e instalado)
- Express 5.2.1 (será instalado a partir do package.json)
- Sequelize 6.37.7 (será instalado a partir do package.json)
- Swagger-JSDoc 6.2.8 (será instalado a partir do package.json)
- Swagger-UI-Express 5.0.1 (será instalado a partir do package.json)

OBS: Certifique-se de ter o Node.JS configurado nas variáveis de ambiente do sistema.

## Instalando o projeto

Lembrar de, a cada instalação que altere as variáveis de ambiente do sistema, reiniciar o terminal e/ou o editor.

### 1 - Instalando e configurando o MySQL Server
- Baixe o MySQL Server no [site oficial do MySQL](https://dev.mysql.com/downloads/), de acordo com seu Sistema Operacional, na versão completa (maior arquivo). Instale-o e configure-o, inclusive nas variáveis de ambiente do sistema.
Lembrar de deixar (ou inserir) porta 3306. 

IMPORTANTE! O usuário e senha aqui devem ser anotados, para uso nos próximos passos.

No CMD do Windows, caso precise parar o MySQL server, execute o comando:
```bash
net stop mysql84
```

Talvez seja necessário utilizar mysql80, a depender de sua versão instalada e SO.

No Linux, usando o systemctl:
```bash
sudo systemctl stop mysql
```

No MacOS, usando o Homebrew:
```bash
brew services stop mysql
```

Para iniciar novamente, basta trocar o "stop" por "start".


### 2 - Clonando o repositório
- Caso tenha o git instalado e configurado nas variáveis de ambiente do sistema, clonar através do
```bash
git clone https://github.com/oldfrogg/bolso_em_dia_back
cd bolso_em_dia_back
```
- Também é possível fazer o download do projeto diretamente através do Github.

### 3 - Instalando as dependências
- Abrir o diretório do arquivo através do terminal e instalar as dependências necessárias:

```bash
npm install
```

### 4 - Criando o arquivo .env na raiz do projeto
- Abra o projeto no editor de sua preferência, e, na raiz do projeto, crie um arquivo ".env" e insira as variáveis de ambiente, conforme sua escolha:
```env
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=suasenha
DB_NAME=BOLSO_EM_DIA
DB_PORT=3306
PORT=3000
```

Atenção! O nome do BD deve ser exatamente "BOLSO_EM_DIA" (sem aspas), pois é o nome utilizado no comando SQL de criação do BD.
Atenção! Seu usuário e senha definidos aqui devem ser os mesmos criados no passo 1.

### 5 - Criando o BD
- No terminal, estando na raiz do projeto, execute o seguinte comando para criar o BD. Pode ser solicitada a senha criada anteriormente:
```bash
mysql -u root -p < ./database/db.sql
```

### 6 - Verificações no package.json
- Confirme se no "script" do package.json há o seguinte comando, caso não, insira-o:
    "start": "node src/app.js"

- Confirme se o "main" do package.json está o seguinte valor associado: "src/app.js". Caso não, altere-o.

### 7 - Executando a aplicação
- Execute o comando, para rodar a aplicação:
```
npm start
```

### 8 - Utilizando a API
- Após seguir todos os passos, já será possível utilizar a API, do modo de sua preferência. A recomendação do autor é utilizar a partir do Front End desenvolvido, relatado no início do Readme, onde terá uma interface gráfica e acesso a todos os comandos da API.

## Rotas

### AUTH
- /auth/login/ - POST - Fazer login na aplicação
- /auth/logout/ - POST- Fazer logout na aplicação

### USUARIOS
- /usuarios/criar/ - POST - Criar um usuário novo
- /usuarios/ - GET - Listar todos os usuários
- /usuarios/usuario/ - GET - Mostrar o usuário logado
- /usuarios/editar/ - PUT - Alterar dados do usuário logado
- /usuarios/deletar/ - DELETE- Deletar do cadastro o usuário logado

### CATEGORIAS
- /categorias/ - GET - Listar todas as categorias
- /categorias/:id/ - GET - Mostrar categoria a partir de seu id

### PERIODOS
- /periodos/criar/ - POST - Criar um período novo
- /periodos/meus_periodos/ - GET - Listar todos os períodos do usuário logado
- /periodos/atual/ - GET - Mostra dados do período atual do usuário logado
- /periodos/periodo/:id/ - GET - Mostra os dados de um período do usuário logado a partir do id do período

### TRANSACOES
- /transacoes/criar/ - POST - Cria uma transação nova do usuário logado
- /transacoes/transacao/:id/ - GET - Mostra a transação do usuário logado a partir do id da transação
- /transacoes/minhas_transacoes/ - GET - Mostra todas as transações do usuário logado
- /transacoes/periodo/:periodoId/ - GET - Mostra as transações do usuário logado em determinado período a partir do id do período
- /transacoes/editar/:id/ - PUT - Edita uma transação do usuário logado a partir do id da transação
- /transacoes/delete/:id/ - DELETE - Deleta a transação do usuário logado a partir do id da transação

## Autor
O projeto foi desenvolvido por Jhonatta Tavares.

## Licença

Licença MIT, portanto, é de livre uso, alteração e publicação.

