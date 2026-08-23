# Migrator contract

Do not implement against folklore. Implement against this file.

## Identity

- Product: **Migrator**
- Repo: `computerpets-migrator`
- Category: Utility Tools
- Idea: Save Migrator
- Port / surface: `CLI`

## Must

- Stay canon with 210 species. No illegal hybrids. No swapped voices.
- Treat the desktop overlay as the main quest. This organ is optional until wired.
- Fail soft: the overlay keeps walking if this service is down, unless this *is* the overlay.
- No PII in public artifacts (Steam id, wallet, home path, webcam frames).

## Data

LocalSave(path, petId, vitals) · Plan(create[], merge[], conflict[]) · Merge(winner=localCare+cloudIdentity)

## Surface

- CLI: migrator scan — find local saves
- CLI: migrator plan — diff vs cloud
- CLI: migrator apply --dry-run|--commit
- POST /v1/import — authenticated merge

## Neighbors

- computerpets desktop local store
- computerpets Spring backend
- computerpets-ledger
- computerpets-minter

## Failure doctrine

Conflict (two Ruis) → stop and show plan, never auto-mint. Cloud 401 → leave local untouched. Partial apply → transaction per pet.

## Stack

Java 21 · CLI (picocli) · local JSON/SQLite overlay saves · Spring import API · dry-run diffs
