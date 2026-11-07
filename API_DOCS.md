# Creator Availability API

Base URL: https://sexyswami.github.io/creator-availability-demo

## GET /availability.json
Returns the creator's open sponsorship dates.
No authentication. No query parameters.

### Response (200, application/json)
| Field | Type | Meaning |
|---|---|---|
| creator | string | Creator name |
| timezone | string | IANA time zone |
| updated | string | Date the calendar was last updated |
| open_dates | array | Dates free for a sponsored integration |
| open_dates[].date | string | ISO date (YYYY-MM-DD) |
| open_dates[].day | string | Weekday name |
| open_dates[].slots | integer | Open slots that day |
| booked_dates | array | ISO dates that are not available |
| integration_rate_60s_usd | integer | Price of one 60-second integration |
| note | string | Booking terms |

### Example
curl https://sexyswami.github.io/creator-availability-demo/availability.json

Use case: when a brand asks "are you free on <date>?", call this endpoint and
answer from open_dates. If the date is in booked_dates or absent, say it is
unavailable and offer the nearest open date.
