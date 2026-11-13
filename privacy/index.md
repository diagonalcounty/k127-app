---
title: Privacy Policy
---

<!-- Internal: this policy was published 13 Nov 2026 at Jacob's request before a formal legal review. Do not put that note in the visible page. -->

# Privacy Policy

**Effective date:** 13 November 2026

This policy describes how the K127 iPad app handles information. It is written from what the app at `diagonalcounty/k127` (`origin/main`, commit `917d9a8a`) actually does. It does not cover GitHub, GitLab, Gitea, Forgejo, or Apple, which have their own policies.

The copyright line is “2026 Jacob Roecker.” This page does not list a company name, mailing address, or email address.

## We do not collect your data

K127 has no developer backend and does not require an account with us. The app does not include analytics, advertising, crash-reporting, or tracking SDKs that send information to us.

The shipping privacy manifest (`PrivacyInfo.xcprivacy`) sets tracking to false, lists no tracking domains, and lists no collected data types. On the App Store privacy label, this is declared as **Data Not Collected**.

Information that leaves this device goes to services **you** choose (a git host you control, or Apple’s MapKit when you open a map view), not to a K127 or developer server. Those cases are described below.

## Notes stay on this device

A vault is the folder of notes on this device. Notes are ordinary files. K127 reads and writes that folder, and you can open the same files in another editor.

Preferences, session state, and (on this device) reading position are stored locally, including in UserDefaults. They are not sent to us.

## Optional sync to a git host you control

GitHub is optional. You can write with everything only on this device. When you want a remote copy, you can connect GitHub, or add a GitLab or Gitea / Forgejo host from Settings, then use Push and Pull when you need them.

If you connect a host, the app sends your notes and git metadata to **your** repository on that host, over HTTPS, using the token you provided. We do not receive a copy.

Connect GitHub asks for a classic personal access token with the `repo` scope. Checking `gist` is optional. If you enable it, K127 can sync your reading position across your devices through a gist on **your** GitHub account, not through the notes repository. There is no OAuth app.

The token is stored in the Keychain on this device, not in the vault. You can also export settings to move a connection to another device. The default export does not include the token. If you choose to include it, that file is yours to keep private; K127 does not send it to us.

## Sync diagnostics on iPad

Settings → Sync includes “Write sync diagnostics.”

On iPad, this toggle defaults **on** if you have never changed it (this is the behavior after #1450). You can turn it off. An explicit choice always wins.

When it is on, the app writes diagnostics into `_k127-diagnostics/` in the vault, one file per device. The in-app explanation says these logs contain no tokens or note contents. Token-shaped strings in log lines are redacted.

Those files stay on this device unless you connect a git host and sync the vault. On iPad, the folder may be committed and pushed with your notes, to **your** repository. The logs are not sent to us.

The same folder can also include:

- Energy and lifecycle lines (for example battery level, thermal state, memory footprint, and when the app moved to the background).
- A short device identifier in the log file name (a sanitized device name plus a four-character fragment of the vendor identifier).
- JSON files from Apple’s MetricKit (performance metrics, and crash or hang diagnostics when MetricKit delivers them). These are written only while the toggle is on, into the same folder, and are not uploaded to us.

On a Mac Catalyst build, which is not part of the planned 0.1.0 App Store listing, the Release default is off, and logs are written outside the vault (`Library/Logs/k127` in the app container) and are not staged or uploaded.

## Maps

If you open a map view in a Bases file, K127 uses Apple MapKit to show pins from coordinates **already stored in those notes**. The app does not request your location, does not show your location, and does not prompt for location permission. Map images load from Apple Maps. The developer does not collect location.

## Children

K127 is not directed at children and is not a Kids Category app. We do not collect personal information from anyone, including children.

## Contact

To contact us about this policy or the app, open a GitHub issue. Instructions are on the [support page](../support/). This page does not publish an email address.

## Changes

If this policy changes, we will update this page and the effective date.
