# Roadmap

## Near-term (v0.2)
- [ ] Train and commit a real species-classification checkpoint on a public
      dataset (see `datasets/README.md`), replacing the fallback as the default.
- [ ] Benchmark `train_transformer_experimental.py` against the ensemble on
      a real (non-synthetic) heart-disease dataset and publish results.
- [ ] Batch resume/cohort upload UI in the frontend (wraps the existing
      `heart_risk.batch_score` Celery task and `inference/batch_predict_heart_risk.py`).
- [ ] Frontend component tests (Vitest + React Testing Library).

## Mid-term (v0.3)
- [ ] Qdrant-backed retrieval for the chat assistant, enabling cross-patient/
      cross-document Q&A instead of single-assessment context.
- [ ] Admin dashboard: usage analytics, audit log viewer, model performance over time.
- [ ] ONNX export path for both models (see `models/README.md`) for
      lower-latency / cross-runtime deployment.
- [ ] Multi-language support for the chat assistant and report generator.

## Long-term (v1.0)
- [ ] Validate on a real, larger, multi-site clinical dataset under
      appropriate ethics/IRB approval — required before any claim of
      clinical utility, not just pipeline correctness.
- [ ] Fairness audit: subgroup performance (sex/age/etc.) for both models,
      published alongside aggregate metrics.
- [ ] Terraform modules for the AWS/Azure/GCP reference deployments in
      `docs/deployment/README.md`.
- [ ] SOC 2-oriented audit trail hardening (currently best-effort logging,
      not a tamper-evident log).

## Always open for contribution
- Expanding the species-classification class taxonomy beyond the 4-class default.
- More engineered clinical features with documented clinical motivation
  (follow the pattern in `backend/app/services/heart_risk/preprocessing.py`).
- Additional fallback-classifier improvements that stay dependency-free.
