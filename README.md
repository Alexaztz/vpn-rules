# VPN Unified Ruleset System

This repository is the single source of truth for multi-platform proxy routing rules.

It is designed for:

- Clash / Mihomo
- V2Ray / Xray clients such as v2rayN and v2rayNG
- Shadowrocket on iOS
- subconverter-based subscription generation

## Architecture

```text
GitHub rules repository
    ↓
subconverter
    ↓
subscription URLs
    ↓
clients: Clash / v2rayN / v2rayNG / Shadowrocket
```

## Core Policy

### Proxy

Always route these categories through the proxy:

- OpenAI / ChatGPT / Codex / Sora
- Claude / Anthropic
- Gemini / Google AI Studio
- Google services, including YouTube
- GitHub / GitHub Copilot
- Notion
- Streaming media, including YouTube, Netflix, Disney+, Max, Hulu and other overseas streaming services

### Direct

Bypass the proxy for:

- WeChat / Weixin
- Xiaohongshu
- Bilibili
- JD / Taobao / Tmall
- Tencent Cloud / Alibaba Cloud
- Local network and private IP ranges

## Security Notes

This repository must not store credentials or secrets.

Do not commit:

- VLESS links
- UUIDs
- Reality private keys
- 3X-UI credentials
- API tokens
- subscription tokens
- server panel paths

Server-specific bypass rules, such as the VPS IP address, should be kept in a local override file on the server rather than in this public repository.

## Update Model

Update rule files here, then refresh subscriptions in client apps or let clients refresh rule providers according to their configured interval.

Manual updates are acceptable and recommended during the build-out phase.
