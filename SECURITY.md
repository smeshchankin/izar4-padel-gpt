# Security Policy

## Known limitations

- The IZAR4 reservation API is external and not controlled by this project.
- The GPT creator does not control IZAR4 API security, availability, or behavior.
- Reservation data may be visible through the external IZAR4 API.
- Cancellation depends on the cancellation code accepted by the IZAR4 API.

## Safety rules

The GPT instructions require that:

- reservations are fetched before booking, cancelling, or rescheduling;
- duplicate reservations for the same date and slot are not created;
- reservations belonging to another apartment are not cancelled;
- bookings and cancellations are allowed only for the current user’s apartment;
- the GPT does not expose cancellation codes or internal API details unless explicitly requested.

## Reporting issues

If you find a problem with this GPT configuration, open a GitHub issue or contact the repository owner.
