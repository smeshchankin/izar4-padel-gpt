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
  "codigo": "1",
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
  "codigo": "1"
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

## Notes

- `idTermino` must be obtained from the API response field `recurso`.
- `idTermino` should not be hardcoded in GPT instructions.
- The GPT should not expose raw JSON or internal API details to users unless explicitly asked.
- The external IZAR4 API may change without notice.
