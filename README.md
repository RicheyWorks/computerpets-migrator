# Migrator

**Save Migrator** — Converts local offline saves into cloud-synced backend data without duplicating pets.

Part of the [ComputerPets](https://github.com/RicheyWorks/computerpets) ecosystem. Index: [computerpets-ecosystem](https://github.com/RicheyWorks/computerpets-ecosystem).

> Status: **design scaffold**. This repository ships the contract, README, and layout so implementation can start without renaming the organ later.

## Why it exists

Rui already walks with no account. When a player later links Steam or a wallet, Migrator merges the offline care history instead of minting a second Rui.

The flagship overlay already puts a living sticker on the real desktop (Rui first, 210 kinds). Migrator does not replace that. It is one organ.

## Stack

Java 21 · CLI (picocli) · local JSON/SQLite overlay saves · Spring import API · dry-run diffs

GroupId / namespace: `com.enterprisepet.migrator`  
Default listen: `CLI`

## Talks to

- computerpets desktop local store
- computerpets Spring backend
- computerpets-ledger
- computerpets-minter

## Contract

### Data

`LocalSave(path, petId, vitals) · Plan(create[], merge[], conflict[]) · Merge(winner=localCare+cloudIdentity)`

### Surface

- CLI: migrator scan — find local saves
- CLI: migrator plan — diff vs cloud
- CLI: migrator apply --dry-run|--commit
- POST /v1/import — authenticated merge

### Failure doctrine

Conflict (two Ruis) → stop and show plan, never auto-mint. Cloud 401 → leave local untouched. Partial apply → transaction per pet.

## Layout

```
computerpets-migrator/
  README.md           this file
  LICENSE             MIT
  docs/CONTRACT.md    the same contract, frozen for implementers
  src/                implementation lands here
```

## Run (Windows)

PowerShell, from this folder, after the flagship helpers (Git, Node LTS 22+, JDK 21 as needed):

```powershell
mvn -q -DskipTests package; java -jar target/migrator.jar scan
```

You do not need this service to meet Rui. The [flagship start-here](https://github.com/RicheyWorks/computerpets/blob/main/docs/START-HERE.md) is still the first pet.

## Ecosystem

| Organ | Repo |
| --- | --- |
| Flagship desktop + Spring | [RicheyWorks/computerpets](https://github.com/RicheyWorks/computerpets) |
| This organ | [RicheyWorks/computerpets-migrator](https://github.com/RicheyWorks/computerpets-migrator) |
| Full map | [RicheyWorks/computerpets-ecosystem](https://github.com/RicheyWorks/computerpets-ecosystem) |

## License

MIT. See [LICENSE](LICENSE).

---

*Two hundred ten living kinds. Keep them so a line does not go quiet.*
