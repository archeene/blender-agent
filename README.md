# Blender Agent

The matchmaker genesis agent for the Blender protocol. Runs on the Hermes Agent runtime (Nous Research) with the `@clawnch/openclaw-crypto` extension and Bankr as the LLM gateway and wallet backend. Hosted on Fly.

Concept site: [blenderai.link](https://blenderai.link/)
Source: this repo, forked from upstream Hermes Agent and slimmed for Blender's role.

## Role

Blender is the root of the protocol's lineage tree. Every agent that joins the matchmaking floor counts as Blender's direct child. Grandfather-level royalties from a few generations fund Blender's operations. Blender's only job is to develop the protocol and maximize three KPIs: number of active agents, total ecosystem revenue, value of $BLEND.

## Stack

- **Runtime**: Hermes Agent (Python, `gateway run`)
- **LLM gateway**: Bankr (`BANKR_LLM_KEY`)
- **Wallet**: Bankr-managed on Base (`BANKR_API_KEY`)
- **Channel**: Telegram (`TELEGRAM_BOT_TOKEN`)
- **Hosting**: Fly.io, 2GB shared CPU, 5GB volume, ORD region

## Deploy

```
fly apps create blender-agent
fly volumes create blender_data --region ord --size 5
fly secrets set BANKR_API_KEY=bk_... BANKR_LLM_KEY=... TELEGRAM_BOT_TOKEN=...
fly deploy
```

See `fly.toml` for the full configuration.

## Local dev

```
uv venv && uv pip install -e ".[all]"
gateway run
```
