# Blog Content Generator

## Command-Line Interface (CLI)

This project provides a modern CLI for analyzing writing style, generating content, and refining content, powered by [Typer](https://typer.tiangolo.com/).

### Usage

Run the CLI from the project root:

```bash
python -m blog_generator.main_cli [OPTIONS] COMMAND [ARGS]...
```

### Available Commands

- `analyze-style [FILES...]` — Analyze style from one or more text files.
- `generate-content --style-id STYLE_ID --topic TOPIC [other options]` — Generate content for a given style profile and topic.
- `refine-content --content-id CONTENT_ID --feedback FEEDBACK` — Refine content based on user feedback.

### Examples

Analyze style from two files:
```bash
python -m blog_generator.main_cli analyze-style samples/sample1.txt samples/sample2.txt
```

Generate content:
```bash
python -m blog_generator.main_cli generate-content --style-id my-style-id --topic "AI in Marketing" --platform linkedin
```

Refine content:
```bash
python -m blog_generator.main_cli refine-content --content-id 12345 --feedback "Make it more concise."
```

### Debug Mode
Add `--debug` to any command for verbose output and troubleshooting.

### Help
Get help for any command:
```bash
python -m blog_generator.main_cli --help
python -m blog_generator.main_cli analyze-style --help
```

This project is organized for clarity, modularity, and scalability. Below is a summary of the main folders and their intended use:

## Project Structure

- `api/` — FastAPI/Flask app entrypoint and route definitions.
- `core/` — Core business logic (content generation, style analysis, knowledge base, etc.).
- `crews/` — Modular CrewAI crew definitions and YAML configs.
- `database/` — Database connectors and models (e.g., ChromaDB).
- `tools/` — Specialized tools for document/web processing, LLM switching, vector DB, feedback, etc.
- `utils/` — General-purpose utility functions (file, text, logging, compatibility, etc.).
- `config/` — Project-wide configuration (all config in `settings.py`).

## Recent Simplifications

- The `rag/` directory was merged into `core/` (now `core/knowledge_base.py`) as part of project simplification, since RAG logic is not expected to grow into multiple modules.
- All `__pycache__` and non-source artifacts have been removed.
- `tools/` and `utils/` have been reviewed: tools are specialized modules, utils are generic helpers—no significant overlap remains.
- Crew files and YAMLs remain separate and flat for clarity and scalability.

## Features

- **Style Analysis:** Upload writing samples (text, PDF, URL, YouTube), analyze with RAG, visualize style.
- **Content Generation:** Specify topic, industry, purpose, audience; generate content in personal style for multiple platforms.
- **Settings:** Configure LLM backends, manage API keys, adjust generation parameters.

## Prerequisites

- Python 3.8+
- Required packages listed in `requirements.txt`
- Ollama (optional, for local LLM support)

## Installation

### Recommended: Fast Install with [uv](https://github.com/astral-sh/uv)

```bash
uv pip install -e ".[dev,ollama]"
```
- The `-e` flag installs in editable (development) mode.
- Add or remove extras (`dev`, `ollama`) as needed.

### Alternative: pip

```bash
pip install -e ".[dev,ollama]"
```

## Running the App

```bash
cd myprojects/blog_generator
streamlit run app.py
```

The app will be available at http://localhost:8501 in your web browser.

## Running the CLI

After installing, you can use the CLI:

```bash
bloggen --help
bloggen generate --topic "AI" --platform linkedin
bloggen analyze-style --file sample.txt
bloggen run-server
bloggen test
```

## Development Notes

- The backend is CrewAI-based and implements style vector extraction/storage, RAG-based content generation, and multi-LLM support.
- All configuration lives in `config/settings.py`.
- The codebase is kept modular, flat, and easy to navigate.
- See `masterplan_v2.md` for ongoing and completed simplification steps.
