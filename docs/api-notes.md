# API Notes

This document describes the external IZAR4 API used by the GPT Action.

## Base URL

```text
https://izar4.es
```

## Authentication

```text
None
```

The current API configuration does not use authentication.

## Operations

### `getReservations`

```http
GET /wp-json/wp/v2/reservas
```

Used to get the current list of padel court reservations.

Recommended query parameters:

| Parameter | Description |
|---|---|
| `per_page` | Number of reservations to return. Recommended: `100`. |
| `recurso` | Court/resource id if known. Current example: `12`. |
| `_fields` | Limits returned fields. Recommended: `id,slug,acf,recurso`. |

Recommended request:

```http
GET /wp-json/wp/v2/reservas?per_page=100&recurso=12&_fields=id,slug,acf,recurso
```

### `createReservation`

```http
POST /wp-json/app/v1/reservar
```

Creates a new reservation.

Request body example:

```json
{
  "titulo": "20260604 - PADEL P1-1",
  "idFranja": "P1-1",
  "fecha": "20260604",
  "nombre": "John Smith",
  "vivienda": "P2-02",
  "codigo": "GPT_20260604_143015",
  "idTermino": 12
}
```

### `cancelReservation`

```http
POST /wp-json/app/v1/cancelar
```

Cancels an existing reservation.

Request body example:

```json
{
  "idReserva": 1369,
  "codigo": "GPT_20260604_143015"
}
```

## Important Response Fields

The GPT reads reservation data from these fields:

| Field | Meaning |
|---|---|
| `id` | Reservation id. |
| `slug` | Reservation slug. |
| `recurso` | Resource/term id used as `idTermino`. |
| `acf.id_franja_reservas` | Slot id, for example `P1-1`. |
| `acf.fecha_reservas` | Reservation date in `YYYYMMDD` format. |
| `acf.nombre_reservas` | Reservation holder name. |
| `acf.vivienda_reservas` | Apartment code. |
| `acf.codigo_cancelacion_reservas` | Cancellation code. |

## Cancellation Code Strategy

For new reservations, the GPT generates `codigo` as:

```text
GPT_YYYYMMDD_HHMMSS
```

Example:
```text
GPT_20260623_143015
```
The timestamp must come from getCurrentMadridTime.

For cancellation, the GPT must not guess or hardcode the code. It must use:
```text
acf.codigo_cancelacion_reservas
```
from the matching reservation returned by fresh getReservations.

Old reservations may still have legacy code values such as 1; in that case, the GPT uses whatever value is returned by the API.

## Notes

- `idTermino` must be obtained from the API response field `recurso`.
- `idTermino` should not be hardcoded in GPT instructions.
- The GPT should not expose raw JSON or internal API details to users unless explicitly asked.
- The external IZAR4 API may change without notice.

## Madrid Time API

The GPT uses a separate time API to get the current date and time in Europe/Madrid.

Base URL:

```text
https://timeapi.io
```

### `getCurrentMadridTime`

```http
GET /api/Time/current/zone?timeZone=Europe/Madrid
```

Used to determine:

- current Europe/Madrid date;
- current Europe/Madrid time;
- `today`;
- `today + 7 days`;
- relative dates such as `today`, `tomorrow`, and weekdays.

Example response:

```json
{
  "year": 2026,
  "month": 6,
  "day": 23,
  "hour": 10,
  "minute": 30,
  "seconds": 15,
  "milliSeconds": 123,
  "dateTime": "2026-06-23T10:30:15.123",
  "date": "06/23/2026",
  "time": "10:30",
  "timeZone": "Europe/Madrid",
  "dayOfWeek": "Tuesday",
  "dstActive": true
}
```
## Required Call Order

For every user request, the GPT should call APIs in this order:

```text
1. getCurrentMadridTime
2. getReservations
3. answer the user or perform the requested action
```

For create, cancel, or reschedule operations, the GPT must use only the fresh `getCurrentMadridTime` and `getReservations` responses from the current user request.

After any create, cancel, or reschedule action, the GPT must call `getReservations` again and show the updated schedule.
