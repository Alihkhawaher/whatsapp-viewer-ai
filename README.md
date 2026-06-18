# WhatsApp Chat Viewer - AI Search Edition

A powerful WhatsApp chat viewer with AI-powered semantic search, built in C# for Windows.

© **Ali Alkhawaher** | [technlov.com](https://technlov.com) | info@technlov.com

---

## Download

Go to the [**Releases**](https://github.com/Alihkhawaher/whatsapp-viewer-ai/releases) page and download `WhatsAppViewerAI.exe`.

No installation required — just run the exe.

---

## Features

- **Paginated chat display** with RTL (Arabic/Hebrew) support
- **Date tree navigation** — browse messages by year, month, day
- **Keyword search** — find messages by exact text match
- **AI Semantic Search** — find messages by meaning using LM Studio embeddings
- **Context-aware results** — search results show surrounding messages for context
- **Embedding cache** — no need to re-compute embeddings after the first build
- **Chat statistics** — view message counts, word counts, and chat duration

---

## Requirements

- **Windows** with .NET Framework 4.0+ (pre-installed on most Windows systems)
- **LM Studio** (optional, for AI search only) — [Download here](https://lmstudio.ai/)

---

## How to Use

### Loading a Chat

1. Go to **File → Open Chat File** (or press `Ctrl+O`)
2. Select a WhatsApp chat export `.txt` file
3. The chat loads with messages displayed in the center and a date tree on the left

### Browsing Messages

- **Date Tree** (left panel): Click a year → month → day to view messages from that date
- **"All Messages"** node at the top shows all messages
- **Pagination**: Use the buttons at the bottom (|<, < Prev, Next >, >|) or change "Per page" count

### Keyword Search

1. Type a word or phrase in the **Keyword** box in the toolbar
2. Press **Enter** or click **Find**
3. Use **< Prev** and **Next >** to navigate between results
4. Click **Clear** to reset

### AI Semantic Search

AI search finds messages by **meaning**, not just exact keywords. For example, searching "meeting schedule" can find messages saying "let's meet at 3pm" even without those exact words.

#### Setup (One-Time)

1. **Download and install [LM Studio](https://lmstudio.ai/)**
2. In LM Studio, download an **embedding model** (e.g., `nomic-embed-text`, `mxbai-embed-large`)
3. Start the LM Studio local server (default: `http://localhost:1234`)

#### Building the Index

1. Load a chat file first
2. In the **AI Semantic Search** panel (right side):
   - Click **Connect** to detect available embedding models
   - Select an embedding model from the dropdown
   - Click **Build Embedding Index**
3. Wait for indexing to complete (progress shown in status bar)
4. The index is cached — you only need to build it once per chat file per model

#### Searching

1. Type your search query in the AI search box (e.g., "project deadline", "vacation plans", a person's name)
2. Click **Search**
3. Results show:
   - **Score** — similarity score (higher = more relevant)
   - **Sender** — who sent the message
   - **Message** — the matching message with surrounding context (`>>` marks the match)
   - **Date** — when the message was sent
4. **Double-click a result** to jump to that message in the chat view (highlighted in yellow)

#### Tips

- You can search in **any language** — the embedding model understands Arabic, English, and many others
- The **"Results"** dropdown (default: 10) controls how many results to show
- Embedding models are cached per chat file — switching models creates a separate cache
- LM Studio must be running when searching (but not when browsing cached results)

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+O` | Open chat file |
| `Ctrl+I` | Show chat statistics |
| `Enter` | Execute keyword search (when in search box) |

---

## Notes

- Chat export files should be in the standard WhatsApp text export format
- The app supports both individual and group chats
- RTL text (Arabic, Hebrew) is automatically detected and displayed correctly
- Large chats (100k+ messages) may take a few minutes to index — use the cached embeddings to avoid re-indexing

---

## License

© Ali Alkhawaher — [technlov.com](https://technlov.com) — info@technlov.com