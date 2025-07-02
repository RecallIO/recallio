
# 🧠 RecallIO

**RecallIO.ai** – a plug‑and‑play memory API for AI apps, agents, and SaaS tools.  
Persistent, scoped memory across sessions—without building any backend infrastructure ([recallio.ai](https://www.recallio.ai/?utm_source=github.com)).

---

## 🚀 Features

- **Scoped & Persistent Memory**  
  Save, retrieve, and update memory items tied to users or sessions.

- **LLM-Agnostic**  
  Works seamlessly with OpenAI, Claude, GPT‑4V, and more ([github.com](https://github.com/embedchain/embedchain/activity?ref=main&utm_source=chatgpt.com), [app.recallio.ai](https://app.recallio.ai/?utm_source=github.com)).

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
├── examples/         # Demo integrations (Node, Python)
└── README.md         # ← You are here
```

---

## ⚡ Quickstart Node.js

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
      userId,
      projectId,
      content: text,
      tags: ['telegram'],
      consentFlag: true
    });

// Recall memories
const result = await client.recallMemory({
        userId,
        projectId,
        query,
        scope: 'user',
        limit: 10,
        similarityThreshold: 0.2,
        tags: ['telegram'],
        summarized: true
      });
const response = result.length > 0 && result[0].content || 'No memory found.';

console.log(result);
```

---

---

## ⚡ Quickstart Python

## Installation

```bash
pip install recallio
```

## Usage

```py
from recallio import RecallioClient, MemoryWriteRequest, MemoryRecallRequest, RecallioAPIError

self.recall_client = RecallioClient(api_key='YOUR_API_KEY')


// Write a memory
self.recall_client.write_memory(
              MemoryWriteRequest(
			  userId=self.user_id, 
			  projectId=self.project_id, 
			  content=user_text, 
			  consentFlag=True)
            )
			

// Recall memories
recall_req = MemoryRecallRequest(
                projectId=self.project_id,
                userId=self.user_id,
                query=user_text,
                scope='user',
                summarized=True,
                similarityThreshold=0.2,
                limit=10,
            )
memories = self.recall_client.recall_memory(recall_req)
if memories:
	first = memories[0]
	summary_text = getattr(first, 'content', '') or getattr(first, 'summary', '')
```

---

## 📚 Examples

- **Node.js**, **Python** – See `/examples` for integration across environments.  
- **AI Agents & SaaS** – Built for conversational tools, customer support, personal assistants.

---

## 🙌 Get Involved

Got feedback? Found issues?  
Drop into discussions, raise issues, or shoot over a PR!

Let’s build better AI memories 🔗  
