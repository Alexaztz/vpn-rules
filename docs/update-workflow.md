# Update Workflow

## Manual update workflow

1. Edit a rule file in this repository.
2. Commit the change to `main`.
3. Refresh the subscription in each client, or wait for the client/provider refresh interval.
4. Verify routing by checking x-ui access logs.

## Do not commit secrets

Never commit:

- VLESS links
- UUIDs
- Reality private keys
- x-ui panel credentials
- subscription tokens
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

## Rule precedence

The intended order is:

1. system direct
2. domestic direct
3. AI / Google / GitHub / streaming proxy
4. GEOIP CN direct
5. final proxy
