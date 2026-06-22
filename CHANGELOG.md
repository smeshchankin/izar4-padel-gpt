# Changelog


## 0.3.0 - 2026-06-23 - Require fresh data for every request

- Added mandatory `getCurrentMadridTime` call at the start of every user request.
- Added mandatory `getReservations` call after current time and before every answer.
- Prohibited using reservation data, date, or time from previous messages, memory, or earlier API calls.
- Updated documentation for fresh data behavior and required API call order.

## 0.2.0 - 2026-06-22 - Add Madrid time action

- Added `Madrid Time API` Action.
- Added `getCurrentMadridTime` operation using `timeapi.io`.
- Updated GPT instructions to use Europe/Madrid time from API before create, cancel, and reschedule operations.
- Updated setup and API documentation.
- Updated privacy notes for external time API usage.

## 0.1.0 - 2026-06-20 - Initial configuration

- Added GPT name and description.
- Added current GPT instructions.
- Added IZAR4 OpenAPI Actions schema.
- Added conversation starters.
- Added privacy policy, disclaimer, and security notes.
- Added manual test checklist.
