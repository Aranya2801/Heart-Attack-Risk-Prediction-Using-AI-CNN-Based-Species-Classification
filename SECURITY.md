# Security Policy

## Supported Versions

| Version | Supported |
|---|---|
| main (latest) | ✅ |
| older tags | ❌ |

## Reporting a Vulnerability

Please **do not** open a public GitHub issue for security vulnerabilities.

Instead:
1. Use GitHub's [private vulnerability reporting](../../security/advisories/new) on this repo, or
2. Email the maintainers (see repository "About" section) with a description,
   reproduction steps, and any suggested remediation.

We aim to acknowledge reports within 5 business days and provide a fix or
mitigation timeline within 14 days for confirmed issues.

## Scope

Includes the FastAPI backend, Celery worker, Next.js frontend, Docker
Compose configuration, and CI workflows in this repository.

Out of scope: vulnerabilities in third-party dependencies that already have
public CVEs and patches available (open a PR bumping the dependency instead).

## Authentication & data handling

- JWT access/refresh tokens (`backend/app/core/security.py`); passwords
  hashed with bcrypt directly (not via passlib, due to a known
  passlib/bcrypt 4.x compatibility issue — see that module's comments).
- Role-based access control via `require_role()` dependencies.
- Every prediction/classification/report access is recorded in
  `audit_logs` (`backend/app/core/audit.py`).
- Rate limiting (`backend/app/core/rate_limit.py`), Redis-backed with an
  in-process fallback.

## Handling of patient data

This platform processes health-adjacent data (clinical features, uploaded
medical images). Operators deploying it are responsible for their own
compliance with applicable law (HIPAA, GDPR, etc.), including:
- Setting a strong, unique `SECRET_KEY` before any non-local deployment
  (never use the `.env.example` placeholder).
- Restricting database access and backups appropriately.
- Not committing `.env` files, database dumps, generated PDF reports
  (`backend/generated_reports/` is gitignored), or real patient data to
  version control.
- Reviewing `docs/deployment/README.md`'s "Common to all targets" section
  before going to production.
