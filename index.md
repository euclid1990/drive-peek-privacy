# Privacy policy — Drive Peek

Last updated: 2026-11-02

## Summary

Drive Peek does not collect, store on any server, sell, or share your data. It has no analytics. Your file content stays in your browser.

## What the extension reads

- The address and page title of Google Drive tabs (drive.google.com), the file name and file id Drive exposes in the page for the open file, and the parts of Drive's viewer needed to place the toggle and the preview frame. The file name is used to decide whether the file is a supported type (HTML, JSON or source code), to check that the downloaded file is the one you opened, and it is shown in the viewer's title. The extension inserts a toggle control into Drive's toolbar and an iframe over the content area, and changes nothing else on the page.
- The content of a supported file you open in Drive. This is "website content" in the Chrome Web Store's terms.

## The only network requests

For a supported file, the extension sends a request to `https://drive.usercontent.google.com/download` to download the file. If you are signed into several Google accounts, Google answers 403 when the file belongs to another account, so the extension repeats the request once per signed-in account (adding `authuser=N` to the address, N being the account's position in your browser) until one is allowed. It stops at the first success or if Google redirects to its sign-in page, and it remembers which account worked only in memory, for as long as the extension's background worker runs. Every request uses your existing Google sign-in (browser cookies); the extension does not ask for your password, uses no OAuth token, and asks the browser not to use its cache (`cache: no-store`). "Open in new tab", Reload in the full viewer, and Preview chosen on a file opened as raw text (Auto preview off) repeat the same requests. With Auto preview off, nothing from the file is loaded or run until you choose Preview. The extension makes no other network request of its own (all of the above go to that one address), and the viewer page itself never requests the remote resources a file refers to. The only other requests come from the content of the file you open, as described under "Files you open" below.

Files over 30 MiB are not downloaded at all (the preview shows a notice instead). If the request ends on a Google sign-in page, the response is discarded unread.

## What is kept, and for how long

- File content: held in the extension's own IndexedDB (on this computer, readable by this extension only) under a one-time key, deleted the moment the preview reads it, and in any case removed after 60 seconds or when the extension next starts. The entry holds the Drive file id, the file name, the file content, a timestamp. The viewer page removes the entry the moment it reads it. If the viewer never reads it (for example the tab was closed first), the extension deletes the entry the next time it stores a preview, as long as the entry is more than about 60 seconds old; at the latest it is gone when the browser closes.
- Settings: `chrome.storage.local` keeps only your on/off switches (overall, Auto preview, and per format). No file names, content, or history are stored there.

## What is not done

- No analytics, tracking, advertising, or crash reporting.
- No third parties: file content and settings are never sent to the developer or anyone else.
- No sale of data, and no use or transfer of data for anything other than the extension's single purpose (rendering HTML, JSON and source code files opened in Drive).
- No file names or content are written to the browser console.
- The extension has no user accounts and keeps no profile of you.

## Chrome Web Store data disclosure

| Data type | Accessed | Collected off-device | Sold | Transferred to third parties | Used outside the single purpose |
|---|---|---|---|---|---|
| Website content (file text from Drive) | Yes | No | No | No | No |
| Everything else (personal information, health, financial, authentication, location, web history, user activity) | No | No | No | No | No |

Certifications for the form: data is not sold or transferred to third parties outside approved use cases; not used for purposes unrelated to the single purpose; not used for creditworthiness or lending.

## Files you open

HTML: an HTML file is shown inside an isolated sandbox page of the extension, which is displayed in the frame the extension adds to the Drive page. Scripts in that file (including scripts it loads from other https sites) are the file author's own and run without access to the extension or to your Drive page; their own network requests are outside this policy.

JSON: shown as an escaped tree or text; it loads nothing from other sites.

Code (source files such as .js, .ts, .py, .java, .php, .go, .rb, .cs, .cpp, .c, .dart, .ex, .erl, .sh, .m, .swift, .pl, .scss, .css, .scala, .sql, .xml, .tf, .dockerfile, .rst, .sol, Dockerfile): shown as escaped, syntax-highlighted text with line numbers. The highlighting library (highlight.js, BSD-3-Clause) is bundled in the extension and runs on your computer; the file content is not sent anywhere and nothing is loaded from other sites.

## Changes and contact

Changes will be posted at this URL with a new date. Contact: [euclid1990@gmail.com](mailto:euclid1990@gmail.com).
