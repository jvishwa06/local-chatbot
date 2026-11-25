# Local Chatbot

A chat web page built with Django that answers using a language model running on your own machine through [Ollama](https://ollama.com). No external API is needed.

## How it works

- The `chatbot` app (`ollama_chat/chatbot/`) serves a chat page (`templates/chatbot/chat.html`) from `chat_view`.
- When you send a message, the page posts it as `user_input`. The view passes it to the model with `OllamaLLM` from `langchain-ollama` and returns the reply as JSON (`{"response": ...}`). An empty message returns a 400 error.
- The model is `qwen2.5:0.5b`, set in `ollama_chat/chatbot/views.py`.

## Setup

1. Install Ollama and pull the model:
   ```bash
   ollama pull qwen2.5:0.5b
   ```
2. Install the Python packages:
   ```bash
   pip install django langchain-ollama
   ```

## Run

```bash
cd ollama_chat
python manage.py runserver
```

Then open the chat page from the address shown in the terminal. To use another model, change the model name in `views.py`.
