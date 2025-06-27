
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
├── sdk/              # SDK wrappers
├── docs/             # Usage guides & API reference
├── tests/            # Automated tests
└── README.md         # ← You are here
```

---

## ⚡ Quickstart

### 1. Install SDK

```bash
npm install recallio
# or
pip install recallio
```

### 2. Initialize Client

```js
import { RecallIO } from "recallio";

const client = new RecallIO({
  apiKey: process.env.RECALLIO_API_KEY,
  userId: "user‑123",
});

await client.addMemory({ key: "greeting", value: "Hi there!" });
```

### 3. Retain & Retrieve Memory

```js
const items = await client.getMemory({ userId: "user‑123" });
console.log(items);
```

### 4. Context-Aware Chat Example

```js
const memories = await client.searchMemory({
  query: userInput,
  userId: "user‑123",
  limit: 5,
});

const prompt = `
You are a chatbot. Here are past memories:
${memories.map(m => "- " + m.value).join("
")}

Now answer:
${userInput}
`;

// send to LLM, get response...

await client.addMemory({
  key: "lastChat",
  value: `${userInput} → ${assistantReply}`,
});
```

---

## 📚 Examples

- **Node.js**, **Python**, **Browser** – See `/examples` for integration across environments.  
- **AI Agents & SaaS** – Built for conversational tools, customer support, personal assistants.

---

## 📘 Documentation

- [API Reference & SDK](https://app.recallio.ai/api-docs) ([github.com](https://github.com/embedchain/embedchain/activity?ref=main&utm_source=chatgpt.com), [app.recallio.ai](https://app.recallio.ai/api-docs?utm_source=chatgpt.com), [mem0.ai](https://mem0.ai/blog/introducing-openmemory-mcp/?utm_source=chatgpt.com), [github.com](https://github.com/embedchain/embedchain/discussions/categories/general?utm_source=chatgpt.com), [app.recallio.ai](https://app.recallio.ai/?utm_source=chatgpt.com), [arxiv.org](https://arxiv.org/abs/2504.19413?utm_source=chatgpt.com))  
- [Website & Blog](https://www.recallio.ai)

---

## 🧪 Tests & CI

- Unit & integration tests located in `/tests`
- CI pipelines ensure release stability

---

## 🛠️ Contributing

1. Fork the repository  
2. Create a feature branch  
3. Write tests  
4. Submit a PR  

All contributions are welcome—bug fixes, new SDKs, fresh integrations!

---

## 📄 License

MIT License – see the [LICENSE](LICENSE) file.

---

## 🎉 Acknowledgements

Inspired by [Mem0](https://github.com/mem0ai/mem0), which uses intelligent, LLM‑augmented memory for AI agents ([github.com](https://github.com/mem0ai/mem0?utm_source=chatgpt.com), [github.com](https://github.com/mem0ai/mem0-chrome-extension?utm_source=chatgpt.com)).

---

## 🙌 Get Involved

Got feedback? Found issues?  
Drop into discussions, raise issues, or shoot over a PR!

Let’s build better AI memories 🔗  
