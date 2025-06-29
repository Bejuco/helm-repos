# media-stack 🎬📡

A modular, Helm-powered media automation stack for Kubernetes. This chart deploys qBittorrent, Radarr, Sonarr, Bazarr, and Prowlarr — fully containerized and ingress-ready, with centralized NFS-based storage.

## 🧰 Features

- ⚙️ Helm-templated: fully reusable and configurable via `values.yaml`
- 🪝 Traefik ingress: HTTP access for each app via custom domain
- 💾 Longhorn storage for app config + NFS volume for shared media data
- 🔁 One-command deploy + easy upgrade path

## 🚀 Install

```bash
helm install media ./media-stack -n media --create-namespace

to Update:


helm upgrade media ./media-stack -n media
