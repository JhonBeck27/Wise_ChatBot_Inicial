# Wise_ChatBot_Inicial

# 🍫 Wisenewera_bot — Assistente de RH da Chocolatech

> Agente inteligente de Recursos Humanos construído com n8n, IA generativa e Telegram. Responde dúvidas dos colaboradores da Chocolatech com precisão, contexto e segurança.

---

## 💡 O que o Wisenewera_bot faz

O **Wisenewera_bot** é o assistente oficial de RH da **Chocolatech**. Ele atende colaboradores diretamente pelo Telegram, respondendo dúvidas como:

- 🗓️ Políticas de férias, folgas e feriados
- 🕐 Jornada de trabalho, banco de horas e ponto
- 📢 Comunicados e políticas internas da empresa
- ❓ Qualquer dúvida relacionada ao setor de RH

> ⚠️ O bot responde **apenas** perguntas relacionadas ao RH da Chocolatech. Perguntas fora desse escopo não são respondidas.

---

## 🧱 Arquitetura do Projeto

```
Colaborador (Telegram)
        │
        ▼
   Webhook (n8n)
        │
        ▼
   Guardrails ──── bloqueia perguntas fora do RH
        │
        ▼
   Agente IA (Wisenewera_bot)
    ├── RAG → busca nas políticas e documentos de RH
    └── SQL → consulta dados do colaborador no MySQL
        │
        ▼
   Resposta personalizada → Telegram
```

---

## 📖 O que aprendi construindo esse projeto

### 🔍 RAG — Retrieval-Augmented Generation
Como fazer o bot buscar informações dentro dos documentos de RH da Chocolatech antes de responder. Em vez de inventar respostas, ele consulta a base de conhecimento real da empresa e responde com precisão.

### 🧬 Embeddings
Como transformar documentos de RH (políticas, manuais, comunicados) em vetores que a IA entende e consegue consultar. É isso que permite o bot encontrar a resposta certa para cada dúvida.

### ⚙️ n8n na prática — Load Data Flow
Como estruturar o fluxo de entrada de dados no n8n: receber os documentos de RH, gerar os embeddings e armazená-los para que o agente possa consultar em tempo real.

### 🗄️ Integração MySQL com Railway
Como hospedar o banco de dados MySQL na nuvem usando o **Railway** e conectar o bot a ele pelo n8n. O Railway permite subir um banco de dados em minutos, sem precisar configurar servidor, e o n8n acessa via host, porta e credenciais geradas pela plataforma.

### 🤖 Dynamic Parameters com `$fromAI`
Como deixar a IA decidir sozinha quais dados buscar no banco de dados — sem precisar fixar os parâmetros no fluxo manualmente.

### ⚡ Hybrid Power — RAG + SQL
Como combinar documentos de RH (RAG) com dados do colaborador (SQL) para que o bot dê respostas completas, baseadas tanto nas políticas da empresa quanto no histórico individual de cada pessoa.

### 📲 Integração com Telegram
Como conectar o Wisenewera_bot ao Telegram via webhook, recebendo e respondendo mensagens dos colaboradores de forma profissional e escalável.

### 🔗 Webhooks e Fluxos
Como estruturar o recebimento e envio de mensagens de forma assíncrona dentro do n8n, garantindo que nenhuma mensagem se perca.

### 🛡️ Guardrails — Filtros Inteligentes
Como limitar o bot para que ele responda **somente** perguntas de RH. Se um colaborador perguntar algo fora do escopo, o bot redireciona educadamente sem responder sobre outros assuntos.

### 🧵 Session ID — Memória por Colaborador
Como cada colaborador tem sua própria sessão de conversa, garantindo que o bot lembre o contexto da conversa e não misture informações entre diferentes pessoas.

---

## 🛠️ Tecnologias utilizadas

| Tecnologia | Função |
|---|---|
| [n8n](https://n8n.io) | Orquestração dos fluxos de automação |
| [Cohere](https://cohere.com) | Modelo de linguagem do agente |
| Embeddings | Indexação dos documentos de RH |
| [Railway](https://railway.app) + MySQL | Banco de dados dos colaboradores na nuvem |
| Telegram Bot API | Interface de atendimento |
| Webhooks | Recebimento de mensagens em tempo real |
| RAG | Busca nas políticas internas de RH |

---

## 🚀 Como importar o workflow

1. Faça o download do arquivo `.json` deste repositório
2. No n8n, clique em **+** → **Import from file**
3. Selecione o arquivo `.json`
4. Configure as credenciais (Cohere, Railway/MySQL, Telegram)
5. Ative o fluxo e teste pelo Telegram

---

## 📌 Observações

- As credenciais **não estão incluídas** no arquivo exportado por segurança
- O banco MySQL está hospedado no **Railway** — as credenciais de conexão ficam no painel do projeto em railway.app
- O webhook do Telegram precisa de uma URL pública (use ngrok para testes locais)
- O bot está configurado para atender **somente** dúvidas de RH da Chocolatech
---

*Wisenewera_bot 
Imagens:
![image alt](https://github.com/JhonBeck27/Wise_ChatBot_Inicial/blob/main/Captura%20de%20tela%202026-06-22%20094231.png) 
![image alt](https://github.com/JhonBeck27/Wise_ChatBot_Inicial/blob/main/Captura%20de%20tela%202026-06-22%20094249.png)
![image alt](https://github.com/JhonBeck27/Wise_ChatBot_Inicial/blob/main/Captura%20de%20tela%202026-06-22%20094304.png)
![image alt]()
![image alt]()
![image alt]()
![image alt]()
