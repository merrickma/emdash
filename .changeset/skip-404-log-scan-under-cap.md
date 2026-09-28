---
"emdash": patch
---

Fixes scheduled cleanup so it stops reading the whole 404 log on every tick when there is nothing to evict. The cap on the 404 log is enforced by the maintenance sweep rather than on the request path, so a deployment with a one-minute cron scanned the table every minute regardless of traffic. A log of a few thousand rows produced millions of D1 rows read per day on a site serving no requests.
