# AGENTS.md

This file provides context for AI assistants working on the TuxedoDrive status page.

## What This Repo Does

This is an [Upptime](https://upptime.js.org) status page that monitors 18 external services TuxedoDrive depends on. GitHub Actions run checks every 5 minutes and auto-commit results.

## Key Files

- `.upptimerc.yml` - Service definitions and configuration (the main file you'll edit)
- `history/*.yml` - Per-service status history (auto-generated, but must be cleaned up manually when removing services)
- `api/` - JSON data for the status page API
- `graphs/` - Response time graphs (PNG files)

## Maintenance Rules

### When Removing a Service

Delete ALL artifacts in the same commit:
1. Remove the service from `.upptimerc.yml`
2. Delete `history/<service-slug>.yml`
3. Delete `api/<service-slug>/` directory
4. Delete `graphs/<service-slug>/` directory

Failure to do this causes spurious "down" alerts from stale history files.

### When Adding External APIs

1. Test the URL manually first: `curl -s -o /dev/null -w "%{http_code}" <url>`
2. Use broad `expectedStatusCodes` - external APIs change behavior without notice
3. For unauthenticated health checks, accept any non-5xx response: `[200, 302, 400, 401, 403]`
4. Document the URL source in a comment if it's not obvious

### When Modifying expectedStatusCodes

If you're updating expected codes because a check is failing:
1. Verify the service is actually up (not a real outage)
2. Test the actual response: `curl -s -o /dev/null -w "%{http_code}" <url>`
3. Update both `.upptimerc.yml` AND reset `history/<service>.yml` status to `up`
4. Close any spurious GitHub issues with an explanation

## Slug Naming

Upptime converts service names to slugs for file/directory names. The conversion lowercases and replaces spaces/special chars with hyphens. Examples:
- "Cloud APIs" -> `cloud-ap-is` (note: "APIs" becomes "ap-is")
- "Code Repository" -> `code-repository`
- "SMS Notifications" -> `sms-notifications`

## Common Issues

### "Service is down" but it's actually up
Usually means `expectedStatusCodes` doesn't include the actual response code. Check with curl, update config, reset history.

### Stale incidents after removing a service
History file wasn't deleted. Remove `history/`, `api/`, and `graphs/` directories for that service.

### Merge conflicts in history files
Upptime bot commits frequently. When rebasing, keep your URL/status fixes but take the bot's timestamps.
