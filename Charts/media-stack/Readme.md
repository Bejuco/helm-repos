# media-stack 🎬📡

A modular, Helm-powered media automation stack for Kubernetes. This chart deploys qBittorrent, Radarr, Sonarr, Bazarr, and Prowlarr — fully containerized and ingress-ready, with centralized NFS-based storage.

## 🧰 Features

- ⚙️ Helm-templated: fully reusable and configurable via `values.yaml`
- 🪝 Traefik ingress: HTTP access for each app via custom domain
- 💾 Longhorn storage for app config + NFS volume for shared media data
- 🔁 One-command deploy + easy upgrade path

## 🚀 Install
Clone this repo, and cd into /charts

```bash
helm install media ./media-stack -n media --create-namespace
```

to Update:
```bash
helm upgrade media ./media-stack -n media
```

## Values
Values.yaml file is included with my own defaults. Most important is the `apps` section: each defines a single container, with the corresponding host and port; only **QBitTorrent** exposes more than a single port. 

**Required Modifications:**
```yaml
global:
  namespace: media
  storageClass: longhorn

nfs:
  enabled: true
  pvName: nfs-media-data
  serverIP: 192.168.5.5         # 🔁 Change this to your NFS Server IP
  serverPath: /volume1/data     # 🔁 Your Media data. This folder includes a Download and a media folder. 
  capacity: 10Gi
  accessModes:
    - ReadWriteMany
  reclaimPolicy: Retain
```

## In-App Config
You can configure each of your apps as you see fit, but when connection between them, you can leverage KubeDNS automatically to set up the host/ip of each service, so for example, to connect to QBitTorrent from Sonarr, you simply put `qbittorrent` as the host with default ports.  