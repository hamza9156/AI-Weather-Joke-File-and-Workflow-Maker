# AI Weather, Joke, File and Workflow Maker

An n8n workflow that gives you a chat assistant (powered by Claude) with four tools:

| Tool | What it does | API key needed? |
|------|--------------|-----------------|
| **Weather Tool** | Current weather for any city via [Open-Meteo](https://open-meteo.com/) | No |
| **Joke Tool** | Random joke from the [Official Joke API](https://github.com/15Dkatz/official_joke_api) | No |
| **File Maker** | Packages text into a named file and shows the contents in chat | No |
| **Workflow Generator** | Returns importable n8n workflow JSON | No |

The only credential is for the Claude model (Anthropic). On n8n Cloud this can use built-in gateway credits; otherwise add your own Anthropic credential.

## Workflow structure (8 nodes)

```
Chat Trigger -> Assistant Agent
                  |-- Claude Model   (language model)
                  |-- Chat Memory    (last 10 messages)
                  |-- Weather Tool
                  |-- Joke Tool
                  |-- File Maker
                  |-- Workflow Generator
```

## How to import

1. Open n8n and create a new workflow.
2. Click the **...** menu (top right) and choose **Import from File**.
3. Select `ai-weather-joke-file-workflow-maker.json`.
4. Open the **Claude Model** node and pick (or create) an Anthropic credential.
5. Save the workflow.

## How to use

Click **Chat** (or **Open chat**) in the workflow and try:

- "What is the weather in Karachi?"
- "Tell me a joke."
- "Save a shopping list as list.txt"
- "Make me an n8n workflow that fetches data, filters it and sends an email"

## Notes

- The file maker shows file contents in the chat; it does not write to disk.
- Generated workflows use placeholder (No Operation) nodes, so you still configure the real node settings yourself.

## Files

- `ai-weather-joke-file-workflow-maker.json` - the n8n workflow export
- `README.md` - this file
