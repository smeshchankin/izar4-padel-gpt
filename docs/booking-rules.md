# Booking Rules

This document summarizes the booking, cancellation, and rescheduling rules implemented in the GPT instructions.

## Apartment Format

Apartment format:

```text
Px-yy
```

Where:

- `x` is `1`, `2`, or `3`;
- `yy` is from `01` to `40`.

Valid examples:

```text
P1-01
P2-22
P3-33
```

Invalid examples:

```text
P4-10
P2-41
2-22
```

If the user provides an apartment without a leading zero, normalize it:

```text
P2-5 -> P2-05
```

## Slots

| Slot | Time |
|---|---|
| `P1-1` | 09:00-10:00 |
| `P1-2` | 10:00-11:30 |
| `P1-3` | 11:30-13:00 |
| `P1-4` | 13:00-14:30 |
| `P1-5` | 14:30-16:00 |
| `P1-6` | 16:00-17:30 |
| `P1-7` | 17:30-19:00 |
| `P1-8` | 19:00-20:30 |
| `P1-9` | 20:30-22:00 |

## Occupied Slot Rule

A slot is occupied when a reservation has:

```text
acf.fecha_reservas = target date YYYYMMDD
acf.id_franja_reservas = target slot id
```

If a slot is occupied, the GPT must not create another reservation for the same date and slot.

## Weekly Schedule Display

For weekly or 7-day schedule requests, the GPT should show a markdown table where:

- columns are dates;
- rows are slot start times;
- each cell shows `🟢` if free or `🔴 Name` if occupied.

Slot rows:

```text
09:00
10:00
11:30
13:00
14:30
16:00
17:30
19:00
20:30
```

## Fresh Data Rule

Before answering any user request, the GPT must:

1. call `getCurrentMadridTime`;
2. call `getReservations`;
3. use only the fresh responses from the current request.

The GPT must not rely on reservation data, current date, or current time from previous messages, memory, or earlier API calls.

This rule applies to schedules, free-slot checks, booking, cancellation, rescheduling, and follow-up questions.

## Booking Safety

The GPT must:

- call `getReservations` before creating a reservation;
- check if the target date and slot are free;
- refuse to create duplicate reservations for the same date and slot;
- not overwrite, replace, or fix existing reservations by creating another one;
- suggest free slots when the requested slot is occupied.

## Cancellation Safety

The GPT must:

- cancel only when the user explicitly asks to cancel, delete, or remove a reservation;
- call `getReservations` before cancellation;
- find the matching reservation;
- cancel only if the reservation apartment matches the current user’s apartment;
- refuse cancellation if the reservation belongs to another apartment;
- ask for clarification if multiple matching reservations are found.

## Cancellation Code

For new reservations, the GPT must generate the cancellation code as:
```text
GPT_YYYYMMDD_HHMMSS
```
using the current Europe/Madrid time from getCurrentMadridTime.

For cancellation, the GPT must use the cancellation code stored in the matching reservation:
```text
acf.codigo_cancelacion_reservas
```

The GPT must not hardcode the cancellation code.

Legacy reservations may still use old cancellation codes such as 1. The GPT must use the actual code returned by the API for that reservation.

## Date Limits

Creating, cancelling, and rescheduling are allowed only from today through 7 days ahead, inclusive.

Past dates are not allowed.

Dates more than 7 days ahead are not allowed.

## Apartment Reservation Limits

The GPT must enforce the same limits as the main reservation system:

- maximum 3 active reservations per apartment per calendar week for this resource;
- maximum 1 active reservation per apartment per day for this resource.

Calendar week means Monday-Sunday in Europe/Madrid.

Before creating a reservation, the GPT must count fresh reservations for the current apartment and same resource:

- daily count: reservations where `acf.fecha_reservas` equals the target date;
- weekly count: reservations where `acf.fecha_reservas` is within the Monday-Sunday week of the target date.

If the apartment already has 1 reservation on the target date, the GPT must not create another reservation for that date.

If the apartment already has 3 reservations in the target week, the GPT must not create another reservation for that week.

## Rescheduling

Rescheduling requires explicit user intent.

The GPT must:

- find the old reservation;
- verify that the old reservation belongs to the current user’s apartment;
- check that the new slot is free;
- not cancel the old reservation if the new slot is occupied;
- clearly explain if cancellation succeeds but new booking fails.
