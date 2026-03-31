# Changelog

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


