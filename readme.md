
# 💨 Turbo Brisa – Chatbot de Aluguel de Ventiladores

Sistema completo de atendimento inteligente via WhatsApp para automação do serviço de locação de ventiladores industriais e comerciais. Desenvolvido com **Node.js**, **React**, **MySQL** e **Docker**, integrado a um modelo de IA conversacional (GPT).

---

## 🚀 Visão Geral

O Turbo Brisa é um assistente digital especializado em aluguéis de ventiladores. Ele:
- Interage com clientes pelo WhatsApp
- Processa solicitações de locação
- Responde dúvidas sobre preços, modelos e disponibilidade
- Gerencia estoque e relatórios via painel administrativo moderno
- Permite configurar o comportamento da IA via prompt customizado

---

## 🛠️ Tecnologias Utilizadas

| Camada        | Tecnologia                          |
|---------------|-------------------------------------|
| Frontend      | React, TypeScript, Tailwind CSS     |
| Backend API   | Node.js + Express                   |
| Banco de Dados| MySQL                               |
| IA Conversacional | OpenAI GPT-4 ou Gemini (via API) |
| Mensagens     | WhatsApp Business API (Z-API, Twilio) |
| Contêineres   | Docker + Docker Compose             |

---

## 📁 Estrutura do Projeto

```
turbo-brisa/
├── frontend/              # React App (Chat + Admin)
│   ├── src/
│   ├── Dockerfile
│   └── ...
├── backend/               # API em Node.js
│   ├── src/
│   │   ├── routes/
│   │   ├── controllers/
│   │   ├── models/
│   │   └── services/
│   ├── .env
│   ├── Dockerfile
│   └── ...
├── sql/
│   └── init.sql           # Script inicial do banco
├── docker-compose.yml
└── README.md
```

---

## 🌐 Funcionalidades

### 🧠 Chatbot Inteligente
- Integração com IA (OpenAI GPT-4)
- Integração com WhatsApp via API
- Interações automatizadas com clientes

### ⚙️ Prompt Customizável
- Botão de configurações na interface
- Prompt inicial predefinido para aluguel
- Salvamento automático no navegador

### 📦 Inventário de Ventiladores
- Adição, edição e remoção de modelos
- Preço, descrição e status de disponibilidade
- Armazenado em MySQL e exibido no painel React

### 📈 Relatórios
- Número total de modelos cadastrados
- Lista de todos os ventiladores disponíveis
- Expansível para dashboards com gráficos

---

## 🖥️ Telas do Sistema

### 1. Tela de Chat
- Chat entre cliente e IA
- Prompt customizável (botão de engrenagem)
- Totalmente responsivo

### 2. Tela de Inventário
- Listagem de ventiladores
- Botão "Adicionar Novo"
- Modal para editar/deletar

### 3. Tela de Relatórios
- Total de modelos
- Lista de disponíveis
- Futuro: gráficos, relatórios CSV

### 4. Tela de Login Admin
- Proteção de rotas
- Campos de login
- Redirecionamento seguro

---

## 👥 Equipe Necessária para o Projeto

| Cargo                      | Responsabilidades                                           |
|----------------------------|-------------------------------------------------------------|
| Desenvolvedor Fullstack     | Implementação do backend (Node.js) e frontend (React)       |
| Engenheiro de DevOps        | Configuração de Docker, CI/CD, deploy e infraestrutura      |
| Designer UI/UX             | Prototipação, design responsivo e experiência do usuário    |
| Especialista em IA         | Configuração do modelo GPT, tuning de prompts, integração   |
| Especialista WhatsApp API  | Integração e manutenção do webhook e API do WhatsApp        |
| Analista de QA             | Testes manuais, automação, garantia de qualidade             |
| Gerente de Projeto         | Planejamento, coordenação da equipe e controle do cronograma|

---

## 📦 Docker Compose (multi-contêiner)

```yaml
version: '3.8'

services:
  frontend:
    build: ./frontend
    ports:
      - "3000:3000"
    depends_on:
      - backend

  backend:
    build: ./backend
    ports:
      - "4000:4000"
    env_file:
      - ./backend/.env
    depends_on:
      - db

  db:
    image: mysql:8.0
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: turbo_brisa
    volumes:
      - ./sql/init.sql:/docker-entrypoint-initdb.d/init.sql
    ports:
      - "3306:3306"

  adminer:
    image: adminer
    restart: always
    ports:
      - "8080:8080"
```

---

## 📊 API – Endpoints Principais

| Método | Endpoint                 | Função                                 |
|--------|--------------------------|----------------------------------------|
| GET    | /api/ventiladores        | Listar todos os ventiladores           |
| POST   | /api/ventiladores        | Criar um novo ventilador               |
| PUT    | /api/ventiladores/:id    | Atualizar informações do ventilador    |
| DELETE | /api/ventiladores/:id    | Remover um ventilador                  |
| POST   | /api/chat                | Enviar mensagem ao modelo de IA        |
| POST   | /api/webhook             | Webhook do WhatsApp                    |

---

## 📆 Cronograma de Desenvolvimento

| Semana | Entregas Principais                                      |
|--------|----------------------------------------------------------|
| 1      | Estrutura inicial, protótipo UI, banco de dados          |
| 2      | Backend (Node API), base do Chatbot                      |
| 3      | Frontend (Chat, Prompt Config), Inventário               |
| 4      | Relatórios, testes internos                              |
| 5      | Integração com WhatsApp Business                         |
| 6      | Responsividade, testes finais, documentação              |
| 7      | Buffer para ajustes e publicação                         |

---

## 📄 Licença

Este projeto está licenciado sob a [MIT License](LICENSE).
