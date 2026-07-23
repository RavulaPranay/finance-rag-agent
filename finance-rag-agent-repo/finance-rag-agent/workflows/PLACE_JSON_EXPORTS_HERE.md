## How to add your workflow files

1. Open each workflow in n8n
2. Click the **"..."** (three dots) menu, top right → **Download**
3. This saves a `.json` file — n8n exports the full workflow (nodes, connections, settings)
4. Rename and drop them into this folder as:
   - `workflow-1-document-ingestion.json`
   - `workflow-2-chat-agent.json`
5. Delete this file once both are added

**Important before exporting:** double-check the JSON doesn't contain your actual Groq/Gemini/Pinecone/Telegram API keys or bot tokens before pushing to a public repo. n8n usually excludes credential values by default, but verify.
