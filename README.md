# checkout.directory

The open merchant registry for agentic commerce.

This repository contains the canonical list of merchants that support agentic commerce protocols like [UCP (Universal Checkout Protocol)](https://ucp.dev).

## What is this?

[checkout.directory](https://checkout.directory) is a directory service that helps AI agents discover merchants they can interact with programmatically. When an agent needs to help a user buy something, it can query this directory to find merchants that support standardized checkout protocols.

## For Agents

### Using the API

```bash
# List all merchants
curl https://checkout.directory/api/merchants

# Search merchants
curl https://checkout.directory/api/merchants?q=shoes

# Get merchant details
curl https://checkout.directory/api/merchants/allbirds.com

# Get merchant's UCP manifest
curl https://checkout.directory/api/merchants/allbirds.com/manifest
```

### Using skills.sh

```bash
npx skills add nekuda/checkout.directory
```

This installs the checkout.directory skill, teaching your agent how to discover and interact with merchants.

## For Merchants

Want to list your store? See [CONTRIBUTING.md](./CONTRIBUTING.md).

Requirements:
- Implement [UCP](https://ucp.dev) at `/.well-known/ucp`
- Submit a PR adding your merchant to `merchants.json`

## For Contributors

See [CONTRIBUTING.md](./CONTRIBUTING.md) for how to add merchants to the directory.

## Protocols

### UCP (Universal Checkout Protocol)

UCP enables AI agents to complete checkouts programmatically. Merchants expose a manifest at `/.well-known/ucp` describing their capabilities.

- Spec: [ucp.dev](https://ucp.dev)
- Capabilities: Product search, cart management, checkout, fulfillment tracking

### ACP (Agent Commerce Protocol)

Coming soon (no public discovery yet).

## Links

- Website: [checkout.directory](https://checkout.directory)
- API Docs: [checkout.directory/api-docs](https://checkout.directory/api-docs)
- UCP Spec: [ucp.dev](https://ucp.dev)
- ACP Spec: [Github](https://github.com/agentic-commerce-protocol/agentic-commerce-protocol)

## License

MIT
