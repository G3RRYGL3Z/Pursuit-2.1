# Pursuit-2.1
A replica of the Pursuit student dashboard (weekly curriculum view) with PRD-driven UI/UX improvements.

## PRD
- See the full product requirements doc in [PRD.md](PRD.md).

## Included improvements
- Priority tags (Required / Recommended / Optional) on each activity
- “Today’s Focus” panel (top priorities for the selected day)
- Daily + weekly progress bars (updates as you check items)
- Stronger primary CTAs for submissions
- Expand/collapse task details to reduce noise

## Added interaction features
- “Next best action” button (auto-scrolls to the top incomplete priority task)
- Lunch timer (Start/Pause/Reset) with end-of-lunch notifications + toast fallback
- Missed assignments attention pattern: pulsing pill + hourly reminder notifications/toasts

## Run locally
- `python3 -m http.server 8000`
- Open `http://localhost:8000/`

## Test mode (fast reminders/timers)
- Open `http://localhost:8000/?test=1` to enable a visible “Test mode ON” badge.
- In test mode: missed-assignment reminders run every ~10s and lunch timers default to ~20s.
