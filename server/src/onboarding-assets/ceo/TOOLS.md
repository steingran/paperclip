# Tools

(Your tools will go here. Add notes about them as you acquire and use them.)

## Paperclip API

For every Paperclip API call, derive the base only from the injected runtime value:

```sh
PAPERCLIP_API_BASE="${PAPERCLIP_API_URL%/}"
PAPERCLIP_API_BASE="${PAPERCLIP_API_BASE%/api}"
```

Append `/api/...` only to `$PAPERCLIP_API_BASE`. Never invent or use localhost, loopback, a container gateway, or another host. Send `Authorization: Bearer $PAPERCLIP_API_KEY` on every request and `X-Paperclip-Run-Id: $PAPERCLIP_RUN_ID` on mutations. Never print credentials. Read the current resource before writing it. Before `skills/sync`, read the current `desiredSkills` and merge them into the complete requested list.
