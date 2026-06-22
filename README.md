# AlexRosbach Unraid Templates

Unraid Community Applications templates for AlexRosbach self-hosted apps:

- [LanLens](https://github.com/AlexRosbach/LanLens)
- [MarketPlaceLens](https://github.com/AlexRosbach/MarketPlaceLens)

This repository contains only the Unraid Docker template metadata. Application code and Docker images stay in the main project repositories and Docker images.

## Templates

- LanLens template: [`templates/lanlens.xml`](templates/lanlens.xml)
- MarketPlaceLens template: [`templates/marketplacelens.xml`](templates/marketplacelens.xml)
- Repository profile: [`ca_profile.xml`](ca_profile.xml)

### LanLens

- Docker image: `alexrosbach/lanlens:latest`
- Template URL: <https://raw.githubusercontent.com/AlexRosbach/lanlens-unraid/main/templates/lanlens.xml>
- Default Web UI port: `7765`
- Appdata path: `/mnt/user/appdata/lanlens`
- Network mode: `host`
- Required capabilities: `NET_ADMIN`, `NET_RAW`

LanLens uses host networking because local ARP/MAC discovery needs raw network access on the Unraid host interface. The template also adds `NET_ADMIN` and `NET_RAW` for the same reason.

The template intentionally uses `alexrosbach/lanlens:latest` so Unraid users receive the current LanLens Docker image through normal container updates.

### MarketPlaceLens

- Docker image: `alexrosbach/marketplacelens:latest`
- Template URL: <https://raw.githubusercontent.com/AlexRosbach/lanlens-unraid/main/templates/marketplacelens.xml>
- Default Web UI port: `8091`
- Appdata path: `/mnt/user/appdata/marketplacelens`
- Network mode: `bridge`

MarketPlaceLens uses normal bridge networking. The template maps Unraid port `8091` to container port `8080` and adds `host.docker.internal` for advanced integrations that need to reach services on the Unraid host.

The template intentionally uses `alexrosbach/marketplacelens:latest` so Unraid users receive the current stable MarketPlaceLens Docker image through normal container updates.

## First Startup

### LanLens

LanLens now starts without a manually supplied `SECRET_KEY`. On first startup, the container generates a strong key and stores it inside the persistent appdata volume at `/data/secret_key`.

Only set the optional `SECRET_KEY` template field when restoring or migrating an existing encrypted LanLens setup that must keep the same signing/encryption key.

The default admin password is only intended for first startup. Change it after login.

### MarketPlaceLens

On first startup, open the Web UI and create the first admin account. The `Admin Username` and `Admin Password` template fields are optional bootstrap helpers for unattended deployments; leave the password empty for the guided setup flow.

MarketPlaceLens stores its SQLite database, settings, user data, session secret, and notification configuration in the persistent appdata volume.

## Community Applications Submission

Current repository readiness checklist:

- Public GitHub repository
- OSI-approved MIT license in `LICENSE`
- Root-level `ca_profile.xml` with a non-empty `<Profile>`
- Docker app XML templates in `templates/`
- Each template includes `<Repository>`, `<Name>`, `<Overview>`, `<Project>`, `<Support>`, `<ReadMe>`, `<Icon>`, `<Category>`, `<WebUI>`, and `<TemplateURL>`
- No plugin wrapper XML files, because this repository publishes only a Docker app template

Use the official Unraid Community Applications submission portal:

<https://ca.unraid.net/submit>

Repository XML help:

<https://ca.unraid.net/submit/help/repository-xml>

Repository profile XML help:

<https://ca.unraid.net/submit/help/repository-info-xml>

XML field reference:

<https://ca.unraid.net/submit/help/xml-field-reference>

Builder guide:

<https://ca.unraid.net/submit/help/builders>

## Support

- LanLens project: <https://github.com/AlexRosbach/LanLens>
- LanLens issues: <https://github.com/AlexRosbach/LanLens/issues>
- MarketPlaceLens project: <https://github.com/AlexRosbach/MarketPlaceLens>
- MarketPlaceLens issues: <https://github.com/AlexRosbach/MarketPlaceLens/issues>
