# Weekwise

An independent, mobile-first prototype for an iPhone weekly budget and subscription tracker. The source is yours to edit. It has no ChatGPT runtime or paid API dependency.

## What works in this first build

- Custom weekly budget, Monday or Sunday start, automatic new weekly period without erasing older expenses.
- Add, edit, and delete expenses; attach a camera photo of a receipt; suggest a category from the merchant name; inspect past weeks and search within a week.
- Enter an amount and short description first; the app suggests a category, subcategory, icon and color from the description. You can change the category.
- Financial calendar with recurring income, bills, planned expenses and subscription due dates. Review weekly budget results and move between months.
- Calendar cash-flow colors: green for expected income, red for payments and recorded expenses, blue for weekly budget availability. Each calendar week includes its own budget bar; tapping a day reveals its entries.
- In-app Notifications area for expected payday and one-time income on the scheduled date. It does not send system push alerts or confirm deposits.
- The Home budget card animates into the detailed view and back, with a reduced-motion fallback.
- Reports with monthly spending, category and subcategory transactions, weekly results and simple observations.
- Add, edit, pause, and delete weekly, monthly, or yearly subscriptions. Estimated monthly total is shown separately from weekly expenses.
- Export a CSV of expenses, or export and restore a JSON backup containing receipt photos.
- Light iPhone interface; installable as a web app when hosted over HTTPS; basic offline app shell after first load.

## Important limits

The camera photo is attached to the expense, but this version does **not** read merchant and total from the photo. It asks you to confirm and enter them. Merchant-based category suggestions work without an internet connection. Receipt OCR is a next development step.

Data is stored in the browser on that device using localStorage. Clearing website data, switching browser/origin, or removing a web app can erase it. Export a backup regularly. Photos are resized to reduce storage use. The calendar is a forecast based on dates you enter; the app does not connect to bank accounts, verify paychecks or automatically create weekly expenses from subscriptions and bills. Reports count actual expenses you record. Older weekly budget limits from before this release cannot be reconstructed; future weekly limits are recorded when you open the app in a new week.

## Run and edit

For desktop testing, run `python3 -m http.server 8000` in this directory and visit `http://localhost:8000`.

For iPhone testing, place these files on an HTTPS static host you control, open its URL in Safari, and choose Share → Add to Home Screen. A locally opened `index.html` can show the design but may have different storage and installation behavior. No ChatGPT subscription is required to run the hosted app. Keep the ZIP/source and periodic JSON backups.

The app lives in `index.html`; colors, layout, and behavior are deliberately easy to change in the same file. `manifest.webmanifest`, `icon.svg`, and `sw.js` provide the home-screen icon and offline shell. Version 1 targets design and core tracking. A native SwiftUI build can later replace the web interface and use Apple's on-device Vision framework for receipt text recognition.
