# TuxedoDrive Status

[![Conforms to README.lint](https://img.shields.io/badge/README.lint-conforming-brightgreen)](https://github.com/discoveryworks/readme-dot-lint)

**Live status page:** [status.tuxedodrive.dev](https://status.tuxedodrive.dev)

🌌 Why did we create this status page?
=============================

TuxedoDrive depends on 18 external services. When something goes wrong, we need to know immediately—and so do our users. This status page provides transparency and automated monitoring so we can respond to outages quickly.

🌌🌌 Who benefits from it?
=============================

- **TuxedoDrive users** who want to check if an issue is on our end
- **The TuxedoDrive team** who need immediate alerts when services fail

🌌🌌🌌 What does it do?
=============================

Monitors 18 critical services across our platform:

- **Internal Services** - Production, staging, dashboards
- **Payment Processing** - Stripe
- **Email Services** - Postmark, SendGrid
- **SMS & Messaging** - Twilio
- **Authentication** - Google OAuth
- **Infrastructure** - Render, GitHub
- **Cloud Services** - Doppler

🌌🌌🌌🌌 How does it work?
=============================

Powered by [Upptime](https://upptime.js.org), this runs automated checks every 5 minutes via GitHub Actions. When a service goes down:

1. A GitHub issue is created
2. The team is notified via email
3. The status page updates automatically

🌌🌌🌌🌌🌌 Extras
=============================

## License

- Code: [MIT](./LICENSE)
- Data in `./history`: [Open Database License](https://opendatacommons.org/licenses/odbl/1-0/)
