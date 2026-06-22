# Privacy Policy and Disclaimer

**Project:** IZAR4 Padel Booking GPT  
**Last updated:** June 18, 2026  
**Contact:** sergey84@gmail.com

## 1. Overview

IZAR4 Padel Booking GPT is an independent assistant created to help users interact with the publicly accessible IZAR4 padel court reservation system.

This GPT is not an official IZAR4 service. It is not affiliated with, endorsed by, operated by, maintained by, or controlled by IZAR4, any property management entity, or any community administration.

This GPT is provided only as a convenience tool for checking availability, creating reservations, cancelling reservations, and rescheduling reservations when possible.

Use of this GPT is entirely at the user’s own risk.

## 2. Data Processed

When you use this GPT, it may process the following information:

- your name for the reservation;
- your apartment number, for example `P1-01`, `P2-22`, or `P3-33`;
- requested reservation date and time;
- existing court reservation data returned by the IZAR4 reservation API;
- reservation creation, cancellation, or rescheduling requests made by you;
- cancellation-related data returned by the IZAR4 reservation API when required to perform a cancellation.

## 3. How the Data Is Used

The data is used only to:

- show court availability;
- display the current court schedule;
- create a reservation;
- cancel a reservation;
- reschedule a reservation when possible;
- validate basic booking rules, such as apartment format, occupied slots, date limits, and reservation limits.

## 4. External API

This GPT uses the publicly accessible IZAR4 reservation API at `izar4.es`.

Reservation data, including names, apartment numbers, dates, times, and cancellation-related information, may be sent to or received from `izar4.es` when the user requests an action.

The creator of this GPT does not control:

- the IZAR4 website;
- the IZAR4 API;
- the availability of the IZAR4 API;
- the security of the IZAR4 API;
- the data stored by IZAR4;
- the correctness, completeness, or freshness of IZAR4 API responses;
- any changes made to the IZAR4 website or API.

Any data sent to or received from `izar4.es` is handled according to the behavior and policies of the IZAR4 website and its API, which are outside the control of this project and its creator.

This GPT may also use an external time API, currently `timeapi.io`, to determine the current date and time in Europe/Madrid.

This time request is used to interpret relative dates, enforce booking date limits, and validate whether a requested action is allowed.

The time API request does not need to include the user’s name, apartment number, or reservation details.

## 5. No Separate Backend Database

This GPT does not operate a separate backend database controlled by the GPT creator.

The GPT creator does not intentionally collect, sell, rent, or share users’ personal data.

Data may still be processed by:

- ChatGPT/OpenAI as part of the conversation and GPT functionality;
- the IZAR4 website/API as part of the requested reservation action;
- any third-party service configured in the GPT Actions schema, if such a service is added in the future.
- an external time API used only to determine the current Europe/Madrid date and time.

## 6. User Responsibility

Users are solely responsible for how they use this GPT.

By using this GPT, users agree that they are responsible for:

- checking that reservation details are correct before relying on them;
- using the GPT only for legitimate reservation purposes;
- providing accurate name and apartment information;
- not cancelling, modifying, or interfering with reservations that do not belong to them;
- complying with any applicable community, property, IZAR4, or reservation rules;
- verifying important reservation details directly on the official IZAR4 reservation page when necessary.

The GPT creator is not responsible for misuse of the GPT by users.

## 7. Cancellation Functionality

The cancellation code may be used by the GPT only for performing cancellation requests through the IZAR4 API when requested by the user.

Users must not misuse cancellation functionality or cancel reservations that are not theirs.

The GPT instructions are designed to prevent cancellation of reservations belonging to another apartment, but no technical or operational guarantee is made that the GPT, the external API, or the user interaction will always behave perfectly.

Users remain responsible for all cancellation requests they make.

## 8. No Guarantee

This GPT is provided **“as is”** and **“as available”**.

No guarantee is made that:

- the schedule shown by the GPT is always accurate, complete, or up to date;
- a reservation request will always succeed;
- a cancellation request will always succeed;
- a rescheduling request will always succeed;
- the IZAR4 API will be available;
- the IZAR4 API will behave consistently;
- the GPT will always correctly interpret the user’s request;
- the GPT will always detect all conflicts, limits, or rule violations;
- the GPT will always prevent user mistakes or misuse;
- the GPT will remain compatible with future changes to the IZAR4 website or API.

Users should verify important reservation details directly on the official IZAR4 reservation page when necessary.

## 9. Limitation of Liability

To the maximum extent permitted by applicable law, the creator of this GPT is not responsible or liable for any direct, indirect, incidental, consequential, special, exemplary, punitive, or other damages, losses, claims, disputes, or issues arising from or related to:

- use of this GPT;
- inability to use this GPT;
- use of the IZAR4 website or API;
- unavailability or failure of the IZAR4 API;
- incorrect, outdated, incomplete, or missing reservation data;
- missed reservations;
- incorrect reservations;
- duplicate reservations;
- failed reservations;
- failed cancellations;
- unintended cancellations;
- failed rescheduling;
- scheduling conflicts;
- data exposure;
- user mistakes;
- misuse by users;
- changes to the IZAR4 website or API;
- decisions made based on information provided by this GPT.

Use of this GPT is entirely at the user’s own risk.

## 10. Open Source Repository

If this GPT configuration is published as an open source repository, the repository license applies only to the repository contents, such as documentation, instructions, configuration files, examples, and OpenAPI schemas.

The repository license does not create any affiliation with IZAR4 and does not provide any warranty regarding the IZAR4 website, the IZAR4 API, reservation availability, or correct GPT behavior.

## 11. Changes

This Privacy Policy and Disclaimer may be updated from time to time.

Continued use of this GPT after changes means that the user accepts the updated version.

## 12. Contact

For questions or removal requests, contact:

**sergey84@gmail.com**