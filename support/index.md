---
title: Support
---

# Support

K127 is a Markdown notes app for iPad. This page is a short getting-started guide, answers to common GitHub-connect questions, and how to get help.

K127 0.1.0 is a free early release. You should not expect everything to be finished. This early release does not include AI on iPad.

## Getting started

You can read the same help in the app: **Help → Getting Started**. It works with no account and no network.

A vault is the folder of notes on this device. Notes are ordinary files. K127 reads and writes that folder, and you can open the same files in another editor.

**Three panes**

- Left — where files live (and Sync, once you connect GitHub)
- Center — the note you are reading
- Right — AI you choose, when you want it. This 0.1.0 early release does not include AI on iPad.

**Preview and Source.** Notes open in Preview. That is the usual view. Source shows the Markdown. Switch with Preview and Source in the header, or from the View menu.

**Wikilinks.** A wikilink points at another note. Write the note title in double brackets, like `[[Welcome]]`. Preview opens that note. Source shows the brackets.

**GitHub** is optional. You can write for days with everything only on this device. When you want a remote copy, choose Connect GitHub, then Push and Pull when you need them. Connect GitHub asks for a personal access token and stores it on this device, not in the vault. You can also add GitLab and Gitea / Forgejo hosts from Settings.

**Help** is in the Help menu: Getting Started and Keyboard Shortcuts.

If you chose **Stay Local for Now** on first launch, the app started a vault on this device and opened a short Welcome note. You can connect GitHub later from Settings → Sync.

## FAQ

### How do I stay local?

On first launch, the app asks “Where should notes live?” Choose **Stay Local for Now**.

Stay Local starts a vault on this device and opens a short Welcome note. You can write, use Preview and Source, follow wikilinks, and read Help without a GitHub account and without a network connection. GitHub is optional; you can connect later from Settings → Sync.

You can also choose **Open Folder…** if you already have a folder of notes on this device.

### How do I connect GitHub and create a token?

K127 has no OAuth app. You paste a classic personal access token.

1. In K127, open Connect GitHub (or Settings → Sync) and tap **Create a token**. On github.com, that opens a new classic token form with the **repo** box already checked.
2. Leave the **repo** box checked, then click **Generate token**.
3. Copy the token and paste it into K127.

This token can read and write the repositories it is allowed to see. K127 stores it in the Keychain on this device and does not put it in the vault.

A few limits to know:

- A **fine-grained** token cannot open someone else’s repository. It only reaches a repository you own or that your organization owns. If you need that kind of repository, use a classic token with the **repo** scope.
- Checking **gist** is optional. If you enable it, K127 can sync your reading position across your devices through a gist on your GitHub account.
- For **GitLab**, the token needs the **api** scope. For **Gitea** or **Forgejo**, the token needs repository read and write access (`write:repository`).

### What does HTTP 403 mean?

A 403 from GitHub is not one thing. K127 classifies it and shows a specific sentence. Your notes stay on this device.

| What you may see | What it means | What to try |
|---|---|---|
| HTTP 403, missing scope. The token needs the repo scope. | The token does not include the permission K127 uses for repositories. | Create a classic token with the **repo** box checked, then paste it again. |
| GitHub is waiting for this token to be authorized for the organization. | The repository is behind organization single sign-on (SAML). | On github.com, authorize this token for the organization, then try again. If GitHub sent an authorize link, K127 includes it in the message. |
| This token is missing a permission… | The token is signed in, but it lacks a named permission for the notes repository. | On github.com, edit the token, allow that permission for the notes repository, then paste it here again. |
| GitHub is busy. k127 will resume when GitHub allows more requests. | This 403 is a rate limit, not a bad token. | Wait, then try again. Your notes stay on this device. |
| GitHub refused this repository for this token. | GitHub returned 403, and it was not classified as a missing scope, SSO, a named permission, or a rate limit. | Check the token and the repository, then try again. Your notes stay on this device. |

Related messages that are not 403:

- **HTTP 401, bad token** — GitHub rejected the token. Check that it was created on this host, is current, and (if the repo is in an organization) is authorized for that organization’s SSO.
- **HTTP 404, repository not found or this token cannot see it** — the name may be misspelled, or the token was not given this repository. A fine-grained token also cannot see someone else’s repository; use a classic token with the **repo** scope in that case.

## How to get help

1. In the app, open **Help → Getting Started** or **Help → Keyboard Shortcuts**. Both work offline.
2. If that does not answer it, [open a GitHub issue on `diagonalcounty/k127-site`](https://github.com/diagonalcounty/k127-site/issues).

Please do not paste a personal access token into an issue or a screenshot.
