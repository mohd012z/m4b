# M4B — Notification and booking process flow

## Daily schedule
- Previous evening–04:59:59 MYT: receive candidate schedules for today's training.
- 04:30: notify coordinator if today's complete schedule is missing (planned).
- 04:45: flag trainer, group and facility overlaps and missing MHmail confirmations (planned).
- 05:00: cutoff. Do not treat new revisions as the official 05:00 snapshot.
- 05:01 onward: coordinator reviews the latest **complete** manually shared schedule, validates conflicts, and approves.
- Following approval: admin shares approved text to the private WhatsApp group manually.
- Later changes: retain as revisions; do not overwrite the cutoff snapshot.

## Booking state machine
DRAFT -> SUBMITTED -> VALIDATING -> CONFLICT_REVIEW -> APPROVED -> PUBLISHED -> COMPLETED

Exception states: REJECTED, CANCELLED, REVISED, MISSING_DATA.

## Conflict rules
- Overlapping bookings for the same trainer or physical facility require review.
- Group overlap may be legitimate split-group training; require explicit confirmation.
- Empty facility slots are unassigned, not confirmed available.
- MHmail Calendar is the authoritative booking confirmation source where applicable.
- Training planned is not the same as training completed.

## Reporting
- Monday: previous week's approved planned sessions.
- First of month: previous month's approved planned sessions.
- Preserve revision history and label actual completion separately.

## Privacy and reliability
- Use explicit Android notification access consent.
- Capture only notifications matching the authorized training group; the title alone is not a secure group identifier.
- WhatsApp notifications may be truncated or missed; use Android Share to import complete schedule text.
- No general official API exists to read arbitrary private WhatsApp group history.
- No automatic WhatsApp group posting is included.

## Implementation status
This file is an **operational design**, not proof that the notification scheduler, booking state machine, conflict engine, or Android APK has been implemented. The existing v0.6 prototype source remains to be imported and compiled.
