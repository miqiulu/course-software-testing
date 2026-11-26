# Team 17 - 12306 fault-revealing tests

Team leader: Weiming Li. Team members: Mingxiang Lu, Hou Xie.

The reports use the course requirements and baseline tests at commit `024c2bc`.
Observations and screenshots come from Chrome on local copies of the target
application. On Windows, run `.\start.bat` from the 12306 application directory and
open the address printed by the launcher. Runtime data survives restarts, so each
report is reproduced from the stated setup on a fresh application copy. Each report
can be reproduced independently.

| Case | Method | Requirement |
| --- | --- | --- |
| [01. Uncompleted orders show city names in the station columns](01-order-stations.md) | White-box | REQ-5.3.2, REQ-3.6.2, REQ-3.6.3 |
| [02. Train search accepts July 32 as a departure date](02-invalid-calendar-day.md) | Black-box | REQ-3.1.3 |
| [03. Upcoming trips rejects the full name of a booked passenger](03-passenger-name-search.md) | Black-box | REQ-5.4.3 |
| [04. History search matches text spanning the train number and passenger name](04-history-cross-field.md) | White-box | REQ-5.7.3 |
| [05. Adding a passenger with an existing name replaces the saved record](05-passenger-record-overwrite.md) | White-box | REQ-7.1, REQ-7.2 |
| [06. Saving Essential information discards the submitted password](06-essential-password.md) | White-box | REQ-6.2 |

## Passenger setup

Unless a case names another account, sign in with the course account
`passenger_manager_user` and password `Password123!`. Open **My 12306 →
Information management → My Passengers → Add new passengers**. Use China, passport
expiry 2028-12-31, birth date 1999-02-20, Male, Adult and email `test@example.com`.
Fill the name, passport, mobile and any overrides specified in the report, then
click **Determine**. Use a fresh application copy if an earlier run already used the
passport or reserved the seat. Order numbers for newly created bookings vary by run.

The cases that depend on booking (01, 03) also need the G1001 business-class seat of
the account to be unused, because each booking account holds one business seat per
journey.
