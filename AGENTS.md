# Base44 Dev Environment

## What this project is
A single Quarto report document (`ETW3483_A3_report.qmd`). It is not a traditional web app — there is no package.json, no backend, no build system beyond Quarto itself.

## How it runs
- `docker-compose.base44.yml` uses the official `ghcr.io/quarto-dev/quarto` image to run `quarto preview` in watch mode on port 3000.
- Edits to the `.qmd` file are automatically re-rendered and reflected in the preview (live reload).
- No external credentials or secrets are needed.
- The Quarto image is Ubuntu-based with `bash` but no `curl`/`wget`/`python3`; the healthcheck uses bash `/dev/tcp`.

## Verifying it works
- `docker compose -f docker-compose.base44.yml up -d --build` then `docker compose ps` and `curl -s localhost:3000 | head`.
- The served page should contain the report title "A3_ETW2001" and its content.

## Notes
- Rendering the `.qmd` produces an `ETW3483_A3_report.html` file in the repo root; this is a build artifact and should not be committed.
