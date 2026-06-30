# Mihomo / Clash Mainline

Mihomo is the preferred main routing engine for this repository.

This repository stores only public rule logic. Device-specific node credentials must stay local and must not be committed.

## Public rule source

The following public rules are consumed as `rule-providers`:

```text
rules/system-direct.list
rules/direct.list
rules/ai.list
rules/google.list
rules/github.list
rules/streaming.list
```

## Local private data

Keep these outside GitHub:

```text
VLESS links
UUIDs
Reality keys
server public IP
management panel path
subscription tokens
```

## Intended architecture

```text
GitHub public rules
    ↓
Mihomo rule-providers
    ↓
Local device-specific Mihomo profiles
    ↓
PC / Android / backup clients
```

## Rule update model

Rule files in GitHub can be updated manually. Mihomo clients refresh rule providers according to the configured `interval`, or immediately when the client refreshes providers manually.

Node credentials rarely change. When they do, regenerate the local device profile instead of committing secrets to GitHub.
