# TaskFlow

Um gerenciador de tarefas minimalista e elegante com design futurista. Criado com React 18 + Node.js/Express + SQLite.

## Visual

Interface dark mode com acento verde neon, tipografia Space Grotesk, sidebar fixa, filtros por status e prioridade, barra de progresso e painel de estatísticas.

## Pré-requisitos

- Node.js 18+
- npm 9+

## Instalação

```bash
# 1. Extraia o ZIP e entre na pasta
cd taskflow

# 2. Backend
cd server
npm install
cp .env.example .env
npm run dev
# → Servidor em http://localhost:3001
# → Banco criado e populado automaticamente

# 3. Frontend (novo terminal)
cd client
npm install
cp .env.example .env
npm run dev
# → Interface em http://localhost:5173
```

## Rotas da API

| Método | Rota                  | Descrição                      |
|--------|-----------------------|--------------------------------|
| GET    | /api/tasks            | Listar tarefas (filtros: status, priority) |
| GET    | /api/tasks/stats      | Estatísticas gerais            |
| GET    | /api/tasks/:id        | Buscar tarefa por ID           |
| POST   | /api/tasks            | Criar nova tarefa              |
| PUT    | /api/tasks/:id        | Atualizar tarefa               |
| DELETE | /api/tasks/:id        | Deletar tarefa                 |

### Exemplos

```bash
# Criar tarefa
curl -X POST http://localhost:3001/api/tasks \
  -H "Content-Type: application/json" \
  -d '{"title":"Minha tarefa","priority":"high"}'

# Listar por status
curl "http://localhost:3001/api/tasks?status=in_progress"

# Stats
curl http://localhost:3001/api/tasks/stats
```

## Estrutura de Pastas

```
taskflow/
├── client/                    # Frontend React + Vite
│   └── src/
│       ├── components/ui/     # Badge, Modal, TaskCard, TaskForm, Toast
│       ├── components/layout/ # Sidebar
│       ├── pages/             # TasksPage, StatsPage
│       ├── hooks/             # useStats
│       ├── services/          # api.js (axios)
│       ├── context/           # TaskContext (estado global)
│       └── styles/            # global.css (design system)
├── server/                    # Backend Node.js + Express
│   ├── routes/                # tasks.js
│   ├── controllers/           # tasksController.js
│   └── database/              # db.js (SQLite auto-init + seed)
└── README.md
```

## Tecnologias

**Frontend:** React 18, React Router v6, Axios, Vite  
**Backend:** Node.js, Express 4, better-sqlite3  
**Design:** Space Grotesk + DM Mono (Google Fonts), CSS custom properties, mobile-first
