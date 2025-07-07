# 🧠 RecallIO

**RecallIO.ai** – Plug‑and‑play memory for next-gen AI apps, agents, and SaaS products.
Persistent, intelligent memory across sessions—zero backend infrastructure required.

---

## 🚀 Key Features

* **Persistent & Scoped Memory**
  Seamlessly save, retrieve, and update memories linked to specific users or sessions.

* **Fact Extraction**
  Automatically distill key facts from memories, storing them efficiently for rapid retrieval.

* **Instant Summaries**
  Generate and access insightful summaries within milliseconds.

* **Intelligent Prioritization**
  Surface the most relevant information precisely when it's needed.

* **Memory Graph Intelligence**
  Dynamically identify entities and relationships for advanced, intuitive access.

* **Plug-and-Play Integration**
  Effortless REST and SDK integration—focus on your product, not infrastructure.

* **Secure & Compliance-Ready**
  Designed with industry-leading data privacy and security best practices built-in.

---

## 💡 Why RecallIO?

| Common Challenges                | RecallIO Advantage                 |
| -------------------------------- | ---------------------------------- |
| Session context resets           | Persistent, searchable memory      |
| Rebuilding memory infrastructure | Out-of-the-box memory API          |
| Excessive token usage            | Efficient, scoped memory retrieval |

---

*Unlock smarter AI experiences with RecallIO.*

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

```python
from recallio import (
    RecallioClient,
    MemoryWriteRequest,
    MemoryRecallRequest,
    RecallSummaryRequest,
    GraphAddRequest,
    GraphSearchRequest,
    MemoryExportRequest,
)

client = RecallioClient(api_key="YOUR_RECALLIO_API_KEY")

req = MemoryWriteRequest(
    userId="user_123",
    projectId="project_abc",
    content="The user prefers dark mode and wants notifications disabled on weekends",
    consentFlag=True,
)

memory = client.write_memory(req)
print(memory.id)

# recall memories
recall_req = MemoryRecallRequest(
    projectId="project_abc",
    userId="user_123",
    query="dark mode",
    scope="user",
    reRank=True,
)
results = client.recall_memory(recall_req)
for m in results:
    print(m.content, m.similarityScore)

# summarized recall
summary_req = RecallSummaryRequest(
    projectId="project_abc",
    userId="user_123",
    scope="user",
)
summary = client.recall_summary(summary_req)
print(summary.content)

# add data to the knowledge graph
graph_req = GraphAddRequest(
    data="John works at OpenAI in San Francisco",
    user_id="user_123",
    project_id="project_abc",
)
client.add_graph_memory(graph_req)

# search the graph
search_req = GraphSearchRequest(
    query="Where does John work?",
    user_id="user_123",
)
graph_results = client.search_graph_memory(search_req)
for r in graph_results:
    print(r.source, r.relationship, r.destination)

# export memories as JSON
export_req = MemoryExportRequest(
    type="fact",
    format="json",
    userId="user_123",
)
json_data = client.export_memory(export_req)
print(json_data)
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
