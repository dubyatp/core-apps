# Core Apps
**Production-grade application deployments for my Kubernetes homelab**  

This repository contains the core applications deployed to my Kubernetes homelab. Applications are deployed using either Kubernetes manifests or Helm charts (with upstream subcharts and custom values).

**Why Helm?** I prefer Helm charts when upstream versions exist because Renovate can automatically track new chart versions, whereas image tags in raw manifests aren't always semantically versioned.

**GitOps Workflow:** This repository is monitored by ArgoCD and serves as the source of truth for deployments. Each top-level directory is its own ArgoCD Application, with subdirectories representing components within that application.

**Automated Commits:** Apps that I wrote/maintain directly (such as yt-dlp-bot and zap2xml) get their manifests automatically updated via an Actions workflow in their respective repositories

- `arr-stack/` - Arr Stack (manifests)
    - `flaresolverr/` - Flaresolverr (captcha processor)
    - `prowlarr/` - Prowlarr (indexer manager)
    - `radarr/` - Radarr (movie media manager)
    - `sonarr/` - Sonarr (TV series media manager)
    - `tunnel/` - Custom SSH tunnel to my seedbox to securely communicate with Deluge
- `attic/` - Attic NixOS cache server (manifests)
- `authentik/` - [Authentik](https://auth.dubyatp.xyz) SSO server (Helm chart)
- `gitea/` - [Gitea](https://git.dubyatp.xyz) Git Server (Helm chart)
- `gitea-runner/` - Gitea Runner (manifests)
    - `buildkitd/` - Docker Buildkitd build environment
- `grafana/` - [Grafana](https://grafana.dubyatp.xyz) observability dashboard (Helm chart)
- `jellyfin/` - [Jellyfin](https://jellyfin.dubyatp.xyz) media server (Helm chart)
- `renovate/` - [Renovate](https://git.dubyatp.xyz/renovate-bot) automated dependency manager (manifests)
- `vaultwarden/` - [Vaultwarden](https://vaultwarden.dubyatp.xyz) password manager (manifests)
- `whatismyip/` - [Simple "what is my IP" HTTP service](https://whatismyip.dubyatp.xyz) (manifests)
- `yt-dlp-bot/` - [yt-dlp bot](https://git.dubyatp.xyz/williamp/yt-dlp-bot) (manifests); a custom Discord bot i created for downloading and storing YouTube videos ad-hoc
- `zap2xml/` - [kube-zap2xml](https://git.dubyatp.xyz/williamp/kube-zap2xml) (manifests); modified version of zap2xml (zap2it TV listings scraper) designed for use as Kubernetes jobs and sends the result XMLTV format to a Rook-Ceph S3 bucket