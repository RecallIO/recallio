
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
  reRank: true,
});

console.log(result);

// Summarize memories
const summary = await client.recallSummary({
  userId: 'user_123',
  projectId: 'project_abc',
  scope: 'user',
});

console.log(summary.content);
```

---

### Working with the knowledge graph

```ts
// Add data to the graph
await client.addGraphMemory({
  data: 'Alice knows Bob',
  user_id: 'user_123',
});

// Search the graph
const relationships = await client.searchGraphMemory({
  query: 'Alice',
  limit: 5,
});

// Export memories as JSON
const data = await client.exportMemory({
  type: 'fact',
  format: 'json',
  userId: 'user_123',
});

console.log(data);
```

### Error handling

API calls throw a `RecallioError` when the service returns an error response. The
error includes the HTTP status code and the payload returned by the API.

```ts
import { RecallioClient, RecallioError } from 'recallio';

try {
  await client.writeMemory({
    userId: 'user_123',
    projectId: 'project_abc',
    content: 'The user prefers dark mode',
    consentFlag: true,
  });
} catch (err) {
  if (err instanceof RecallioError) {
    console.error('API error', err.status, err.details);
  } else {
    console.error('Unexpected error', err);
  }
}
```

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
