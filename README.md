# 🚀 API UberVan

API desenvolvida em Node.js usando Express e hospedada na Vercel. A API possui dois endpoints principais:

Um endpoint básico de Hello World.
Um endpoint que utiliza o SDK Admin do Firebase para alteração de senhas.

## 🗂️ Estrutura do Projeto

```plaintext
Copiar código
APIVAN/
├── api/
│ └── index.ts # Configuração do servidor na Vercel
├── public/
│ └── .gitkeep # Diretório público (para arquivos estáticos, se necessário)
├── src/
│ ├── api/
│ │ ├── emojis.ts # Arquivo de exemplo com emojis (Hello World)
│ │ ├── index.ts # Configuração principal dos endpoints
│ ├── interfaces/ # Tipagens do projeto
│ │ ├── app.ts
│ │ ├── index.ts
│ ├── middlewares.ts # Middlewares personalizados
├── test/ # Arquivos de configuração e testes
├── .env.sample # Exemplo do arquivo de variáveis de ambiente
├── vercel.json # Configuração do deploy na Vercel
```

## 🛠️ Endpoints

### 1. Hello World

URL: /
Método: GET
Descrição: Endpoint básico que retorna uma mensagem de boas-vindas.
Resposta:
json
Copiar código
{
"message": "Hello World!"
}

### 2. Alteração de Senha do Usuário

URL: /api/update-password
Método: POST
Descrição: Endpoint que utiliza o Firebase Admin SDK para alterar a senha de um usuário específico.
Autenticação: Nenhuma (depende de como você configurou a API para acesso interno ou protegido por chave).
Corpo da Requisição
Envie um JSON com os seguintes campos:

```json
{
  "idToken": "id_do_usuario",
  "password": "nova_senha"
}


Exemplo de Requisição
bash
Copiar código
POST /api/update-password HTTP/1.1
Host: suaprojetohospedado.vercel.app
Content-Type: application/json

{
"userId": "user123",
"newPassword": "novaSenha123!"
}

Resposta de Sucesso
{
"success": true,
"message": "Senha alterada com sucesso para o usuário user123."
}

Resposta de Erro
{
"success": false,
"error": "Usuário não encontrado ou erro ao alterar a senha."
}
```

## 🚀 Hospedagem e Testes

### Hospedagem

A API está hospedada na Vercel, facilitando deploys rápidos e integrações contínuas. O arquivo vercel.json contém as configurações necessárias.

### Testes com Postman

Todos os endpoints foram testados utilizando o Postman.
Para reproduzir os testes:
Execute as requisições simulando diferentes cenários (sucesso/erro).

## 🔧 Configuração do Firebase

### A integração com o Firebase Admin SDK exige:

Um arquivo de credenciais do serviço (serviceAccountKey.json).
