# infra-poste
Infra de Poste.io (VPS Hostinger + Traefik + Coolify).

## Contenido
- `deploy/docker-compose.yml`: compose de producción.
- `deploy/.env.from_container`: variables de entorno actuales (snapshot).
- `backups/poste_data_YYYY-MM-DD.tar.gz`: backup del volumen `/data` (Git LFS).

## Restore rápido post-reset
1) `docker network create traefik_proxy || true`
2) `cd deploy`
3) (Opcional) revisar `.env.from_container` y crear `.env` si querés.
4) `docker compose up -d`

Notas:
- Traefik maneja solo la parte web (panel). SMTP/IMAP/Submission están expuestos en host.
- Para restaurar correos: extraer `backups/*.tar.gz` en el volumen `/data`.
