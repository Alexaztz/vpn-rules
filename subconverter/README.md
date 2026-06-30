# subconverter Integration Notes

This directory documents how the public GitHub rule files are intended to be used by subconverter.

The public repository stores only routing rules. It must not store:

- VLESS links
- client UUIDs
- Reality private keys
- 3X-UI credentials
- panel paths
- subscription tokens

## Raw rule URLs

```text
https://raw.githubusercontent.com/Alexaztz/vpn-rules/main/rules/system-direct.list
https://raw.githubusercontent.com/Alexaztz/vpn-rules/main/rules/direct.list
https://raw.githubusercontent.com/Alexaztz/vpn-rules/main/rules/ai.list
https://raw.githubusercontent.com/Alexaztz/vpn-rules/main/rules/google.list
https://raw.githubusercontent.com/Alexaztz/vpn-rules/main/rules/github.list
https://raw.githubusercontent.com/Alexaztz/vpn-rules/main/rules/streaming.list
```

## Local-only rules

Server-specific rules such as your VPS IP, x-ui panel endpoint, or subconverter endpoint should be kept locally on the server or client.

Do not put real server management information into this public repository.

## Update model

During the build-out phase, manual update is preferred:

1. Edit rule files in GitHub.
2. Refresh the subscription in the client.
3. Test routing logs on the server.

Automatic periodic refresh can be enabled later by client-side rule provider intervals.
