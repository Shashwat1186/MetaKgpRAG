# MetaKGP RAG

> **MetaKGP** – a lightweight Python Retrieval‑Augmented Generation pipeline that cleans, chunks, and stores Wikipedia‑style data for LLM‑based research.

---

## Overview

- **Ingestion** – reads raw JSON, removes markup, splits into overlapping chunks (`CHUNK_SIZE`, `CHUNK_OVERLAP`).
- **Idempotent** – cached files are skipped unless `--force` is used.
- **Analytics** – `--stats` and `analyze_chunks.py` provide quick insights into page length and chunk distribution.
- **Pluggable** – output (`data/processed/*.json`) works with `chromadb`, `faiss`, or any custom vector store.

---

## Features

- Selective sampling (`--sample N`)
- Rich statistics (`--stats`)
- Chunk‑size analysis (`analyze_chunks.py`)
- Compatible with `sentence‑transformers` embeddings

---

## Installation

```bash
# Clone the repo
git clone https://github.com/your-org/MetaKGP-RAG.git
cd MetaKGP-RAG

# Virtual environment (recommended)
python -m venv .venv
.\.venv\Scripts\Activate.ps1   # PowerShell
# or .\.venv\Scripts\activate.bat  # cmd

# Install dependencies
pip install -r requirements.txt
```

---

## Usage

```bash
# Process all data
python ingest.py

# Force re‑process cached files
python ingest.py --force

# Process first 20 files (quick test)
python ingest.py --sample 20

# Show summary statistics
python ingest.py --stats

# Analyse chunk lengths
python analyze_chunks.py
```

*Tip*: For large corpora, consider batching embeddings and persisting the collection to avoid repeated indexing.

---

## Development

```bash
# Run the linter (flake8) and formatter (black)
pip install flake8 black
flake8 .
black .
```

The code follows **PEP 8** conventions and includes type hints where useful.  Contributions should maintain this style.

---

## Testing

A minimal test suite lives under `tests/` (add your own).  Run with:

```bash
pytest
```

---

## Contributing

1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/my‑feature`).
3. Write tests and ensure the existing suite passes.
4. Submit a Pull Request with a clear description of the change.
5. Follow the **code‑style** guidelines (black, flake8) and update the README if you add a public‑facing feature.

---

## License

This project is licensed under the **MIT License** – see the `LICENSE` file for details.

---

*Happy hacking!* 🎉
