💬 Chat Laravel

Projeto de um sistema de chat em tempo real desenvolvido com Laravel, utilizando Laravel Breeze para autenticação e Pusher + Laravel Echo para comunicação em tempo real.

🚀 Tecnologias utilizadas

- PHP
- Laravel
- Laravel Breeze
- Blade
- JavaScript
- Vite
- Laravel Echo
- Pusher
- MySQL (ou outro banco configurado no ".env")

📌 Funcionalidades

Atualmente, o projeto possui:

- Cadastro de usuários
- Login e logout
- Autenticação de usuários
- Página protegida de chat
- Envio de mensagens
- Comunicação em tempo real utilizando Pusher
- Laravel Echo para receber eventos no navegador

📁 Estrutura principal

app/
├── Events/
│   └── MessageSent.php
│
├── Http/
│   └── Controllers/
│       └── ChatController.php

resources/
├── js/
│   ├── app.js
│   └── bootstrap.js
│
└── views/
    └── chat.blade.php

routes/
└── web.php

⚙️ Instalação

1. Clonar ou abrir o projeto

Entre na pasta do projeto:

cd nome-do-projeto

2. Instalar as dependências PHP

composer install

3. Instalar as dependências JavaScript

npm install

4. Criar o arquivo ".env"

Caso o arquivo ".env" não exista:

cp .env.example .env

No Windows, também é possível simplesmente copiar ".env.example" e renomeá-lo para ".env".

5. Gerar a chave da aplicação

php artisan key:generate

🗄️ Configuração do banco de dados

Configure as informações do banco no arquivo ".env".

Exemplo:

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=nome_do_banco
DB_USERNAME=root
DB_PASSWORD=

Depois execute:

php artisan migrate

📡 Configuração do Pusher

O projeto utiliza o Pusher para transmitir as mensagens em tempo real.

No ".env", configure:

BROADCAST_CONNECTION=pusher

PUSHER_APP_ID=SEU_APP_ID
PUSHER_APP_KEY=SUA_APP_KEY
PUSHER_APP_SECRET=SEU_APP_SECRET
PUSHER_HOST=
PUSHER_PORT=443
PUSHER_SCHEME=https
PUSHER_APP_CLUSTER=SEU_CLUSTER

VITE_PUSHER_APP_KEY="${PUSHER_APP_KEY}"
VITE_PUSHER_APP_CLUSTER="${PUSHER_APP_CLUSTER}"

Substitua os valores pelos dados fornecidos pelo Pusher.

📦 Dependências do chat

As bibliotecas utilizadas no frontend são:

npm install laravel-echo pusher-js

O Laravel Echo é responsável por escutar os eventos enviados pelo servidor, enquanto o Pusher realiza a comunicação em tempo real.

▶️ Como executar o projeto

É necessário executar o Laravel e o Vite.

Terminal 1 — Laravel

Na pasta do projeto:

php artisan serve

O projeto ficará disponível normalmente em:

http://127.0.0.1:8000

Terminal 2 — Vite

Em outro terminal:

npm run dev

Mantenha esse terminal aberto enquanto estiver desenvolvendo.

Terminal 3 — Fila

Como o projeto utiliza:

QUEUE_CONNECTION=database

os eventos podem ser processados pela fila.

Execute:

php artisan queue:work

Mantenha esse terminal aberto durante os testes do chat.

🔐 Acessando o sistema

Depois de iniciar o projeto, acesse:

http://127.0.0.1:8000

Crie uma conta ou faça login.

A página do chat está disponível em:

http://127.0.0.1:8000/chat

A rota do chat exige autenticação.

📨 Funcionamento das mensagens

Quando uma mensagem é enviada:

Usuário
   ↓
Página do Chat
   ↓
POST /chat/send
   ↓
Laravel
   ↓
MessageSent
   ↓
Fila
   ↓
Pusher
   ↓
Laravel Echo
   ↓
Outros usuários conectados

O evento responsável pela transmissão é:

app/Events/MessageSent.php

O canal utilizado atualmente é:

chat

E o frontend escuta o evento:

MessageSent

🧹 Limpar configurações

Se alguma alteração no ".env" não estiver sendo reconhecida, execute:

php artisan config:clear

Também pode ser utilizado:

php artisan cache:clear

Depois reinicie o Vite:

npm run dev

🛠️ Comandos úteis

Iniciar servidor Laravel:

php artisan serve

Iniciar Vite:

npm run dev

Iniciar fila:

php artisan queue:work

Limpar configuração:

php artisan config:clear

Limpar cache:

php artisan cache:clear

Executar migrations:

php artisan migrate

Criar um evento:

php artisan make:event NomeDoEvento

Criar um controller:

php artisan make:controller NomeDoController

📋 Estado atual do projeto

O projeto já possui a estrutura básica de autenticação e chat em tempo real.

Concluído

- [x] Laravel configurado
- [x] Laravel Breeze instalado
- [x] Login
- [x] Cadastro
- [x] Autenticação
- [x] Página do chat
- [x] Pusher configurado
- [x] Laravel Echo configurado
- [x] Evento "MessageSent"
- [x] Rota "/chat"
- [x] Rota "/chat/send"

Próximos passos

- [ ] Salvar mensagens no banco de dados
- [ ] Exibir histórico de mensagens
- [ ] Identificar o usuário que enviou cada mensagem
- [ ] Criar conversas privadas
- [ ] Criar lista de usuários
- [ ] Melhorar a interface do chat
- [ ] Adicionar status online/offline
- [ ] Adicionar notificações
- [ ] Criar salas de conversa

👨‍💻 Desenvolvimento

Este projeto está sendo desenvolvido como um sistema de chat utilizando Laravel e tecnologias de comunicação em tempo real.

Para iniciar o ambiente de desenvolvimento, normalmente são necessários três terminais:

Terminal 1 → php artisan serve
Terminal 2 → npm run dev
Terminal 3 → php artisan queue:work

Com os três processos funcionando, acesse:

http://127.0.0.1:8000/chat
