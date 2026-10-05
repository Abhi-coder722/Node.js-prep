# Insurance CRM

A small modular monolith in an npm monorepo. The React client talks only to the CRM BFF. The BFF delegates single-domain work to public facades and cross-domain dashboard reads to the orchestration layer.

```text
apps/web -> apps/crm-api/src/bff -> orchestration -> domain facades
                                               -> customer / policy / task
                                               -> repository contracts
                                               -> memory or MySQL adapters
```

## Run locally

```bash
npm install
npm run dev
```

Open `http://localhost:5173`. The API runs at `http://localhost:4000` and uses seeded in-memory data by default.

## Run with MySQL

```bash
docker compose up -d
cp .env.example .env
DATABASE_MODE=mysql npm run dev
```

The schema is installed from `apps/crm-api/database/schema.sql`. Seed records are included so both persistence modes show the same CRM workflow.

## Verify

```bash
npm test
npm run typecheck
npm run build
```
# Node.js-prep
