# Ollama, n8n, and Obsidian vault

This stack runs Ollama and n8n locally. The `obsidian-vault` directory is an Obsidian-compatible vault on the host and is available to n8n workflows at `/files/obsidian`.

## Start

1. Copy `.env.example` to `.env`.
2. Replace `N8N_ENCRYPTION_KEY` with a long, random, stable secret.
3. Run `docker compose up -d`.
4. Open `http://localhost:5678` and complete n8n's initial setup.

In n8n, call Ollama using `http://ollama:11434`; Docker resolves the service name internally. Open the same `obsidian-vault` directory in the Obsidian desktop application to view or edit the Markdown notes that workflows create.

To install a model, run `docker compose exec ollama ollama pull llama3.2`. Replace `llama3.2` with a model suited to your hardware.

## Data persistence

- `n8n_data` retains workflows, credentials, and n8n configuration.
- `ollama_data` retains downloaded models.
- `obsidian-vault` is a normal host directory, deliberately separate from Docker volumes so Obsidian and n8n can share it.