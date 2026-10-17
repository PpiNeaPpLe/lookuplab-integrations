# LookupLab integrations

[![M8ven Score](https://m8ven.ai/badge/mcp/ppineapple-lookuplab-integrations-czyq6i?v=6214a60100c0b57734ab1289d926b17e)](https://m8ven.ai/mcp/ppineapple-lookuplab-integrations-czyq6i?s=readme)

Phone carrier, email-domain, IP-network and DNS checks through [LookupLab](https://lookuplab.io/mcp/).

Find LookupLab on [Smithery](https://smithery.ai/servers/jude/lookuplab) and in the [official MCP Registry](https://registry.modelcontextprotocol.io/v0.1/servers/io.github.PpiNeaPpLe%2Flookuplab/versions/1.0.0).

## Claude web and Desktop

1. Open **Customize > Connectors > Add custom connector**. Name it LookupLab and use `https://lookuplab.io/api/mcp`.
2. Choose **Sign in now** and **Register automatically** if Claude shows authentication options. Leave a custom client ID and secret blank.
3. On LookupLab's consent page, enter your [LookupLab key](https://lookuplab.io/dashboard/) and approve. Enable the connector in your chat. Try: "Check the mail records for example.com."

Your key goes only to LookupLab; Claude receives a revocable OAuth connection. On Team and Enterprise plans, an owner first adds the connector, then each member connects their account. See [Claude's connector setup](https://claude.com/docs/connectors/custom/add-unlisted).

## Claude Code

Set `LOOKUPLAB_API_KEY` privately in your environment, then merge [claude-code.mcp.json](claude-code.mcp.json) into your project's `.mcp.json`. Start Claude Code in that project, approve LookupLab when prompted, and check `/mcp`. Keep the variable reference in the file; never replace it with a real key in a shared repository.

The config uses Claude Code's [HTTP transport and environment expansion](https://code.claude.com/docs/en/mcp). Try: "Check the mail records for example.com."

## Gemini CLI

Install with `gemini extensions install https://github.com/PpiNeaPpLe/lookuplab-integrations`. Supply your existing LookupLab API key in the extension's sensitive setting. Gemini stores this setting in its system keychain when available. Never put a key in a chat message.

## Other MCP clients

Connect to `https://lookuplab.io/api/mcp` with `Authorization: Bearer YOUR_API_KEY` or `X-API-Key: YOUR_API_KEY` in the client's secure connection settings. The server uses Streamable HTTP with JSON responses and no SSE stream.

## ChatGPT and Codex

The `openai/` directory is the portable plugin package. OAuth needs an exact callback registered by LookupLab before the platform connection can run. This source package is not a claim of directory approval or publication.

## Tools and costs

| Tool | Checks | Account credits |
| --- | --- | --- |
| `phone_lookup` | Carrier, line type; optional caller name | 1 for landline/VoIP/toll-free, 3 mobile/unknown; caller name adds 2 |
| `email_verify` | Syntax, MX and domain indicators | 1 |
| `ip_lookup` | Approximate location and network | 1 |
| `dns_check` | MX, SPF, DMARC or DKIM | 1 |

The account needs enough balance for the maximum charge before the lookup runs. Failed/invalid results are not charged. Tools debit credits, so they are marked as operations with side effects. Duplicate calls may charge again unless your client sends a stable `Idempotency-Key` header for retries.

Data is not proof of a person's identity, ownership, consent to contact, guaranteed email delivery or precise location. Privacy flags can be unavailable. Supply only data you are authorized to check.

[Privacy](https://lookuplab.io/privacy/) · [Terms](https://lookuplab.io/terms/) · [Support](https://lookuplab.io/contact/)
