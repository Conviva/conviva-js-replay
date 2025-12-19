# Conviva Replay

A standalone replay module for Conviva analytics that works with both npm and script tags.

## Installation

### NPM
```bash
npm install @convivainc/conviva-js-replay
```

### Script Tag
```html
<script src= "<<URL / Path to conviva-replay.umd.min.js>>"></script>
```

## Usage

### NPM/ES Modules

#### Simple Usage (Recommended)
```typescript
import { init } from '@convivainc/conviva-js-replay';

// Just provide your customer key - that's it!
init('CONVIVA_ACCOUNT_CUSTOMER_KEY');
```

### Script Tag

#### Simple Usage (Recommended)
```html
<script src= "<<URL / Path to conviva-replay.umd.min.js>>"></script>
<script>
  // Just provide your customer key - that's it!
  ConvivaReplay.init('CONVIVA_ACCOUNT_CUSTOMER_KEY');
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
init('CONVIVA_ACCOUNT_CUSTOMER_KEY');
```
