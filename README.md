# Anisette Server — Home Assistant Addon

Home Assistant addon repository for [anisette-v3-server](https://github.com/Dadoum/anisette-v3-server).

Used as anisette provider for [FindMy Fleet](https://github.com/luisreg81a/findmy-fleet) and similar integrations.

## Install

1. In Home Assistant: **Settings → Add-ons → Add-on Store → ⋮ → Repositories**
2. Add: `https://github.com/iblur01/anisette-ha-addon`
3. Install **Anisette Server**
4. Start the addon

The server listens on port **6969**.

## Usage

In FindMy Fleet setup, use:

```
http://homeassistant.local:6969
```

or replace `homeassistant.local` with your HA IP.

## Notes

- First start provisions Apple libraries automatically (takes ~30s, requires internet).
- Data persisted in addon `/data` volume across restarts.
- Based on [Dadoum/anisette-v3-server](https://github.com/Dadoum/anisette-v3-server).
