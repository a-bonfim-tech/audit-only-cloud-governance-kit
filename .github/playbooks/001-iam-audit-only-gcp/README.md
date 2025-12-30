# Playbook 001 — IAM Audit-Only Baseline (GCP)

[![EN](https://img.shields.io/badge/Language-English-2ea44f)](README.md)
[![PT-BR](https://img.shields.io/badge/Idioma-Portugu%C3%AAs-0a66c2)](README.pt-BR.md)
[![DE](https://img.shields.io/badge/Sprache-Deutsch-555)](README.de.md)

## Objective
Establish a repeatable, audit-only baseline to identify IAM over-privilege and governance drift across a GCP project.

## Safety Contract
Audit-only. Collect state and evidence. No changes executed.

## Steps (Audit-Only)
1) Confirm identity and active project:
   - gcloud auth list
   - gcloud config list project

2) Export IAM policy (evidence):
   - gcloud projects get-iam-policy <PROJECT_ID> --format=json > evidence-iam-policy.json

3) List service accounts:
   - gcloud iam service-accounts list --project <PROJECT_ID> --format=json > evidence-service-accounts.json

4) Review high-risk bindings (manual baseline):
   - owner/editor
   - serviceAccountTokenCreator
   - security admin variants

## Evidence Pack Checklist
- evidence-iam-policy.json
- evidence-service-accounts.json
- notes.md (findings + recommended backlog, no changes executed)
