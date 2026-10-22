# M4B Fast Booking — First Come, First Served

## Policy
- MHmail is optional; not a dependency.
- No supervisor approval for routine bookings.
- The first valid booking atomically committed by the shared booking service wins.
- Booking statuses: REQUESTED, CONFIRMED, CONFLICT, CANCELLED, COMPLETED.
- Offline submissions remain REQUESTED, never CONFIRMED, until synchronized and accepted.
- A notification or WhatsApp message is not itself a booking confirmation.

## Flow
1. User selects date, start/end time, facility, group, trainer, and activity.
2. Server validates mandatory fields, time boundaries, facility availability and trainer conflicts.
3. In one transaction, server checks overlapping CONFIRMED bookings and commits a CONFIRMED reservation or returns CONFLICT.
4. On conflict, show available alternatives. Never silently override.
5. On confirmation, update shared calendar and send in-app notification.
6. Optionally share the confirmation through Android's share sheet to WhatsApp; never claim automated private-group posting.
7. Store timestamp, booking ID, creator and revision/cancellation history.

## Collision rule
Two confirmed bookings conflict when they reserve the same exclusive facility and:
  existing.start < requested.end AND requested.start < existing.end.
For multi-capacity facilities, enforce configured capacity rather than blanket exclusivity.

## Schedule capture
WhatsApp group notifications and manually shared schedules are imported as candidate planning data, not authoritative booking writes. Keep the 05:00 MYT daily snapshot for reporting, independently of live booking confirmations.

## Release gates
- Central authoritative storage and transactional collision prevention.
- Concurrent request tests, offline sync tests, cancellation/reschedule tests.
- Notification permission and Android 16 background behavior tests.
- APK build and device validation.

## Status
Architecture specification only. Not yet implemented or tested.
