# Conviva Session Record

A standalone session recording module for Conviva analytics that works with both npm and script tags.

## Installation

### NPM
```bash
npm install @convivainc/conviva-js-replay
```

### Script Tag
```html
<script src="https://unpkg.com/@convivainc/conviva-replay/dist/conviva-replay.umd.min.js"></script>
```

## Usage

### NPM/ES Modules

#### Simple Usage (Recommended)
```typescript
import { init } from '@convivainc/conviva-js-replay';

// Just provide your customer key - that's it!
init('your-customer-key');
```

### Script Tag

#### Simple Usage (Recommended)
```html
<script src="https://unpkg.com/@convivainc/conviva-replay/dist/conviva-replay.umd.min.js"></script>
<script>
  // Just provide your customer key - that's it!
  ConvivaReplay.init('your-customer-key');
</script>
```

## API Reference

### Functions

#### `init(customerKey)`
**Recommended method** - Simple initialization with just a customer key.

**Parameters:**
- `customerKey` (string): Your Conviva customer key

**Example:**
```typescript
// Simple usage
init('your-customer-key');
```

## Browser Support

- Modern browsers with ES2018 support
- IndexedDB support
- Web Workers support
- AbortController support (with polyfill for older browsers)

## License

BSD-3-Clause
