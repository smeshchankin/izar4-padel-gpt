# GPT Builder Settings

## Name

```text
IZAR4 Padel Booking
```

## Description

```text
IZAR4 padel court booking assistant
```

## Capabilities

Current configuration:

```text
Web Search: enabled
Canvas: enabled
Image Generation: enabled
Code Interpreter & Data Analysis: enabled
Actions: enabled
```

Recommended production configuration:

```text
Web Search: disabled
Canvas: disabled
Image Generation: disabled
Code Interpreter & Data Analysis: disabled
Actions: enabled
```

## Actions

Authentication:

```text
None
```

Configured Actions:

```text
IZAR4 Reservas API
Madrid Time API
```

### IZAR4 Reservas API

Schema file:

```text
actions/izar4.openapi.yaml
```

Operations:

```text
getReservations
createReservation
cancelReservation
```

### Madrid Time API

Schema file:

```text
actions/madrid-time.openapi.yaml
```

Operations:

```text
getCurrentMadridTime
```

## Privacy Policy

Repository file:

```text
PRIVACY.md
```

GitHub URL:

```text
https://github.com/smeshchankin/izar4-padel-gpt/blob/main/PRIVACY.md
```

Alternative raw URL, if GPT Builder does not accept the GitHub page URL:

```text
https://raw.githubusercontent.com/smeshchankin/izar4-padel-gpt/main/PRIVACY.md
```

## Repository

```text
https://github.com/smeshchankin/izar4-padel-gpt
```

## Notes

This GPT is not an official IZAR4 service.

It is not affiliated with, endorsed by, operated by, or maintained by IZAR4.

Use at your own risk.
