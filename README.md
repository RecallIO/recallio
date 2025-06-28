
# 🧠 RecallIO

**RecallIO.ai** – a plug‑and‑play memory API for AI apps, agents, and SaaS tools.  
Persistent, scoped memory across sessions—without building any backend infrastructure ([recallio.ai](https://www.recallio.ai/?utm_source=chatgpt.com)).

---

## 🚀 Features

- **Scoped & Persistent Memory**  
  Save, retrieve, and update memory items tied to users or sessions.

- **LLM-Agnostic**  
  Works seamlessly with OpenAI, Claude, GPT‑4V, and more ([github.com](https://github.com/embedchain/embedchain/activity?ref=main&utm_source=chatgpt.com), [app.recallio.ai](https://app.recallio.ai/?utm_source=chatgpt.com)).

- **Plug‑and‑Play API**  
  Easy REST + SDK integration—no infra, no fuss.

- **Secure & Compliant**  
  Supports best practices for data privacy and access control.

---

## 💡 Why RecallIO?

| Problem | RecallIO Solution |
|--------|-------------------|
| Context resets across sessions | Memory persists and is searchable |
| Reinvention of memory infra | Ready-to-use API layer |
| Token overload | Efficient retrieval with scoped context |

---

## 📦 Repository Structure

```
/
├── examples/         # Demo integrations (Node, Python, Web)
├── docs/             # Usage guides & API reference
└── README.md         # ← You are here
```

---

## ⚡ Quickstart

## Installation

```bash
npm install recallio
```

## Usage

```ts
import { RecallioClient } from 'recallio';

const client = new RecallioClient({ apiKey: 'YOUR_API_KEY' });

// Write a memory
await client.writeMemory({
  userId: 'user_123',
  projectId: 'project_abc',
  content: 'The user prefers dark mode',
  consentFlag: true,
});

// Recall memories
const result = await client.recallMemory({
  userId: 'user_123',
  projectId: 'project_abc',
  query: 'dark mode',
  scope: 'user',
});

console.log(result);
```

---

## 📚 Examples

- **Node.js**, **Python**, **Browser** – See `/examples` for integration across environments.  
- **AI Agents & SaaS** – Built for conversational tools, customer support, personal assistants.

---

## 🙌 Get Involved

Got feedback? Found issues?  
Drop into discussions, raise issues, or shoot over a PR!

Let’s build better AI memories 🔗  
