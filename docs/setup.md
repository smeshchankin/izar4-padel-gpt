# Setup Guide

This guide explains how to configure the IZAR4 Padel Booking GPT in GPT Builder.

## 1. Create a Custom GPT

Open GPT Builder and create a new GPT.

## 2. Basic Settings

Use the following values:

```text
Name: IZAR4 Padel Booking
Description: IZAR4 padel court booking assistant
```

## 3. Icon

Upload the icon from:

```text
assets/icon.png
```

## 4. Instructions

Copy the content from:

```text
gpt/instructions.md
```

and paste it into the GPT Instructions field.

## 5. Conversation Starters

Copy the recommended starters from:

```text
gpt/conversation-starters.md
```

Current starters:

```text
What court slots are free today?
Book padel tomorrow at 09:00
Cancel my court booking
Set up my name and apartment for bookings
```

## 6. Capabilities

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

## 7. Actions

Create one Action:

```text
IZAR4 Reservas API
```

Authentication:

```text
None
```

Schema file:

```text
actions/izar4.openapi.yaml
```

The schema defines these operations:

```text
getReservations
createReservation
cancelReservation
```

## 8. Privacy Policy

Use the privacy policy from the repository:

```text
PRIVACY.md
```

Public GitHub URL:

```text
https://github.com/smeshchankin/izar4-padel-gpt/blob/main/PRIVACY.md
```

Alternative raw URL:

```text
https://raw.githubusercontent.com/smeshchankin/izar4-padel-gpt/main/PRIVACY.md
```

The current privacy policy URL is documented in:

```text
docs/privacy-policy-url.md
```

## 9. Testing

Before publishing or sharing the GPT, run the manual checklist:

```text
tests/manual-test-checklist.md
```

## 10. Notes

This GPT is not an official IZAR4 service.

It is not affiliated with, endorsed by, operated by, or maintained by IZAR4.

Use at your own risk.
