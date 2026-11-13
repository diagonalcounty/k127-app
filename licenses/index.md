---
title: Licenses
---

# Licenses

K127 is built on other people's work. The libraries and fonts below ship inside the iPad app — they are not fetched from a network at runtime — and we keep their licenses here and in the app (Settings → Licenses). Thank you.

This page matches the in-app Licenses list and the notice files in [`diagonalcounty/k127`](https://github.com/diagonalcounty/k127) at `origin/main` (commit [`917d9a8a`](https://github.com/diagonalcounty/k127/commit/917d9a8a)). Each row links to the full notice or license text in this repository.

K127's own source is under the MIT license in that repository. That grant does not relicense the third-party work below.

## Written offer for LGPL components

LibXDiff is statically linked into K127, inside the libgit2 xcframework. Its header says it is licensed under the [GNU Lesser General Public License, version 2.1 or later](texts/lgpl-2.1.txt).

The copy of LibXDiff used in K127 is the tree vendored in libgit2 1.3.1:

- [libgit2 `src/xdiff` at tag v1.3.1](https://github.com/libgit2/libgit2/tree/v1.3.1/src/xdiff) (the source actually compiled into the app)
- Author: Davide Libenzi. The original LibXDiff project is at [xmailserver.org/xdiff-lib.html](http://www.xmailserver.org/xdiff-lib.html).

For at least three years after each release of K127, if you ask, we will provide:

- the corresponding source of those LGPL libraries as used in that release of K127, and
- the K127 object files and build instructions needed to relink the app with a modified version of those libraries.

To request that, [open an issue on this repository](https://github.com/diagonalcounty/k127-app/issues). Please name the K127 version (for example 0.1.0) and which library you need.

**libiconv.** K127 dynamically links the system `libiconv` from the iOS SDK. It is not inside the xcframework. Apple's published libiconv sources have used different licenses in different drops (an older GNU libiconv drop labeled LGPL, and later Citrus / FreeBSD drops labeled BSD). Which drop a given K127 iOS build links has not been determined, so we do not list libiconv here as a definite LGPL component. If you believe the libiconv in your OS is LGPL and you need corresponding source or relink materials, open an issue and we will respond with what we can provide.

This offer is only for the LGPL libraries described above. It does not change the licenses of the other components on this page, and it does not relicense K127.

## Components in the app

| Component | Version or commit | License | Notice |
|---|---|---|---|
| [MiniGit](https://github.com/diagonalcounty/MiniGit) (fork of [light-tech/MiniGit](https://github.com/light-tech/MiniGit); XGit product only) | Pinned [`bc14e1fdbe2eb24cf012a5776ff9759eb21bb174`](https://github.com/diagonalcounty/MiniGit/commit/bc14e1fdbe2eb24cf012a5776ff9759eb21bb174) | GPL-2.0 with linking exception | [minigit-NOTICE.txt](texts/minigit-NOTICE.txt). The full license text is the same as [libgit2-NOTICE.txt](texts/libgit2-NOTICE.txt). |
| [libgit2](https://github.com/libgit2/libgit2/tree/v1.3.1) | 1.3.1, statically linked inside MiniGit's xcframework ([LibGit2-On-iOS v1.3.1](https://github.com/light-tech/LibGit2-On-iOS/releases/tag/v1.3.1)) | GPL-2.0 with linking exception | [libgit2-NOTICE.txt](texts/libgit2-NOTICE.txt) (COPYING at tag v1.3.1) |
| [LibXDiff](https://github.com/libgit2/libgit2/tree/v1.3.1/src/xdiff) | Vendored in libgit2 1.3.1 (`src/xdiff`); statically linked | LGPL-2.1-or-later | [libxdiff-NOTICE.txt](texts/libxdiff-NOTICE.txt), [lgpl-2.1.txt](texts/lgpl-2.1.txt) |
| libiconv | System library, dynamically linked (`.linkedLibrary("iconv")`). Version is the iOS SDK's libiconv, not pinned by K127. | Depends on the OS drop; see the note above | [libiconv-NOTICE.txt](texts/libiconv-NOTICE.txt) |
| [OpenSSL](https://github.com/openssl/openssl/tree/openssl-3.0.4) | 3.0.4, statically linked inside the libgit2 xcframework | Apache-2.0 | [openssl-NOTICE.txt](texts/openssl-NOTICE.txt) |
| [libssh2](https://github.com/libssh2/libssh2/tree/libssh2-1.10.0) | 1.10.0, statically linked inside the libgit2 xcframework | BSD-3-Clause | [libssh2-NOTICE.txt](texts/libssh2-NOTICE.txt) |
| [PCRE](https://github.com/light-tech/PCRE) | 8.45 (2021-06-15), static objects inside the libgit2 xcframework | BSD (as in the shipped `pcre.h`) | [pcre-NOTICE.txt](texts/pcre-NOTICE.txt). See [PCRE](#pcre-in-the-xcframework) below. |
| zlib | System `libz`, dynamically linked (`.linkedLibrary("z")`). Version is the iOS SDK's zlib, not pinned by K127. | zlib | [zlib-NOTICE.txt](texts/zlib-NOTICE.txt) |
| [http-parser](https://github.com/libgit2/libgit2/tree/v1.3.1/deps/http-parser) | Vendored in libgit2 1.3.1; statically linked | MIT | [http-parser-NOTICE.txt](texts/http-parser-NOTICE.txt) |
| [ntlmclient](https://github.com/libgit2/libgit2/tree/v1.3.1/deps/ntlmclient) | 0.9.0 (header); statically linked. Vendored `LICENSE.txt` is absent from libgit2 1.3.1; the MIT text is in the notice. | MIT | [ntlmclient-NOTICE.txt](texts/ntlmclient-NOTICE.txt) |
| utf8.h | Compiled into ntlm.c inside the xcframework | The Unlicense | [utf8-h-NOTICE.txt](texts/utf8-h-NOTICE.txt) |
| wildmatch | Vendored in libgit2 1.3.1; statically linked | BSD | [wildmatch-NOTICE.txt](texts/wildmatch-NOTICE.txt) |
| SHA-1 collision detection | Vendored in libgit2 1.3.1; statically linked | MIT | [sha1dc-NOTICE.txt](texts/sha1dc-NOTICE.txt) |
| winhttp.c.o | One archive member in the libgit2 1.3.1 xcframework | See [winhttp.c.o](#winhttp-c-o) below | [winhttp-object-NOTICE.txt](texts/winhttp-object-NOTICE.txt) |
| [CodeMirror 6](https://github.com/codemirror/dev) | Vendored as `editor.bundle.js` (no CDN). Lockfile versions include `@codemirror/view` 6.43.11, `@codemirror/state` 6.7.4, `@codemirror/commands` 6.11.0, `@codemirror/language` 6.12.4, `@codemirror/lang-markdown` 6.5.2, `@codemirror/theme-one-dark` 6.1.3, `@codemirror/search` 6.7.2, `@codemirror/autocomplete` 6.20.3 | MIT | [codemirror-NOTICE.txt](texts/codemirror-NOTICE.txt) |
| [Mermaid](https://github.com/mermaid-js/mermaid) | mermaid@11.17.2, vendored as `mermaid.min.js` (no CDN) | MIT | [mermaid-NOTICE.txt](texts/mermaid-NOTICE.txt) |
| [Excalidraw](https://github.com/excalidraw/excalidraw) | @excalidraw/excalidraw@0.18.1, vendored as `drawing.bundle.js` (view-only `exportToSvg`; no CDN) | MIT | [excalidraw-NOTICE.txt](texts/excalidraw-NOTICE.txt) |
| [lz-string](https://github.com/pieroxy/lz-string) | 1.5.0, bundled with the Excalidraw viewer | MIT | [lz-string-NOTICE.txt](texts/lz-string-NOTICE.txt) |
| [React](https://github.com/facebook/react) | react@18.3.1 and react-dom@18.3.1, bundled with the Excalidraw viewer | MIT | [react-NOTICE.txt](texts/react-NOTICE.txt) |
| [Lezer](https://github.com/lezer-parser) | `@lezer/common` 1.5.2 and related `@lezer/*` packages, bundled with CodeMirror 6 | MIT | [lezer-NOTICE.txt](texts/lezer-NOTICE.txt) |
| style-mod | 4.1.3 (CodeMirror 6 transitive) | MIT | [style-mod-NOTICE.txt](texts/style-mod-NOTICE.txt) |
| crelt | 1.0.7 (CodeMirror 6 transitive) | MIT | [crelt-NOTICE.txt](texts/crelt-NOTICE.txt) |
| w3c-keyname | 2.2.8 (CodeMirror 6 transitive) | MIT | [w3c-keyname-NOTICE.txt](texts/w3c-keyname-NOTICE.txt) |
| [@marijn/find-cluster-break](https://github.com/marijnh/find-cluster-break) | 1.0.4 (CodeMirror 6 transitive) | MIT | [find-cluster-break-NOTICE.txt](texts/find-cluster-break-NOTICE.txt) |
| Plus Jakarta Sans | Bundled ExtraLight and Medium faces; brand row font for Vault and AI titles | SIL OFL 1.1 | [plus-jakarta-sans-OFL.txt](texts/plus-jakarta-sans-OFL.txt) |
| Annie Use Your Telescope | Optional handwritten face for the note in Preview | SIL OFL 1.1 | [annie-use-your-telescope-OFL.txt](texts/annie-use-your-telescope-OFL.txt) |
| Yuyu | Optional writing face for the note in Preview | SIL OFL 1.1 | [yuyu-OFL.txt](texts/yuyu-OFL.txt) |
| Spectral | Optional serif writing face for the note in Preview | SIL OFL 1.1 | [spectral-OFL.txt](texts/spectral-OFL.txt) |
| Literata | Optional serif writing face for the note in Preview | SIL OFL 1.1 | [literata-OFL.txt](texts/literata-OFL.txt) |
| Source Serif 4 | Optional serif writing face for the note in Preview | SIL OFL 1.1 | [source-serif-4-OFL.txt](texts/source-serif-4-OFL.txt) |
| Atkinson Hyperlegible | Optional sans writing face for the note in Preview | SIL OFL 1.1 | [atkinson-hyperlegible-OFL.txt](texts/atkinson-hyperlegible-OFL.txt) |
| Source Sans 3 | Optional sans writing face for the note in Preview | SIL OFL 1.1 | [source-sans-3-OFL.txt](texts/source-sans-3-OFL.txt) |
| Figtree | Optional sans writing face for the note in Preview | SIL OFL 1.1 | [figtree-OFL.txt](texts/figtree-OFL.txt) |
| Crimson Pro | Optional serif writing face for the note in Preview | SIL OFL 1.1 | [crimson-pro-OFL.txt](texts/crimson-pro-OFL.txt) |

The Excalidraw and Mermaid bundles also pull in transitive packages. Those are recorded in `docs/LICENSES.md` in the K127 repo. Most are MIT; some are Apache-2.0, ISC, BSD-3-Clause, or similar. They do not have their own rows in the in-app Licenses pane, so they are not given separate notice files here.

esbuild, jsdom, and linkedom are build- or test-only tools and are not shipped in the app. They are omitted from the in-app list and from this page.

### MiniGit pin

K127 pins MiniGit to [`bc14e1fdbe2eb24cf012a5776ff9759eb21bb174`](https://github.com/diagonalcounty/MiniGit/commit/bc14e1fdbe2eb24cf012a5776ff9759eb21bb174) in `Package.resolved` and the Xcode project. That revision is one commit after [`2d289c51`](https://github.com/diagonalcounty/MiniGit/commit/2d289c51bf24ab5bb60cfa0593c4fafef873f046), which added LICENSE and NOTICE on the `xgit-additions` branch. The later pin is what `origin/main` actually builds.

## PCRE
{: #pcre-in-the-xcframework}

PCRE **is present** in the shipping xcframework.

The LibGit2-On-iOS v1.3.1 build includes PCRE 8.45 (dated 2021-06-15). The archive contains 22 `pcre_*.c.o` members and a `_pcre_version` symbol. Headers report `PCRE_MAJOR` 8, `PCRE_MINOR` 45. The license in the shipped `pcre.h` is the University of Cambridge BSD terms.

The in-app notice still says whether libgit2 *calls* those objects was not confirmed. MiniGit's NOTICE at the pinned revision goes a step further: the archive has `regexp.c.o`, which references `pcre_*` symbols, and it does not contain GNU regex sources. libgit2 1.3.1 can also be built to use the system regex instead of PCRE; that choice was not re-verified here beyond those archive facts. The PCRE license applies to the PCRE objects that are shipped.

## winhttp.c.o
{: #winhttp-c-o}

The iOS static archive contains one member named `winhttp.c.o`. Two different things in libgit2 1.3.1 share the “winhttp” name, and they are easy to confuse.

1. **`src/transports/winhttp.c`** is libgit2's own Windows HTTP transport. Its copyright header says it is part of libgit2, distributed under the GNU GPL v2 with a linking exception. The entire implementation is wrapped in `#ifdef GIT_WINHTTP`. On iOS that macro is not set, so the file compiles to an empty translation unit. MiniGit's NOTICE at the pinned revision reports that, on the `ios-arm64` slice, `winhttp.c.o` defines no symbols beyond a local label.

2. **`deps/winhttp`** is a separate MinGW import-library and header set (Francois Gouget). libgit2's COPYING licenses that directory under LGPL-2.1-or-later. At tag v1.3.1 it contains headers and `.def` files only — there is no `winhttp.c` in that directory to compile into `winhttp.c.o`.

The archive member in the iOS xcframework is the empty libgit2 transport object, not a compilation of the LGPL import library. It is unused on iOS. It is not included in the written offer above. The in-app notice, written before this check, still flags the member as unverified; the finding here is from reading libgit2 v1.3.1 and MiniGit's NOTICE at `bc14e1fd`.

## Bundled themes

The Licenses pane also lists community themes shipped inside the app. Each is a point-in-time MIT snapshot. The pane links to the upstream repository.

| Theme | Author (manifest) | License | Snapshot | Repository |
|---|---|---|---|---|
| Minimal | kepano | MIT | kepano/obsidian-minimal@ccc832cff3 (`theme.css` 9.1.1) | [obsidian-minimal](https://github.com/kepano/obsidian-minimal) |
| Border | Akifyss | MIT | akifyss/obsidian-border@05d2df5d15 (`theme.css` 1.13.8) | [obsidian-border](https://github.com/akifyss/obsidian-border) |
| Blue Topaz | WhyI & Pkmer | MIT | pkm-er/Blue-Topaz_Obsidian-css@54821893b8 (`theme.css` 2026081501) | [Blue-Topaz_Obsidian-css](https://github.com/pkm-er/Blue-Topaz_Obsidian-css) |
| Baseline | Alexis C | MIT | svnaxis/obsidian-baseline@60dabdf3c7 (`theme.css` 4.0.0) | [obsidian-baseline](https://github.com/svnaxis/obsidian-baseline) |
| Cupertino | Alexis C | MIT | svnaxis/obsidian-cupertino@78a353a525 (`theme.css` 4.0.0) | [obsidian-cupertino](https://github.com/svnaxis/obsidian-cupertino) |
| Things | colineckert | MIT | colineckert/obsidian-things@9b8bef93d3 (`theme.css` 2.2.4) | [obsidian-things](https://github.com/colineckert/obsidian-things) |
| Maple | subframe7536 | MIT | subframe7536/obsidian-theme-maple@5f5521e111 (`theme.css` 1.5.12) | [obsidian-theme-maple](https://github.com/subframe7536/obsidian-theme-maple) |

Only Minimal and Blue Topaz carry the MIT text inside the shipped `theme.css`. The other five are declared MIT in K127's theme catalog; there is no separate license file for them in the K127 repo. A theme a person loads from their own vault is user content, not a K127 dependency, and is credited in the Themes sheet while it is active.

## Maps

Map views in bases use Apple MapKit, a system framework. Map images load from Apple Maps over the internet. Nothing from your notes is sent except the map area being shown. MapKit is not a third-party package with a notice file in this repository.

## Requesting LGPL source or object files

[Open an issue](https://github.com/diagonalcounty/k127-app/issues) on this repository. That is also how to [contact us](../support/) about the app.
