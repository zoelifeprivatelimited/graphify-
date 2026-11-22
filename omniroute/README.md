# OmniRoute

Self-hosted [OmniRoute](https://github.com/diegosouzapw/OmniRoute) AI gateway:
one OpenAI-compatible endpoint that routes to many model providers with fallback.

## Run

```bash
cd omniroute
cp .env.example .env
```

Fill in `.env` (generate each secret with `openssl rand -hex 32`), then:

```bash
docker compose up -d
```

- Dashboard: http://localhost:20128
- API base: http://localhost:20128/v1 (requires an OmniRoute API key — create one in the dashboard)

## Security defaults

- Published on `127.0.0.1` only. Put a TLS reverse proxy in front before exposing it.
- `REQUIRE_API_KEY=true`: `/v1/*` rejects requests without a key.
- No default secrets: the upstream package ships an empty `JWT_SECRET` and a
  `CHANGEME` password, so `.env` must be filled in before first start.
- `.env` is git-ignored; never commit it.

## Upgrade

Change the image tag in `docker-compose.yml`, then `docker compose pull && docker compose up -d`.
Data lives in the `omniroute-data` volume.
