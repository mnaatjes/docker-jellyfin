# docker-jellyfin

Declarative Docker Compose application stack for Jellyfin Media Server across the homelab infrastructure.

---

## 1. Overview & Architecture

* **Service Name:** `docker-jellyfin`
* **Upstream Image:** [`jellyfin/jellyfin:10.9.11`](https://hub.docker.com/r/jellyfin/jellyfin)
* **Target Node:** `prd-media-01.lan` (Worker Archetype)
* **Network Mode:** `host` (Port `8096` HTTP, `8920` HTTPS, DLNA `1900/udp`, discovery `7359/udp`)
* **Hardware Transcoding:** Intel QuickSync Video via VA-API (`/dev/dri/renderD128` and `/dev/dri/card0`)
* **Deployment Orchestrator:** Ansible `roles/compose_stack` in `homelab-ops`

---

## 2. Directory Taxonomy & Mounts

In strict compliance with the **Homelab Systems Lifecycle (HSL)**:

* **Compose Specification:** `/opt/homelab/prod/compose/docker-jellyfin/compose.yml`
* **Persistent Configuration & Database:** `/opt/homelab/prod/data/docker-jellyfin/config/`
* **Transcoding & Image Cache:** `/opt/homelab/prod/data/docker-jellyfin/cache/`
* **Media Library Storage:** `/mnt/nas/media/` (Read-only NFS mount from `prd-nas-01.lan`)

---

## 3. Local Development & Verification

Validate the Compose configuration:

```bash
cp .env.example .env
docker compose config --quiet
```
