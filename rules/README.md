# Rules Directory

All files in this directory use Clash classical rule-provider syntax unless otherwise noted.

A rule line normally looks like:

```text
DOMAIN-SUFFIX,example.com
DOMAIN,exact.example.com
IP-CIDR,10.0.0.0/8,no-resolve
```

The policy target, such as `PROXY` or `DIRECT`, is not written in these files. It is assigned by the consuming profile, for example:

```yaml
- RULE-SET,ai,PROXY
- RULE-SET,direct,DIRECT
```

## Files

- `app-direct.list`: Clash/Mihomo process rules for applications that must bypass the proxy; currently WorkBuddy.
- `app-proxy.list`: Clash/Mihomo process rules for applications that must be forced through the proxy; currently Google Antigravity and OpenAI Codex / ChatGPT on Windows.
- `ai.list`: OpenAI, Claude, Gemini, Notion and related AI services.
- `google.list`: Google full-service proxy rules, including YouTube domains.
- `github.list`: GitHub, GitHub Copilot, npm and developer service domains.
- `streaming.list`: overseas streaming media.
- `direct.list`: China/domestic services that should bypass proxy.
- `system-direct.list`: localhost and private network bypass rules.
- `local-overrides.example.list`: example only; keep real server-specific public IP rules private.

## Important

Do not store credentials, VLESS links, UUIDs, tokens, or Reality private keys here.

Application-level process rules must be evaluated before broad domain/category rules. In particular, `app-proxy` must precede domestic `direct`, otherwise a forced-proxy application could be captured by a domestic domain rule first.
