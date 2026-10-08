# LinenLoop Laundry Management System

Next.js and Cloudflare D1 application for a laundry operation. It includes a dashboard, customer directory, service catalog, orders, status workflow, payments, balances and CSV order export. Monetary values are shown in Philippine pesos and stored as integer centavos.

## Local setup

1. Install Node.js 22.13 or newer.
2. Extract this archive and open the `linenloop-laundry` directory.
3. Run `npm ci`.
4. Run `npm run dev` and open the printed local URL. The starter's Workers runtime uses a local Cloudflare D1 database.
5. Go to **Services** and click **Load sample services**. This inserts six example offerings once. Add a customer, then create an order.

The D1 binding name is `DB` in `.openai/hosting.json`. The initial migration is already in `drizzle/0000_glamorous_thaddeus_ross.sql`. If changing `db/schema.ts`, run `npm run db:generate` and apply the new migration through your deployment environment. For independent Cloudflare deployment, configure an equivalent D1 binding and migration process and adapt the Sites-specific build scripts.

## Workflow

- Orders price quantity by the selected service's rate, calculate an expected completion time, and may take an initial payment.
- Allowed status progression: Received → Washing → Drying → Ready → Collected; active orders may be cancelled.
- Payments are limited to the outstanding balance and recorded in the activity log.
- Search orders by reference, customer or phone; export matching orders to CSV.
- Services can be activated or deactivated without removing historical order data.

## Checks

`npx tsc --noEmit` validates types. `npm run build` creates the Workers-compatible app.

## Before public or production use

This is a working operational demo. Add staff authentication, role permissions, audit logging and rate limiting before public exposure. Cancellation does not issue a refund automatically. Payment entries are records of external payments; this project does not charge cards or connect to a payment gateway. Add payment provider integration, receipts, printer support, inventory, detailed multi-item tickets and customer notifications if required for your business.
