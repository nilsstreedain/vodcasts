# vodcasts
Set up Raspberry Pi to convert YouTube channels feeds into hosted vodcast (Video-On-Demand Podcast) feeds, downloadable by supported podcast apps.

1. Install `Raspberry Pi OS Lite (64-bit)` using Raspberry Pi Imager
    - Set username/password, locale on General tab
    - Enable SSH (Allow public-key authentication only) and paste key in Services tab
    - Disable telemetry in Options tab
2. SSH into pi
```
ssh username@192.168.x.x
```

3. Install Docker
```
curl -fsSL https://get.docker.com | sh
```

4. Create docker-compose.yml
```
nano docker-compose.yml
```

Paste the contents of [this file](https://raw.githubusercontent.com/nilsstreedain/vodcasts/refs/heads/main/docker-compose.yml) and save.

5. Create podsync-config.toml
```
nano podsync-config.toml
```

Paste the contents of [this file](https://raw.githubusercontent.com/nilsstreedain/vodcasts/refs/heads/main/podsync-config.toml).
(add YouTube API token and [configure feeds](https://github.com/mxpv/podsync/blob/0dfc8f15ab6f7d4d91872fa1a202d4984c26866e/config.toml.example))

6. Start Docker containers
Add Cloudflare tunnel token
```
export TOKEN=...
```

```
sudo docker compose up -d
```
