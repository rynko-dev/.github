# Rynko

**Document generation & AI output validation platform for developers.** Generate PDFs and Excel files from templates. Validate AI outputs with schema-driven gates.

## What We Build

- **Rynko Render** - High-performance document generation with Yoga layout engine
- **Rynko Flow** - AI output validation gateway with schema gates, approvals, and webhook deliveries
- **Template Designer** - Visual editor for PDF and Excel templates
- **SDKs** - Node.js, Python, and Java libraries (documents + Flow)
- **Integrations** - Zapier, Make, n8n, Google Sheets, MCP

## Repositories

### SDKs

| SDK | Package | Description |
|-----|---------|-------------|
| [sdk-node](https://github.com/rynko-dev/sdk-node) | `@rynko/sdk` | Node.js/TypeScript SDK |
| [sdk-python](https://github.com/rynko-dev/sdk-python) | `rynko` | Python SDK with async support |
| [sdk-java](https://github.com/rynko-dev/sdk-java) | `dev.rynko:sdk` | Java SDK for JVM applications |

### Tools

| Repository | Description |
|------------|-------------|
| [mcp-server](https://github.com/rynko-dev/mcp-server) | Model Context Protocol server for AI assistants |
| [developer-resources](https://github.com/rynko-dev/developer-resources) | Sample templates, code examples, and tutorials |

### No-Code Integrations

| Repository | Description |
|------------|-------------|
| [zapier-rynko](https://github.com/rynko-dev/zapier-rynko) | Official Zapier integration |
| [make-rynko](https://github.com/rynko-dev/make-rynko) | Official Make.com (Integromat) integration |
| [n8n-rynko](https://github.com/rynko-dev/n8n-rynko) | Official n8n community node |

### Quick Links

| Resource | Link |
|----------|------|
| Documentation | [docs.rynko.dev](https://docs.rynko.dev) |
| Website | [rynko.dev](https://rynko.dev) |
| API Reference | [docs.rynko.dev/api-reference](https://docs.rynko.dev/api-reference) |

## Get Started

```bash
npm install @rynko/sdk
```

**Generate a document:**

```typescript
import { Rynko } from '@rynko/sdk';

const client = new Rynko({ apiKey: 'your-api-key' });
const job = await client.documents.generatePdf({
  templateId: 'invoice-template',
  variables: { customerName: 'Acme Corp', amount: 150.00 },
});
const completed = await client.documents.waitForCompletion(job.jobId);
console.log(completed.downloadUrl);
```

**Validate AI output with Flow:**

```typescript
const run = await client.flow.submitRun('gate_abc123', {
  input: { customerName: 'Acme Corp', amount: 150.00 },
});
const result = await client.flow.waitForRun(run.id);
console.log(result.status); // 'approved' | 'rejected'
```

## Contributing

We welcome contributions! See our [Contributing Guide](https://github.com/rynko-dev/.github/blob/main/CONTRIBUTING.md).

## License

Our SDKs are open source under the MIT License.
