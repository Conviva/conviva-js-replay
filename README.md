# Conviva Replay

A standalone replay module for Conviva analytics that works with both npm and script tags.

## Installation

### NPM
```bash
npm install @convivainc/conviva-js-replay
```

### Script Tag
Conviva hosts sensor scripts on its CDN, allowing direct integration via <script> tags without needing a package manager. The CDN URLs follow the pattern below, where the version segment (e.g., v1.0.0, v1.0.1) should be replaced with the desired sensor version:

To use them, add a script tag to your HTML before DPI SDK intialization:

```js
<script src="https://sensor.conviva.com/replay/releases/v1.0.1/conviva-replay.umd.min.js"></script>
```

Conviva's CDN supports Brotli and gzip compression. When the browser sends the appropriate Accept-Encoding header (which modern browsers do by default), the CDN automatically serves a compressed response, reducing download size and improving load times with no additional configuration required.

## Usage

### NPM/ES Modules

#### Simple Usage (Recommended)
```typescript
import { init } from '@convivainc/conviva-js-replay';

// Just provide your customer key - that's it!
init('CONVIVA_ACCOUNT_CUSTOMER_KEY');
// INITIALISE CONVIVA-JS-APPP-ANALYTICS(https://github.com/Conviva/conviva-js-appanalytics) AFTER COHORT REPLAY INITIALISATION
```

### Script Tag

#### Simple Usage (Recommended)
```html
<script src= "<<URL / Path to conviva-replay.umd.min.js>>"></script>
<script>
  // Just provide your customer key - that's it!
  ConvivaReplay.init('CONVIVA_ACCOUNT_CUSTOMER_KEY');
  // INITIALISE CONVIVA-JS-SCRIPT-APPP-ANALYTICS(https://github.com/Conviva/conviva-js-script-appanalytics) AFTER COHORT REPLAY INITIALISATION
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

## Important configurations

### Content Security Policy (CSP): allow Web Workers (Blob)
Some environments enforce a strict Content Security Policy (CSP). The SDK uses a Web Worker created from a blob: URL, which requires explicitly allowing workers.
Add the following directive to your site’s Content-Security-Policy:
```typescript
Content-Security-Policy: worker-src 'self' blob:;
```
**Notes**
1. If your policy already includes worker-src, extend it to include blob:.
2. If worker-src is not defined, browsers may fall back to script-src, which can prevent worker creation.

### CORS: allow loading required external assets (CSS/SVG)
On many websites, required assets (commonly CSS files or SVGs) may be hosted on a different origin (domain/subdomain). If those assets are blocked by cross-origin restrictions, configure the hosting server/CDN to allow cross-origin access.
Ensure the asset server returns appropriate CORS response headers, such as:
```typescript
Access-Control-Allow-Origin: https://pulse.conviva.com
// If the host changes or a new host is introduced in the future, it should be allowed as well.
```
Or, if your security policy allows it:
```typescript
Access-Control-Allow-Origin: *
```

## Limitation

### Replay availability after tab close
If a user closes the browser tab after performing an activity, the last up to 1 minute of user activity per origin may not be available immediately.
This duration represents the maximum possible gap; in most cases, the unavailable replay segment will be less than 1 minute.
Replay data for that origin will resume only after the application is relaunched and the user returns to the same origin.

**Notes**
1. This limitation applies on a per-origin basis.
2. Once the user revisits the same origin, replay capture and availability continue as expected.
