# JPN2026 trip data (private)

Plaintext booking data for the JPN2026 app. **Never deploy or publish this repo.** Only the encrypted `enc/` folder the app builds from it is published.

## Use

Clone this repo into the app repo as `data/` (the app repo ignores that folder), then from the app repo:

```
node encrypt.mjs data '<trip passphrase>'
vercel deploy --prod
```

`salt` is created on the first run; commit it so phones keep working after re-publishing.

## Files to add before the first encrypt

These were attachments in the booking emails and could not be copied automatically. Save each from Gmail (jonbloomy@gmail.com) under `attachments/` with exactly this name; `encrypt.mjs` stops if any is missing.

| File | From email |
|---|---|
| `jreast-pickup-qr.png` | JR-EAST "[Reservation accepted] ... 10/24" (the QR image in the email) |
| `usj-voucher.pdf` | "Fwd: You're on your way! Booking NUT433342 confirmed." |
| `krisflyer-osaka.pdf` | "Fw: Booking confirmation - Booking ID: 2026044284" |
| `krisflyer-kyoto.pdf` | "Booking confirmation - Booking ID: 2018102254" (Confirmation_for_Booking_ID...) |
| `krisflyer-kyoto-checkin.pdf` | same email (special_checkin_...) |
| `thunderbird-voucher.pdf` | Klook "Booking SNY755390 confirmed." |
| `shirakawago-voucher.pdf` | Klook "Booking UCP155477 confirmed." |
| `teamlab-voucher.pdf` | Klook "Booking ZRZ723350 confirmed." |

## Still open

- Kanazawa → Osaka on Wed 28 Oct: covered by the open Klook Thunderbird voucher SNY755390 (exchange at the station, pick the train there). Once you know the train, the gap item can become a proper train.
- Nozomi 254: seats arrive by email after 08:00 JST on 7 Oct. Update `car` and `seats`, and set `method` (`smartex-qr` assumed).
- Placeholder end times: USJ 20:00, Shirakawa-go tour 17:00, teamLab 20:00. Set them once known; they only affect the Plan tab's scheduling.
- Dated reminders live in `reminders` in trip.json.
