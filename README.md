# TuxedoDrive Status

This repository contains the status page for TuxedoDrive, powered by [Upptime](https://upptime.js.org).

**Live status page:** [status.tuxedodrive.dev](https://status.tuxedodrive.dev)

## Monitored Services

We monitor 18 critical services across our platform:

- **Internal Services** - Production, staging, dashboards
- **Payment Processing** - Stripe
- **Email Services** - Postmark, SendGrid
- **SMS & Messaging** - Twilio
- **Authentication** - Google OAuth
- **Infrastructure** - Render, GitHub
- **Cloud Services** - Doppler

## How It Works

Upptime runs automated checks every 5 minutes via GitHub Actions. When a service goes down:
1. A GitHub issue is created
2. The team is notified via email
3. The status page updates automatically

## License

- Code: [MIT](./LICENSE)
- Data in `./history`: [Open Database License](https://opendatacommons.org/licenses/odbl/1-0/)
