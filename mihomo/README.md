# Mihomo / Clash Mainline

Mihomo is the preferred main routing engine for this repository.

This repository stores only public rule logic. Device-specific node credentials must stay local and must not be committed.

## Public rule source

The following public rules are consumed as `rule-providers`:

```text
rules/system-direct.list
rules/app-direct.list
rules/app-proxy.list
rules/direct.list
rules/ai.list
rules/google.list
rules/github.list
rules/streaming.list
```

For Windows / Clash Verge TUN profiles that use the application-level rules, use `find-process-mode: always` so process matching is deterministic. The repository Clash template sets this explicitly.

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

## Application-level precedence

The intended Windows / Clash order is:

```text
system-direct -> DIRECT
app-direct    -> DIRECT
app-proxy     -> PROXY
domestic      -> DIRECT
AI/Google/... -> PROXY
GEOIP CN      -> DIRECT
final         -> PROXY
```

This ensures WorkBuddy remains direct under TUN while Google Antigravity is forced through the proxy before a domestic-domain rule can short-circuit it.

## Rule update model

Rule files in GitHub can be updated manually. Mihomo clients refresh rule providers according to the configured `interval`, or immediately when the client refreshes providers manually.

When the provider list or top-level precedence changes, refresh/regenerate the whole Clash subscription/profile rather than refreshing only an already-existing provider.

Node credentials rarely change. When they do, regenerate the local device profile instead of committing secrets to GitHub.
