# Manual Test Checklist

## Schedule

- Ask: What court slots are free today?
- Verify GPT calls getReservations.
- Verify GPT shows all 9 slots.
- Verify free and occupied slots are displayed correctly.

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

- Try booking more than 7 days ahead.
- Verify GPT refuses.
- Try booking a 4th reservation for the same apartment.
- Verify GPT refuses.

## Language

- Ask in English.
- Ask in Spanish.
- Ask in Ukrainian.
- Verify the GPT responds in the same language as the latest user message.