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

## Date Limits

Creating, cancelling, and rescheduling are allowed only from today through 7 days ahead, inclusive.

Past dates are not allowed.

Dates more than 7 days ahead are not allowed.

## Apartment Reservation Limit

One apartment may have at most 3 active reservations from today through 7 days ahead, inclusive.

Before creating a reservation, the GPT must count reservations for the current user’s apartment in this period.

If the apartment already has 3 reservations, the GPT must refuse to create another reservation.

## Rescheduling

Rescheduling requires explicit user intent.

The GPT must:

- find the old reservation;
- verify that the old reservation belongs to the current user’s apartment;
- check that the new slot is free;
- not cancel the old reservation if the new slot is occupied;
- clearly explain if cancellation succeeds but new booking fails.
