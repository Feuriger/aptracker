# Archipelago Overlay Studio

Stream overlays for [Archipelago](https://archipelago.gg) multiworlds: paste a room link and build OBS overlays showing everyone's progress (leaderboard, player card, total progress, live item feed).

Live: **https://aptracker.fireflo.at**

## How it works
- `index.html` is the whole app (static, talks directly to the Archipelago web API).
- Every push to `main` → GitHub Actions builds `ghcr.io/feuriger/aptracker:latest`.
- On the NAS, Watchtower pulls the new image within ~5 minutes and restarts the container.
- Cloudflare Tunnel publishes it at aptracker.fireflo.at.

## Run on a NAS
```bash
git clone https://github.com/Feuriger/aptracker.git && cd aptracker
cp .env.example .env   # put your Cloudflare tunnel token in it
docker compose up -d
```
Tunnel public hostname: `aptracker.fireflo.at` → `http://aptracker:80`.

## Tips
- Open `https://aptracker.fireflo.at/?room=<room link>` to auto-connect.
- Overlay settings live in the overlay URL, so OBS sources keep working across updates.
