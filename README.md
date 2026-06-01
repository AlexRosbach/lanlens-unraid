# LanLens Unraid Template

Unraid Community Applications template for [LanLens](https://github.com/AlexRosbach/LanLens).

This repository contains only the Unraid Docker template metadata. The application code and Docker image stay in the main LanLens repository and Docker image.

## Template

- Template: [`templates/lanlens.xml`](templates/lanlens.xml)
- Docker image: `alexrosbach/lanlens:latest`
- Default Web UI port: `7765`
- Appdata path: `/mnt/user/appdata/lanlens`
- Network mode: `host`

LanLens uses host networking because local ARP/MAC discovery needs raw network access on the Unraid host interface. The template also adds `NET_ADMIN` and `NET_RAW` for the same reason.

## Required Setup

Before starting the container, set a strong `SECRET_KEY` in the Unraid template.

Generate one with:

```bash
python3 -c "import secrets; print(secrets.token_hex(32))"
```

The default admin password is only intended for first startup. Change it after login.

## Community Applications Submission

Use the official Unraid Community Applications submission portal:

<https://ca.unraid.net/submit>

Repository XML help:

<https://ca.unraid.net/submit/help/repository-xml>

## Support

- Project: <https://github.com/AlexRosbach/LanLens>
- Issues: <https://github.com/AlexRosbach/LanLens/issues>
