# 🚀 Evolution Stack — WhatsApp API + n8n + PostgreSQL + Redis

Este projeto contém uma stack completa para automação inteligente com **[Evolution API](https://github.com/atendai/evolution-api)** integrada ao **n8n**, utilizando **PostgreSQL** como banco de dados e **Redis** como cache.

---

## 📦 Tecnologias

| Serviço         | Função Principal                                                                 |
|-----------------|----------------------------------------------------------------------------------|
| **Evolution API** | API para integração e automação de mensagens WhatsApp                          |
| **PostgreSQL**     | Banco de dados relacional utilizado para persistir dados da API                |
| **Redis**          | Cache e mensageria para otimizar desempenho e conexões                         |
| **n8n**            | Plataforma low-code para orquestração de automações e fluxos de trabalho        |
| **Docker Compose** | Orquestra e executa todos os containers da stack                               |

---

## ⚙️ Estrutura do Projeto


---

## 🌍 Variáveis de Ambiente (`.env`)

### 🔧 Configurações do Servidor
| Variável | Descrição | Exemplo |
|-----------|------------|---------|
| `SERVER_URL` | URL onde a API será acessada | `http://localhost:8080` |
| `SWAGGER_ENABLED` | Ativa a documentação Swagger | `true` |
| `AUTHENTICATION_API_KEY` | Chave de autenticação para acesso à API | `senha_magica` |
| `NODE_ENV` | Ambiente de execução | `production` |
| `TZ` | Fuso horário padrão | `America/Sao_Paulo` |
| `LOG_LEVEL` | Nível de log da aplicação | `info` |

### 🗄️ Banco de Dados (PostgreSQL)
| Variável | Descrição | Exemplo |
|-----------|------------|---------|
| `DATABASE_PROVIDER` | Tipo de banco utilizado | `postgresql` |
| `DATABASE_CONNECTION_URI` | URI de conexão ao banco | `postgresql://evo:senha_magica@evolution-db:5432/evolution` |
| `DATABASE_CONNECTION_CLIENT_NAME` | Nome do cliente da conexão | `evolution_exchange` |

### 💾 Salvamento de Dados
As opções abaixo controlam o que será persistido no banco:

### ⚡ Cache (Redis)
| Variável | Descrição | Exemplo |
|-----------|------------|---------|
| `CACHE_REDIS_ENABLED` | Ativa o uso de cache Redis | `true` |
| `CACHE_REDIS_URI` | URI de conexão Redis | `redis://default:@redis:6379/0` |

### 🤖 Integrações
| Variável | Descrição | Exemplo |
|-----------|------------|---------|
| `INTEGRATIONS_ENABLED` | Ativa integrações externas | `true` |
| `WHATSAPP_ENABLED` | Ativa o módulo do WhatsApp | `true` |
| `CONFIG_SESSION_PHONE_VERSION` | Define a versão da sessão WhatsApp | `2.3000.1028148389` |

---

## 🐳 Docker Compose

### Subir todos os serviços
```bash
docker compose up -d
| Serviço           | Porta  | Acesso                                         |
| ----------------- | ------ | ---------------------------------------------- |
| **Evolution API** | `8080` | [http://localhost:8080](http://localhost:8080) |
| **PostgreSQL**    | `5432` | Conexão interna (`evolution-db`)               |
| **Redis**         | `6379` | Cache interno                                  |
| **n8n**           | `5678` | [http://localhost:5678](http://localhost:5678) |
👨‍💻 Autor

Marcos Vinícius
Engenharia de Software — Automação com IA & n8n
📍 Brasília, Brasil
💬 "Simplificando a automação, um fluxo por vez."
