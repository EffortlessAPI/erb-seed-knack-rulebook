# Knack Rulebook Seed

A rulebook extracted from a Knack application, plus everything that can be derived
from it. The extraction has already happened when this project reaches you --
`effortless-rulebook/effortless-rulebook.json` IS your model, as a rulebook
you own. (In this repository it is the starter's sample rulebook; the website
replaces it with the one pulled from your source.)

## What `effortless build` produces

| Folder | From | What it is |
|---|---|---|
| `postgres/` | rulebook-to-postgres | The schema, `vw_*` views, functions and seed data |
| `docs/` | rulebook-to-markdown | Documentation of every table, field and rule |
| `rulespeak/` | rulebook-to-rulespeak | Business-readable RuleSpeak statements |
| `explainer-dag/` | rulebook-to-explainer-dag | Interactive dependency graph of every derived value |
| `xlsx/` | rulebook-to-xlsx | An Excel workbook with the model and live formulas |
| `effortless-rulebook/docker/` | effortless-rulebook-editor | A Docker image: Postgres + the generated API + the browser rulebook editor |

Nothing generated is meant to be edited or committed: change
`effortless-rulebook/effortless-rulebook.json`, run `effortless build`, and
every surface follows.

## Pulling from the source again

The `knack-to-rulebook` step is registered but **disabled**: a normal
`effortless build` never calls Knack and needs no credentials. To make the
rulebook follow the application again, add your API key to that step's
`CommandLine` in `effortless.json` **locally** (do not commit it):

```
knack-to-rulebook -o effortless-rulebook.json -p applicationId=<app id> -p projectName=<name> -p apiKey=<your Knack API key> -w 540000
```

then run:

```bash
effortless build -id      # -id runs disabled steps too
```

## Getting started

```bash
effortless build
./effortless-rulebook/edit-rulebook.sh      # open the rulebook editor (needs Docker)
```

## Requirements

- the `effortless` CLI (`npm i -g @effortlessapi/cli`), signed in
- Docker, only for the rulebook editor
- a Knack API key, only to re-pull from the application
