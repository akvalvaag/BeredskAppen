# BeredskAppen requirements specification

## Purpose

BeredskAppen is an offline-first, bilingual web app that helps Norwegian households prepare to manage for one week during an emergency. It gives a household a clear readiness overview, tracks supplies and expiry dates, identifies purchase gaps, records important plans, and offers concise offline emergency guidance.

## Users and boundaries

- Primary users: people managing emergency preparedness for a household in Norway.
- Initial languages: Norwegian Bokmål and English.
- Initial storage: local to the browser/device. The MVP has no account, cloud sync, or live-alert service.
- The app is a preparedness aid, not emergency, medical, or live authority advice. Users must follow official authority instructions in a real incident.

## Source baseline

The DSB leaflets in `docs/reference/` are the source for the initial checklist and guidance:

- Aim to be self-sufficient for one week.
- Store approximately 20 litres of drinking water per household member.
- Cover water; food and cooking; heat and light; information and communications; medicines and first aid; hygiene; payments; and household planning/preparedness buddies.
- Account for children, pets, special diets, medicines, and medical aids.

All guidance derived from an authority source must retain a source name and review date.

## Functional requirements

### Household profile

1. A user can record household size and optional household circumstances, including children, pets, dietary needs, heating/cooking options, a preparedness buddy, and alternative accommodation.
2. The app calculates a drinking-water target of 20 litres per household member.
3. On first access, the app guides a user through household setup before the DSB checklist, then requires an explicit completion action before opening the dashboard.

### Readiness and shopping

1. The dashboard shows water held versus target, category status, upcoming expiry items, and a next action.
2. Drinking water is managed through a dedicated litres-and-location workflow rather than as general inventory. The water total includes any legacy water inventory records.
3. The app includes a DSB-derived baseline checklist, with guided setup for water, food, cooking, heat, light, information, medicines, hygiene, payments, children, and pets.
4. Checklist items can be recorded as available, needed, or not relevant. Child and pet items appear only when relevant to the household profile.
5. Marking a checklist gap as needed adds it to the shopping list; recording it as available or not relevant removes that checklist-generated shopping entry.
6. Users can create, edit, and remove inventory batches.
7. Each batch has a name, category, quantity, unit, consumable/equipment type, optional expiry/review date, optional storage location, and notes.
8. The shopping list records missing or replacement supplies and supports completion.
9. Completing a shopping-list item offers to add it to supplies using pre-filled details; water items use the dedicated water workflow.

### Rotation

1. The app groups dated batches as expired, use this week, use this month, or review soon.
2. Marking a batch as used reduces/removes it and offers a replacement item for the shopping list.
3. Multiple batches of the same product may have different expiry dates and locations.
4. The app maintains local review routines for power banks, radio/batteries, medicines, water storage, household plans, and alternative heating. Completing a routine schedules its next review.

### QR-labelled storage locations

1. Users can create storage locations for boxes, shelves, cupboards, rooms, and vehicles, with optional parent locations.
2. Every location has a random local token and a human-readable short code.
   - Root locations use `TYPE-AREA-##`, such as `ROOM-BSMNT-01`.
   - Child locations inherit the nearest room area and use `AREA-TYPE-##`, such as `BSMNT-SHELF-01`.
   - `AREA` is a four- or five-character, vowel-reduced version of the location name; the trailing number increments only when that identifier base already exists.
3. The app provides a printable label with a QR code, location name, and short code.
4. A user can enter a short code or scan a QR label to open the matching location and view, add, or check its inventory.
5. QR codes must contain only a random location token; they must not contain an address, household details, or inventory data.
6. The location workflow must have a manual fallback when camera scanning is unavailable.

### Emergency reference and plans

1. The app provides concise, cached guidance for power outages, water outages, evacuation, communications loss, and information verification.
2. Norwegian emergency numbers 110, 112, 113, and 14 12 are immediately available.
3. Users can store important contacts and practical plan notes locally.
4. The app offers a printable household plan for use without a device, including water status, contacts, emergency numbers, preparedness arrangements, important home locations, storage locations, checklist gaps, and the next review.
5. Scenario mode provides offline, DSB-based action guidance for power outages, water outages, evacuation, communications loss, and extreme cold. Each scenario shows relevant recorded supplies, their storage locations, emergency numbers, and household-specific plan information.

## Non-functional requirements

- The installable PWA works after its first successful load without a network connection.
- Personal data remains on-device in the MVP.
- The UI is responsive, keyboard-accessible, and clear under stressful conditions.
- Local data must persist across normal app reloads.
- A persistent low-power mode provides a high-contrast OLED-friendly presentation, with solid colours and no animations or gradients.
- The app provides no fear-based score and uses clear, actionable status labels.

## Initial acceptance criteria

- A household can set its member count and immediately see its water target.
- A user can add water inventory and see the dashboard total change.
- A dated food item appears in the appropriate rotation group.
- A user can create a labelled storage location, open it via its short code, and view its assigned item.
- The emergency page remains available offline after installation.

## Future scope

- Encrypted household sharing and sync.
- Device notifications.
- Camera-assisted QR location scanning where supported.
- Location transfer and dedicated stock-check mode.
- Printable household plan and label packs.
