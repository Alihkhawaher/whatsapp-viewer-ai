# WhatsApp Chat Viewer - AI Search Edition

A powerful WhatsApp chat viewer with AI-powered semantic search, built in C# for Windows.

© **Ali Alkhawaher** | [technlov.com](https://technlov.com) | info@technlov.com

---

## Download

Go to the [**Releases**](https://github.com/Alihkhawaher/whatsapp-viewer-ai/releases) page and download `WhatsAppViewerAI.exe`.

No installation required — just run the exe. Your settings are saved in `WhatsAppViewerAI.json` next to the executable.

---

## Features

- **Paginated chat display** with RTL (Arabic/Hebrew) support
- **Date tree navigation** — browse messages by year, month, day
- **Keyword search** — find messages by exact text match
- **AI Semantic Search** — find messages by **meaning**, not just keywords
- **Multi-provider support** — LM Studio (local, free) or OpenRouter (cloud)
- **Context-aware results** — search results show surrounding messages
- **Sortable results** — click column headers to sort by Score, Sender, Message, or Date
- **Embedding cache** — no need to re-compute embeddings after the first build
- **Auto-load last file** — remembers your last chat file
- **Chat statistics** — view message counts, word counts, and chat duration

---

## Requirements

- **Windows** with .NET Framework 4.0+ (pre-installed on most Windows systems)
- **One of the following** (for AI search only):
  - **[LM Studio](https://lmstudio.ai/)** — free, runs locally, no API key needed
  - **[OpenRouter](https://openrouter.ai/)** — cloud-based, requires API key

---

## Quick Start

1. Download `WhatsAppViewerAI.exe` from [Releases](https://github.com/Alihkhawaher/whatsapp-viewer-ai/releases)
2. Double-click to run
3. Go to **File → Open Chat File** (`Ctrl+O`) and select a WhatsApp chat export `.txt` file
4. Browse messages using the date tree on the left
5. Use keyword search in the toolbar, or set up AI search (see below)

---

## How to Use

### Browsing Messages

- **Date Tree** (left panel): Click a year → month → day to view messages from that date
- **"All Messages"** at the top shows all messages
- **Pagination**: Use |<, < Prev, Next >, >| buttons or change "Per page" count
- Each message shows full date and time (e.g., `2024/01/15 03:30 PM Monday`)

### Keyword Search

1. Type a word or phrase in the **Keyword** box in the toolbar
2. Press **Enter** or click **Find**
3. Use **< Prev** and **Next >** to navigate between results

### AI Semantic Search

AI search finds messages by **meaning**. For example, searching "meeting schedule" can find messages saying "let's meet at 3pm" even without those exact words. Works with any language — Arabic, English, and more.

#### Setup (One-Time)

1. Click **Config** in the AI panel (right side)
2. Choose a provider:

**Option A: LM Studio (Free, Local)**
- Download and install [LM Studio](https://lmstudio.ai/)
- In LM Studio, download an embedding model (see recommendations below)
- Start the local server (default port: 1234)
- Select "LM Studio" in Config → click Save

**Option B: OpenRouter (Cloud, Paid)**
- Create an account at [openrouter.ai](https://openrouter.ai)
- Get an API key from your dashboard
- Select "OpenRouter" in Config → enter API key → click Save
- The app auto-detects available embedding models

3. Select a model and click **Save**

#### Building the Index

1. Load a chat file first
2. Click **Build Embedding Index**
3. Wait for indexing to complete (progress shown in status bar)
4. The index is cached — you only build it once per chat file per model

#### Searching

1. Type your query in the AI search box
2. Press **Enter** or click **Search**
3. Results show Score, Sender, Message preview, and Date
4. **Click a column header** to sort results
5. **Double-click a result** to jump to that message in the chat

---

## Recommended Embedding Models

For best results with **Arabic and English** WhatsApp chats:

### Via OpenRouter (Cloud)

| Model | Arabic | Quality | Price |
|-------|--------|---------|-------|
| `qwen/qwen3-embedding-4b` | ★★★★ | ★★★★★ | ~$0.0001/request |
| `qwen/qwen3-embedding-0.6b` | ★★★ | ★★★★ | ~$0.00005/request |
| `openai/text-embedding-3-large` | ★★ | ★★★★ | $0.13/1M tokens |
| `jinaai/jina-embeddings-v3` | ★★★ | ★★★★ | $0.08/1M tokens |
| `baai/bge-m3` | ★★★ | ★★★★ | $0.08/1M tokens |

**Top pick:** `qwen/qwen3-embedding-4b` — best Arabic support, excellent quality, minimal cost.

### Via LM Studio (Local, Free)

| Model | Size | Arabic | Notes |
|-------|------|--------|-------|
| `multilingual-e5-large-instruct` | 560M | Good | Best multilingual for its size |
| `bge-m3` | 568M | Good | Supports 100+ languages |
| `jina-embeddings-v3` | 572M | Good | Flexible dimensions |
| `nomic-embed-text-v1.5` | 137M | Moderate | Fast, lightweight |

**Top pick:** `multilingual-e5-large-instruct` — strong Arabic/English support, runs locally for free.

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+O` | Open chat file |
| `Ctrl+I` | Show chat statistics |
| `Enter` | Execute keyword search or AI search |

---

## Notes

- Chat export files should be in the standard WhatsApp text export format
- Supports both individual and group chats
- RTL text (Arabic, Hebrew) is automatically detected and displayed correctly
- Large chats (100k+ messages) may take a few minutes to index
- Embedding cache is stored next to your chat file (`.embeddings` files)
- OpenRouter costs are minimal — most searches cost less than $0.001
- Settings are saved in `WhatsAppViewerAI.json` next to the exe

---

## License

© Ali Alkhawaher — [technlov.com](https://technlov.com) — info@technlov.com