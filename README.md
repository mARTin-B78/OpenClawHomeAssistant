# Papur (Clawdbot) Home Assistant Add-on (Draft)

This is a starter Home Assistant add-on wrapper to run **Clawdbot** as a Supervisor-managed container on **HAOS**.

## What this gives you
- Always-on Clawdbot instance on your HAOS host
- Separate bot identity (you will provide a new Telegram bot token)
- Persistent storage in `/data` inside the add-on (maps to HAOS add-on data folder)

## Notes / constraints
- This is a **headless** deployment; browser automation via Chrome-extension relay won’t be available.
- You can still do LAN automation (MikroTik/HA API, cron reminders, etc.).

## Install overview (high level)
1. Put this repo on GitHub (or local git).
2. In Home Assistant: **Settings → Add-ons → Add-on Store → ⋮ → Repositories**
3. Add the repo URL.
4. Install the add-on and configure the options.

## Configuration
You’ll set options in the add-on UI (Telegram token + optional HA token + MikroTik connection hints). See `papur-addon/config.yaml` schema.

### MikroTik key
For MikroTik access, put the private key file inside the add-on data folder:
- host path (HAOS): `/addon_configs/<addon_slug>/keys/mikrotik_papur_nopw`
- in-container path: `/data/keys/mikrotik_papur_nopw`

(Exact host path may vary; easiest is using File editor / Samba share to place the key under the add-on’s data directory.)

## Logs
View logs in the add-on UI.

## Next steps
If you want, I can tailor:
- default config for Telegram routing
- persistent memory paths
- optional Home Assistant token mounting (for HA integration skill)
