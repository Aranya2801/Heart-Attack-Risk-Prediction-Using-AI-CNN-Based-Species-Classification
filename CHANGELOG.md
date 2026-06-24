# Changelog

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [0.1.0] - 2026-06-20

### Added
- FastAPI backend: JWT auth + RBAC, heart-risk prediction, species
  classification, PDF report generation, RAG chat assistant.
- Heart-risk ensemble: Logistic Regression + XGBoost + LightGBM + CatBoost,
  soft-voted, with SHAP explainability and a documented heuristic fallback.
  Pretrained bundle (on synthetic data) committed for out-of-the-box use.
- Species classification: configurable CNN backbone (custom CNN, ResNet50,
  EfficientNet-B0, ConvNeXt-Tiny, ViT-B/16, DenseNet121) with Grad-CAM /
  attention-rollout, and a documented non-CNN fallback classifier.
- PDF medical report generator (reportlab) with patient summary, risk
  factors, AI findings, and a doctor-notes section.
- Healthcare RAG chat assistant with OpenAI/Ollama/offline-extractive
  generation paths and a curated medical glossary.
- Celery + Redis async task queue (batch scoring, async report generation).
- Prometheus metrics + Grafana dashboard provisioning.
- Audit logging and rate limiting middleware.
- Next.js 14 frontend: landing, login/register, heart-risk form, image
  classification, report generation, chat — all build cleanly.
- Docker Compose: postgres, redis, backend, celery-worker, frontend,
  prometheus, grafana.
- GitHub Actions CI (lint, test, Trivy scan, frontend build).
- Backend test suite: 42 tests across preprocessing, risk scoring, species
  inference, PDF generation, chat, security, and full API integration.
- Synthetic data generator + ensemble training/evaluation scripts (actually
  run in this repo: ROC-AUC ~0.94 on the synthetic dataset).
- Species CNN training/evaluation scripts (correct, syntax-verified;
  not executed in this repo's dev environment — no GPU/large-dependency
  install available — see `training/README.md`).
- Experimental tabular Transformer benchmark script, explicitly marked
  unvalidated.
- IEEE-format research paper template, demo content plan, SVG brand assets.

### Known limitations
- No trained species-classification checkpoint is committed (by design —
  see `training/README.md`); the endpoint uses a documented fallback until you train one.
- The experimental tabular Transformer has not been benchmarked in this repo.
- No vector-database-backed retrieval yet for the chat assistant across
  multiple documents (currently single-document context only).
- Frontend has no component test suite yet.

[0.1.0]: https://github.com/your-org/Heart-Attack-Risk-Prediction-Using-AI-CNN-Based-Species-Classification/releases/tag/v0.1.0
