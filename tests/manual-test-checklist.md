# Manual Test Checklist

## Schedule

- Ask: What court slots are free today?
- Verify GPT calls getReservations.
- Verify GPT shows all 9 slots.
- Verify free and occupied slots are displayed correctly.

- Ask: `Show this week’s court schedule`
- Verify GPT shows dates as columns.
- Verify GPT shows slot start times as rows.
- Verify free cells use `🟢`.
- Verify occupied cells use `🔴 Name`.

## Booking

- Ask to book a free slot.
- Verify GPT asks for name/apartment if missing.
- Verify GPT does not book an occupied slot.
- Verify GPT creates reservation only after checking current reservations.
- Verify GPT shows updated schedule after booking.
- Verify new reservations use `codigo` in format `GPT_YYYYMMDD_HHMMSS`.

## Cancellation

- Ask to cancel own reservation.
- Verify GPT checks apartment before cancellation.
- Try cancelling another apartment's reservation.
- Verify GPT refuses.
- Verify GPT shows updated schedule after cancellation.
- Verify GPT uses `acf.codigo_cancelacion_reservas` from the matching reservation.
- Verify GPT does not hardcode `codigo="1"` for cancellation.

## Rescheduling

- Ask to move an existing reservation to a free slot.
- Verify old reservation belongs to same apartment.
- Verify new slot is free before cancellation.
- Verify GPT does not cancel old reservation if new slot is occupied.

## Limits

- Verify GPT refuses a second reservation for the same apartment on the same day.
- Verify GPT refuses a fourth reservation for the same apartment in the same calendar week.
- Verify weekly count uses the target date's Monday-Sunday week, not today+7.
- Verify rescheduling does not incorrectly count the old reservation as an extra reservation after cancellation.

## Language

- Ask in English.
- Ask in Spanish.
- Ask in Ukrainian.
- Verify the GPT responds in the same language as the latest user message.