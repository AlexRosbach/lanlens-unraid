# LanLens Unraid Template

Unraid Community Applications template for [LanLens](https://github.com/AlexRosbach/LanLens).

This repository contains only the Unraid Docker template metadata. The application code and Docker image stay in the main LanLens repository and Docker image.

## Template

- Template: [`templates/lanlens.xml`](templates/lanlens.xml)
- Repository profile: [`ca_profile.xml`](ca_profile.xml)
- Docker image: `alexrosbach/lanlens:latest`
- Template URL: <https://raw.githubusercontent.com/AlexRosbach/lanlens-unraid/main/templates/lanlens.xml>
- Default Web UI port: `7765`
- Appdata path: `/mnt/user/appdata/lanlens`
- Network mode: `host`
- Required capabilities: `NET_ADMIN`, `NET_RAW`

LanLens uses host networking because local ARP/MAC discovery needs raw network access on the Unraid host interface. The template also adds `NET_ADMIN` and `NET_RAW` for the same reason.

The template intentionally uses `alexrosbach/lanlens:latest` so Unraid users receive the current LanLens Docker image through normal container updates.

## First Startup

LanLens now starts without a manually supplied `SECRET_KEY`. On first startup, the container generates a strong key and stores it inside the persistent appdata volume at `/data/secret_key`.

Only set the optional `SECRET_KEY` template field when restoring or migrating an existing encrypted LanLens setup that must keep the same signing/encryption key.

The default admin password is only intended for first startup. Change it after login.

## Community Applications Submission

Current repository readiness checklist:

- Public GitHub repository
- OSI-approved MIT license in `LICENSE`
- Root-level `ca_profile.xml` with a non-empty `<Profile>`
- One Docker app XML template in `templates/`
- Template includes `<Repository>`, `<Name>`, `<Overview>`, `<Project>`, `<Support>`, `<ReadMe>`, `<Icon>`, `<Category>`, `<WebUI>`, and `<TemplateURL>`
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

- Project: <https://github.com/AlexRosbach/LanLens>
- Issues: <https://github.com/AlexRosbach/LanLens/issues>
