# WhatsApp group booking template

Post the template in the training group and replace [BOOKING URL] with the live, deployed M4B booking page after backend verification.

📅 MABA TRAINING SLOT BOOKING
Date: [DATE]
Facilities: CEET B737/A330, Wet Drill, Fire & Smoke, Door Trainers B737/A330/A350, Room 205/206.
Time slots (configurable): 08:30–10:00, 10:00–11:30, 11:30–13:00, 14:00–15:30, 15:30–17:00.
Open [BOOKING URL], choose facility and time, enter instructor and group, submit.
Only a CONFIRMED response from the shared booking server means the slot is reserved.
No supervisor approval for authorized users.

## Engineering gates
- Authenticated instructors and shared transactional storage.
- Server-side no-overlap constraints; concurrent booking test.
- Confirmed booking ID and timestamp.
- Slot availability refreshed on every booking; cancellation and change audit.
- Notification to instructor and optionally group via manual WhatsApp share.
- Group poll alone cannot guarantee a booking.
- Static HTML demo is not a live booking system.
