# Known Limitations

This document lists known limitations of the current GPT configuration.

## External API

- This project does not control the IZAR4 website or API.
- The IZAR4 API may change without notice.
- The IZAR4 API may be unavailable or return incomplete data.
- The GPT creator does not control how IZAR4 stores or exposes reservation data.

## Authentication

- The current IZAR4 API Action uses no authentication.
- Reservation and cancellation behavior depends entirely on the external IZAR4 API.

## Cancellation Code

- The current configuration uses `codigo="1"` for create and cancel operations.
- Future versions may use a generated GPT marker as the cancellation code.

## Time Handling

- The current configuration uses an external Madrid Time API to determine the current Europe/Madrid date and time.
- The GPT should use `getCurrentMadridTime` before create, cancel, or reschedule operations.
- If the Madrid Time API is unavailable, the GPT should not create, cancel, or reschedule reservations.

## Fresh Data

- The current instructions require `getReservations` before schedule, booking, cancellation, and rescheduling operations.
- Future versions may strengthen this by requiring a fresh API call at the start of every user message.

## Schedule Display

- The current configuration supports day schedule tables.
- Weekly schedule table output is planned for a future version.

## Safety

The GPT instructions are designed to reduce mistakes, but no guarantee is made that:

- the GPT will always interpret the user correctly;
- the external API will behave consistently;
- every invalid action will always be prevented;
- all displayed reservation data will always be accurate or up to date.

Users should verify important reservation details directly on the official IZAR4 reservation page when necessary.
