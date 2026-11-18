# Repository guidance

## Product

This repository contains BeredskAppen, a local-first emergency-preparedness PWA for Norwegian households. The DSB PDFs under `docs/reference/` are reference material and must not be modified.

## Engineering principles

- Keep the app usable offline and without an account.
- Do not transmit household, medical, contact, location, or inventory data unless a future feature explicitly obtains consent.
- QR labels must use opaque random location tokens only; never encode personal or inventory data.
- Preserve Norwegian Bokmål and English parity for user-facing additions.
- Attribute authority-derived guidance and retain a review date. Do not make the app appear to provide medical, emergency, or live-alert advice.
- Prefer calm, direct, accessible language and actionable readiness status over fear-based scoring.

## Verification

- Test core workflows with network access disabled after the first load.
- Verify keyboard navigation, small-screen layouts, and local data persistence.
- Keep manual paths for any camera or hardware-assisted feature.
- Do not add external dependencies or services without documenting the privacy, offline, maintenance, and licensing impact.
