# Update Workflow

## Manual update workflow

1. Edit a rule file in this repository.
2. Commit the change to `main`.
3. Refresh the subscription/profile in each client, or wait for the client/provider refresh interval when only existing provider contents changed.
4. Verify routing by checking the client connection/rule view and, when relevant, x-ui access logs.

When the provider list or top-level rule precedence changes, refresh/regenerate the whole Clash/Mihomo profile; refreshing only an already-existing provider is not sufficient.

## Do not commit secrets

Never commit:

- VLESS links
- UUIDs
- Reality private keys
- x-ui panel credentials
- API/subscription tokens
- panel paths
- real local-only override secrets

## Adding a new proxy domain

Add a line to one of:

```text
rules/ai.list
rules/google.list
rules/github.list
rules/streaming.list
```

Example:

```text
DOMAIN-SUFFIX,example.com
```

## Adding a new direct domain

Add a line to:

```text
rules/direct.list
```

Example:

```text
DOMAIN-SUFFIX,example.cn
```

## Adding application-level rules for Clash Verge / Mihomo

Use:

```text
rules/app-direct.list
rules/app-proxy.list
```

These use Clash classical process-rule syntax. Windows Clash Verge profiles should enable process matching with:

```yaml
find-process-mode: always
```

## Rule precedence

The intended order is:

1. system direct
2. explicit application direct (`app-direct`)
3. explicit application proxy (`app-proxy`)
4. domestic direct
5. AI / Google / GitHub / streaming proxy
6. GEOIP CN direct
7. final proxy

The application providers must come before broad domain/category rules. Otherwise a forced-proxy application could be captured by a domestic DIRECT rule before its process rule is evaluated.
