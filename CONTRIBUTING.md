# Contributing to checkout.directory

Thank you for helping grow the agentic commerce ecosystem!

## Adding a Merchant

### Prerequisites

Before adding a merchant, ensure they have a working UCP endpoint:

```bash
curl https://example.com/.well-known/ucp
```

This should return a valid JSON manifest.

### Steps

1. **Fork this repository**

2. **Edit `merchants.json`**

   Add your merchant to the `merchants` array:

   ```json
   {
     "domain": "example.com",
     "name": "Example Store",
     "category": "Fashion",
     "protocols": ["ucp"]
   }
   ```

3. **Submit a Pull Request**

   - Use a descriptive title: "Add Example Store"
   - Include a link to verify the UCP endpoint works

4. **Wait for Review**

   Our CI will validate your entry. A maintainer will review and merge.

## Validation Rules

Your entry must pass these checks:

| Field | Requirements |
|-------|-------------|
| `domain` | Valid domain format, no `https://`, no trailing slash, unique |
| `name` | 1-100 characters |
| `category` | 1-50 characters, free-form text |
| `protocols` | Array containing `"ucp"` and/or `"acp"` |

### Valid Examples

```json
{"domain": "store.com", "name": "Store", "category": "Fashion", "protocols": ["ucp"]}
{"domain": "shop.example.com", "name": "My Shop", "category": "Electronics", "protocols": ["ucp", "acp"]}
```

### Invalid Examples

```json
{"domain": "https://store.com", ...}     // No https://
{"domain": "store.com/", ...}            // No trailing slash
{"domain": "store", ...}                 // Must be valid domain
{"protocols": [], ...}                   // Must have at least one protocol
```

## Categories

Categories are free-form text. Use existing categories when possible:

- Fashion
- Footwear
- Beauty
- Electronics
- Home/Bedding
- Travel/Luggage
- Activewear
- Fitness Apparel
- Accessories
- Baby/Children
- Music/Instruments
- Audio
- Apparel
- Mattresses
- Grooming

Or create a new one that fits.

## Questions?

Open an issue if you have questions or need help.
