# Weekwise

An independent, mobile-first prototype for an iPhone weekly budget and subscription tracker. The source is yours to edit. It has no ChatGPT runtime or paid API dependency.

## What works in this first build

- Custom weekly budget, Monday or Sunday start, automatic new weekly period without erasing older expenses.
- Add, edit, and delete expenses; attach a camera photo of a receipt; suggest a category from the merchant name; inspect past weeks and search within a week.
- Add, edit, pause, and delete weekly, monthly, or yearly subscriptions. Estimated monthly total is shown separately from weekly expenses.
- Export a CSV of expenses, or export and restore a JSON backup containing receipt photos.
- Light iPhone interface; installable as a web app when hosted over HTTPS; basic offline app shell after first load.

## Important limits

The camera photo is attached to the expense, but this version does **not** read merchant and total from the photo. It asks you to confirm and enter them. Merchant-based category suggestions work without an internet connection. Receipt OCR is a next development step.

Data is stored in the browser on that device using localStorage. Clearing website data, switching browser/origin, or removing a web app can erase it. Export a backup regularly. Photos are resized to reduce storage use. Subscriptions are reminders and estimates; the app does not connect to bank accounts or automatically create charges in the weekly ledger.

## Run and edit

For desktop testing, run `python3 -m http.server 8000` in this directory and visit `http://localhost:8000`.

For iPhone testing, place these files on an HTTPS static host you control, open its URL in Safari, and choose Share → Add to Home Screen. A locally opened `index.html` can show the design but may have different storage and installation behavior. No ChatGPT subscription is required to run the hosted app. Keep the ZIP/source and periodic JSON backups.

The app lives in `index.html`; colors, layout, and behavior are deliberately easy to change in the same file. `manifest.webmanifest`, `icon.svg`, and `sw.js` provide the home-screen icon and offline shell. Version 1 targets design and core tracking. A native SwiftUI build can later replace the web interface and use Apple's on-device Vision framework for receipt text recognition.
