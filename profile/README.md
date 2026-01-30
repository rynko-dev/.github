# Rynko

**Document generation platform for developers.** Generate PDFs and Excel files from templates with a simple API.

## What We Build

- **Rendering Engine** - High-performance document generation with Yoga layout
- **Template Designer** - Visual editor for PDF and Excel templates
- **SDKs** - Node.js, Python, and Java libraries
- **Integrations** - Zapier, Make, n8n, Google Sheets

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

```javascript
import { Rynko } from '@rynko/sdk';

const client = new Rynko({ apiKey: 'your-api-key' });
const pdf = await client.documents.generatePdf({
  templateId: 'invoice-template',
  data: { customerName: 'Acme Corp', amount: 150.00 }
});
```

## Contributing

We welcome contributions! See our [Contributing Guide](https://github.com/rynko-dev/.github/blob/main/CONTRIBUTING.md).

## License

Our SDKs are open source under the MIT License.
