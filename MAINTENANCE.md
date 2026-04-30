# Maintenance Guide

This repo hosts the public-facing legal documents for Bet Tracker. These docs are referenced by the App Store, Google Play, and the app itself — keeping them accurate is a legal requirement, not a nice-to-have.

## When to Update

Update `privacy.html` and/or `terms.html` whenever ANY of the following happens:

### Entity & Identity
- [ ] LLC forms or entity name changes → update ownership clauses in terms.html, add entity name throughout
- [ ] Business address changes → update both files
- [ ] Privacy contact email changes → update both files

### Data & Privacy (privacy.html)
- [ ] New third-party processor added (analytics, crash reporting, ads, push notifications, etc.)
- [ ] New data category collected (location, contacts, photos, payment info, etc.)
- [ ] Account deletion flow changes (path, timing, what gets deleted)
- [ ] Data retention period changes
- [ ] International data transfer practices change

### App Functionality (both files)
- [ ] App adds payments or in-app purchases
- [ ] App adds messaging or DMs between users
- [ ] App adds public profiles or social discovery features
- [ ] App scope changes from "tracking only" to anything resembling facilitation
- [ ] Age requirements change

### Time-Based
- [ ] Annual review: every January, re-read both docs end-to-end

## Update Process

1. Edit the relevant file(s)
2. Bump the "Effective Date" at the top of any changed file
3. Commit with a clear message: `git commit -m "privacy: add Sentry as processor"`
4. Push to main (`git push`) — GitHub Pages auto-deploys within ~1 minute
5. Verify the live URL reflects the change
6. If the change is material (new data collection, new processors, changed user rights):
   - Notify users in-app on next launch
   - Consider an email notification for significant changes

## Pending Updates

Track known-but-not-yet-resolved items here:

- [ ] Replace "Bet Tracker" with legal entity name throughout terms.html once LLC is filed (sections: Ownership, Limitation of Liability, Governing Law)
- [ ] Confirm final privacy contact email before App Store submission
- [ ] Add analytics/crash reporting processor to privacy.html if/when added (PostHog, Sentry, etc.)

## File Map

- `index.html` — landing page linking to both docs
- `privacy.html` — privacy policy (referenced by `privacyPolicyUrl` in app.json)
- `terms.html` — terms of service
- `MAINTENANCE.md` — this file (not public-facing, just for maintainers)

## Hosting

- Hosted on GitHub Pages from the `main` branch, root folder
- Live URL: `https://<username>.github.io/bettracker-legal/`
- No build step — pure static HTML
- DNS: none (using default github.io domain for now)

## Original Source

The HTML files were generated from `privacy-policy.md` and `terms-of-service.md` (kept in this repo for reference). The HTML versions are authoritative — if substantive edits are needed, edit the HTML directly and optionally back-port to the markdown files.
