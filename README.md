# LinenLoop Laundry Management System

Next.js and Cloudflare D1 application for a laundry operation. It includes a dashboard, customer directory, service catalog, orders, status workflow, payments, balances and CSV order export. Monetary values are shown in Philippine pesos and stored as integer centavos.

Portfolio demonstration by RowLee Tanawan. The implementation uses Next.js-compatible App Router APIs with the Vinext runtime; deployment targets Cloudflare Workers. It is not a conventional standalone `next dev` deployment.

## Features

- Orders price quantity by the selected service's rate, calculate an expected completion time, and may take an initial payment.
- Allowed status progression: Received → Washing → Drying → Ready → Collected; active orders may be cancelled.
- Payments are limited to the outstanding balance and recorded in the activity log.
- Search orders by reference, customer or phone; export matching orders to CSV.
- Services can be activated or deactivated without removing historical order data.

## Technology

React, TypeScript, Next.js-compatible App Router, Vinext, Vite and responsive CSS. Cloudflare D1 SQLite and Drizzle migrations provide persistent data.

## Run locally

Node.js 22.13+ is required. Follow [installation, database initialization and walkthrough instructions](docs/SETUP.md), including the project-specific migration command. Dependencies and local database files are excluded from source control.

## Screenshots

Actual application screenshots are pending capture. No mockup is presented as a running application screenshot.

## Project layout

- `app/page.tsx`: application interface
- `app/globals.css`: responsive styling
- `app/api/`: server workflows, where applicable
- `db/` and `drizzle/`: schema and migrations, where applicable
- `docs/SETUP.md`: full setup, workflow rules and limitations

## Demo scope

Use fictional data for portfolio demonstrations. See [documented limitations](docs/SETUP.md) before deployment; authentication, payment integrations and operational safeguards vary by project and are not implied by the portfolio presentation.
