# Contributing to the AI Healthcare Platform

Thanks for considering a contribution — bug fixes, new features, docs,
dataset/benchmark contributions, and trained model checkpoints (with clear
provenance/license) are all welcome.

## Getting started

```bash
git clone <your-fork-url>
cd Heart-Attack-Risk-Prediction-Using-AI-CNN-Based-Species-Classification
bash scripts/setup.sh   # backend venv + synthetic data + trained ensemble + frontend deps
```

Or follow the manual Quickstart in the root README.

## Development workflow

### Backend
```bash
cd backend
pip install -r requirements.txt ruff black pytest pytest-cov
ruff check app tests
black app tests
pytest --cov=app
```
Note: `pytest` will pick up the committed
`training/heart_risk/models/ensemble_bundle.joblib` automatically — tests
pass under both the trained-model path and (if you temporarily move that
file) the heuristic-fallback path.

### Frontend
```bash
cd frontend
npm install
npm run lint
npm run build
```

## Commit and PR guidelines

- Clear, present-tense commit messages.
- Keep PRs focused on one change.
- Fill out the PR template, including the test checklist.
- New services in `backend/app/services/` ship with unit tests in `backend/tests/`.
- New API routes get documented in the README's API table.

## Where to contribute

- **Species CNN training**: no pretrained checkpoint is committed (see
  `training/README.md` for why) — training one on a real public dataset
  and documenting the results is a high-value contribution.
- **Experimental tabular Transformer**: `training/heart_risk/train_transformer_experimental.py`
  has never been run in this repo's dev environment (no GPU) — benchmarking
  it on a real dataset and reporting results is valuable, win or lose.
- **Qdrant/vector-search-backed RAG**: the chat assistant currently does
  in-memory retrieval over a single loaded document; a proper vector store
  for cross-document retrieval is open for contribution.
- **Frontend component tests**: see `tests/README.md`.
- **i18n**: the platform is English-first.

## Code style

- Python: `black` formatting, `ruff` linting, type hints on public functions.
- TypeScript: existing `eslint-config-next` rules, functional React components.

## Code of Conduct

By participating, you agree to abide by [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).
