# Vaultwarden

Start the service with `docker compose up -d`, then open
<http://localhost:8080>. The port is bound to this machine's loopback interface.

For access through a domain, copy `.env.example` to `.env` and set `DOMAIN`
to your public HTTPS URL. Configure a TLS reverse proxy or tunnel on this
machine to forward to `http://127.0.0.1:8080` and set
`X-Forwarded-Proto: https`. Apply URL changes with `docker compose up -d`.
Setting `DOMAIN` alone does not configure DNS or HTTPS.

Account registration is disabled. For initial setup on localhost, temporarily
set `SIGNUPS_ALLOWED` to `"true"` in `compose.yml`, run
`docker compose up -d`, and create your account. Then restore `"false"` and
run `docker compose up -d` again before enabling remote access.

Vault data is persisted in `vw-data/`. Back up this directory; it and `.env`
are excluded from Git.
