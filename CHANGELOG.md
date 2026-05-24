# Changelog

## 1.0.4 (24/MAY/2026)
* **Live clientId update — keep replay in the same Conviva session as DPI when the clientId changes mid-session.** The SDK now reacts to mid-session changes to `Conviva.sdkConfig.clId` — detected via storage events on the DPI cookie, the `ConvivaClientIdChanged` `window` CustomEvent that DPI fires when its native WebView bridge resolves, and a `visibilitychange` fallback. On detection the SDK: drains all pending events and blobs under the OLD signed upload policy + OLD `clId` so the trailing segment of the old recording lands at the correct GCS path; hot-swaps the worker's `clId`; invalidates the cached upload policy (in memory and in IndexedDB) so the next upload re-fetches with the new clId; and forces a fresh rrweb full snapshot so the new clId's recording segment begins from a complete DOM state. Recording continues uninterrupted — no worker restart, no re-sampling, no `recordId` regeneration.
* **`Conviva_sdkConfig` cookie now preferred over `localStorage`.** `getSdkConfig()` reads the `Conviva_sdkConfig` cookie first (which DPI sets when `enableClIdInCookies` is enabled — the default since DPI v2.1.0) and only falls back to the `Conviva.sdkConfig` localStorage entry when no cookie is present. This is what lets replay immediately share the same clientId DPI selected (via its WebView bridge or native cookie write) without waiting for the localStorage backfill.
* **Compatibility:** This release is the required pair for DPI SDK v2.2.0 and later. Earlier replay versions will not react to DPI's mid-session clientId changes and the replay session will be detached from the DPI session.

## 1.0.3 (01/APR/2026)
* Fixed issue where cohort replay recording status was not set due to race condition
* Fixed issue when cohort replay was initialized for the first time after local storage available due to race condition.
* Enhanced failure handling

## 1.0.2 (17/MAR/2026)
* Resolved an issue in the sampling logic to ensure more accurate and consistent data representation.
* Introduced diagnostic information tracking for cohort replay

## 1.0.1 (28/JAN/2026)
* Enhanced data upload logic
* Partial support for Shadow DOM open mode
* Bug fixes

## 1.0.0 (19/DEC/2025) – Initial Release

### Added
- Standalone **Cohort Replay Plugin** providing cohort replay functionality.
- Support for replaying user cohorts previously available in the conviva-js-appanalytics SDK.

### Notes
- This plugin contains the Cohort Replay functionality that was bundled with the SDK up to version 1.5.1.
- Designed to work alongside SDK version 1.5.2 and later.

### Compatibility
- Compatible with SDK >= 1.5.2


