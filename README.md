<p align="center">
  <img src="https://rynko.dev/logo.svg" alt="Rynko" width="200" />
</p>

<h1 align="center">Rynko</h1>

<p align="center">
  <strong>Document Infrastructure & AI Output Validation for Developers</strong><br/>
  Generate pixel-perfect PDFs and Excel files from templates. Validate AI outputs with schema-driven gates.
</p>

<p align="center">
  <a href="https://rynko.dev">Website</a> •
  <a href="https://docs.rynko.dev">Documentation</a> •
  <a href="https://docs.rynko.dev/api-reference">API Reference</a> •
  <a href="https://app.rynko.dev/signup">Get Started</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/generation-200--500ms-brightgreen" alt="Generation Speed" />
  <img src="https://img.shields.io/badge/uptime-99.9%25-blue" alt="Uptime" />
  <img src="https://img.shields.io/badge/formats-PDF%20%7C%20Excel-orange" alt="Formats" />
  <img src="https://img.shields.io/badge/Flow-AI%20Validation-purple" alt="Rynko Flow" />
</p>

---

## Why Rynko?

### Rynko Render — Document Generation

Traditional PDF generation is slow and fragile. HTML-to-PDF libraries require headless browsers, take 3-8 seconds per document, and produce inconsistent results.

- **Sub-second generation** — 200-500ms typical (10-15x faster than HTML-to-PDF)
- **Native rendering engine** — No browser overhead, no HTML parsing
- **Yoga Layout** — Facebook's Flexbox engine (same as React Native) for pixel-perfect layouts
- **Zero XSS surface** — JSON-based TextRuns instead of HTML for rich text
- **Dual output** — PDF and Excel from the same template

### Rynko Flow — AI Output Validation

AI agents generate structured data, but you can't ship it without validation. Flow is a validation gateway that sits between your AI and production systems.

- **Schema gates** — Define JSON Schema with business rules; every AI output is validated before delivery
- **Human-in-the-loop approvals** — Flag runs for manual review when conditions are met
- **Webhook deliveries** — Deliver validated outputs to downstream systems with automatic retries
- **SDK support** — Submit runs, poll results, and manage approvals from Node.js, Python, or Java
- **MCP integration** — AI agents can validate their own outputs via MCP tools

## Quick Start

### REST API

```bash
curl -X POST https://api.rynko.dev/api/v1/documents/generate \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "templateId": "invoice-template",
    "format": "pdf",
    "variables": {
      "invoiceNumber": "INV-2026-001",
      "customerName": "Acme Corp",
      "items": [
        { "description": "Consulting", "quantity": 10, "price": 150.00 }
      ],
      "total": 1500.00
    }
  }'
```

### Node.js SDK

```bash
npm install @rynko/sdk
```

```typescript
import { Rynko } from '@rynko/sdk';

const client = new Rynko({ apiKey: 'YOUR_API_KEY' });

const result = await client.documents.generate({
  templateId: 'invoice-template',
  format: 'pdf',
  variables: {
    invoiceNumber: 'INV-2026-001',
    customerName: 'Acme Corp',
    items: [{ description: 'Consulting', quantity: 10, price: 150.00 }],
    total: 1500.00
  }
});

console.log(result.downloadUrl);
```

### Python SDK

```bash
pip install rynko
```

```python
from rynko import RynkoClient

client = RynkoClient(api_key="YOUR_API_KEY")

result = client.documents.generate(
    template_id="invoice-template",
    format="pdf",
    variables={
        "invoiceNumber": "INV-2026-001",
        "customerName": "Acme Corp",
        "items": [{"description": "Consulting", "quantity": 10, "price": 150.00}],
        "total": 1500.00
    }
)

print(result.download_url)
```

## AI-Native Workflow (MCP)

Connect Claude, Cursor, or any MCP-compatible AI agent directly to Rynko:

```json
{
  "mcpServers": {
    "rynko": {
      "command": "npx",
      "args": ["-y", "@rynko/mcp-server"],
      "env": {
        "RYNKO_USER_TOKEN": "your-personal-access-token"
      }
    }
  }
}
```

Then just ask: *"Create an invoice template for consulting services with VAT"*

## Rynko Flow — Quick Start

Submit AI-generated data to a gate for validation:

### Node.js

```typescript
import { Rynko } from '@rynko/sdk';

const client = new Rynko({ apiKey: 'YOUR_API_KEY' });

// Submit a run for validation
const run = await client.flow.submitRun('gate_abc123', {
  input: {
    customerName: 'Acme Corp',
    amount: 1500.00,
    currency: 'USD',
  },
});

// Wait for the result
const result = await client.flow.waitForRun(run.id);

if (result.status === 'approved') {
  console.log('Validated!', result.output);
} else {
  console.log('Rejected:', result.errors);
}
```

### Python

```python
from rynko import Rynko

client = Rynko(api_key="YOUR_API_KEY")

run = client.flow.submit_run(
    "gate_abc123",
    input={"customerName": "Acme Corp", "amount": 1500.00, "currency": "USD"},
)

result = client.flow.wait_for_run(run["id"])
print(f"Status: {result['status']}")
```

### Java

```java
FlowRun run = client.flow().submitRun("gate_abc123",
    SubmitRunRequest.builder()
        .inputField("customerName", "Acme Corp")
        .inputField("amount", 1500.00)
        .inputField("currency", "USD")
        .build()
);

FlowRun result = client.flow().waitForRun(run.getId());
System.out.println("Status: " + result.getStatus());
```

## Features

| Feature | Description |
|---------|-------------|
| **28 Component Types** | Text, tables, charts, QR codes, barcodes, form fields, and more |
| **8 Chart Types** | Bar, line, pie, doughnut, area, radar, polar area, scatter |
| **10 Barcode Formats** | Code128, Code39, EAN-13/8, UPC-A/E, ITF-14, PDF417, DataMatrix, QR |
| **9 PDF Form Fields** | Text, textarea, checkbox, radio, dropdown, date, signature, button |
| **Hybrid Logic** | Server-side JavaScript expressions + native Excel formulas |
| **Visual Designer** | Drag-and-drop template builder with live preview |
| **Batch Generation** | Generate thousands of documents in parallel |
| **Webhooks** | Real-time notifications for document events |
| **Flow Gates** | Schema + business rule validation for AI outputs |
| **Flow Approvals** | Human-in-the-loop review for flagged runs |
| **Flow Deliveries** | Webhook delivery with automatic retries |

## Integrations

| Platform | Package | Description |
|----------|---------|-------------|
| **Node.js** | [`@rynko/sdk`](https://github.com/rynko-dev/sdk-node) | Official TypeScript SDK |
| **Python** | [`rynko`](https://github.com/rynko-dev/sdk-python) | Official Python SDK |
| **Java** | [`dev.rynko:sdk`](https://github.com/rynko-dev/sdk-java) | Official Java SDK |
| **MCP Server** | [`@rynko/mcp-server`](https://github.com/rynko-dev/mcp-server) | AI agent integration |
| **Zapier** | [Rynko for Zapier](https://github.com/rynko-dev/zapier-rynko) | No-code automation |
| **Make.com** | [Rynko for Make](https://github.com/rynko-dev/make-rynko) | Visual automation |
| **n8n** | [n8n-nodes-rynko](https://github.com/rynko-dev/n8n-rynko) | Workflow automation |
| **Google Sheets** | Add-on | Generate documents from spreadsheet data |

## Pricing

**Flow (included in all plans):**

| Tier | Flow Runs/Month | Price |
|------|-----------------|-------|
| **Free** | 500 | $0/month |
| **Starter** | 10,000 | $29/month |
| **Growth** | 100,000 | $99/month |
| **Scale** | 500,000 | $349/month |

**Render Packs (add-on for document generation):**

| Pack | Documents/Month | Price |
|------|-----------------|-------|
| **Basic** | 500 | +$19/month |
| **Pro** | 2,000 | +$49/month |
| **Business** | 10,000 | +$119/month |

[View full pricing →](https://rynko.dev/pricing)

## Resources

- **Documentation**: [docs.rynko.dev](https://docs.rynko.dev)
- **API Reference**: [docs.rynko.dev/api-reference](https://docs.rynko.dev/api-reference)
- **Template Schema**: [docs.rynko.dev/developer-guide/template-schema](https://docs.rynko.dev/developer-guide/template-schema)
- **Status Page**: [status.rynko.dev](https://status.rynko.dev)

## LLM Context Files

For AI assistants and code generation tools:

- [`llms.txt`](https://rynko.dev/llms.txt) — Compact overview
- [`llms-full.txt`](https://rynko.dev/llms-full.txt) — Comprehensive reference
- [`llms-templates.txt`](https://rynko.dev/llms-templates.txt) — Template schema for AI

## Security

- **TLS 1.3** encryption for all API calls
- **Signed URLs** with configurable expiration
- **GDPR compliant** with data removal support
- **SOC 2 Type II** certification in progress

## Support

- **Email**: support@rynko.dev
- **Documentation**: [docs.rynko.dev](https://docs.rynko.dev)
- **Status**: [status.rynko.dev](https://status.rynko.dev)

---

<p align="center">
  <sub>Built by <a href="https://rynko.dev">Rynko</a> — Document Infrastructure & AI Output Validation for Developers</sub>
</p>
