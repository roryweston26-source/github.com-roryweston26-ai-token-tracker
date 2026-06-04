# AI Token Tracker — Privacy Policy

**Effective date: May 31, 2026**

---

## Single Purpose

AI Token Tracker has a single purpose: to read AI chat conversations already displayed in your browser and estimate the number of tokens, monetary cost, and water consumption associated with those conversations. All analysis is performed locally on your device. The extension has no secondary purpose.

---

## Summary

Your conversation text never leaves your device. The extension reads text that is already visible to you on screen and uses it locally to count tokens. The extension makes no network requests by default. If you optionally provide an Anthropic API key, only the text of your own messages (never AI responses) is sent to Anthropic's token-counting API — nothing else.

- Does **not** transmit conversation text to any external server.
- Does **not** sell, rent, or share any user data with third parties.
- Does **not** track users across websites or sessions.
- Does **not** collect analytics, telemetry, or usage statistics.
- Does **not** use your data for advertising or profiling.
- Does **not** store conversation content between browser sessions.
- Does **not** load any resources from external servers at runtime. All fonts, scripts, and data files are bundled inside the extension package.
- Does **not** make any network requests unless you optionally provide an Anthropic API key. When a key is provided, only the text of your own messages (not AI responses) is sent to Anthropic's token-counting API (`api.anthropic.com/v1/messages/count_tokens`). No other external connections are made under any circumstances.
- **Does** store your optional API key in `chrome.storage.session` (cleared automatically when the browser closes) and your model preference in `chrome.storage.local` (persisted on your device only).

---

## Data the Extension Accesses

### Conversation text (read-only, stays on device)

The extension uses a content script running inside your browser tab to read the visible text of AI chat pages you are already viewing — the same text you can see on screen. This text is used only to count tokens locally and is never transmitted anywhere. It is not written to disk and is discarded when the page is navigated away from or the browser is closed.

### Anthropic API key (optional, session-only)

If you choose to enter an Anthropic API key, it is stored using `chrome.storage.session`. Session storage is ephemeral: it is held in memory only for the duration of the current browser session and is automatically cleared when the browser closes. The key is never written to persistent storage and never synced to any remote server. It is used solely to call Anthropic's official token-counting endpoint (`api.anthropic.com/v1/messages/count_tokens`) on your behalf, using the message text already present in your browser — no conversation data is stored by this call. You can remove the key at any time using the "remove key" button in the panel.

### Model preference (local device only)

Your selected AI model is stored in `chrome.storage.local`, which keeps data on your device only and never syncs it to Google's servers or any other remote server. This preference is never transmitted anywhere.

### Active tab identity (not stored, not transmitted)

When the user clicks the extension icon, the browser grants temporary access to the active tab's numeric ID. This ID is stored in session memory solely to route messages between the side panel and the content script on that tab. The tab URL is not read, stored, or transmitted by the extension.

---

## Network Requests

When no API key is provided the extension makes **zero network requests**. All fonts, scripts, and pricing data are bundled inside the extension package; no content is loaded from external servers at runtime.

When an API key is provided, the only external connection the extension makes is to Anthropic's token-counting API (`api.anthropic.com/v1/messages/count_tokens`), using your own key. Only the text of your own messages is sent — AI responses are counted locally and never transmitted. This request is governed by [Anthropic's Privacy Policy](https://www.anthropic.com/privacy). No other external connections are made under any circumstances.

---

## Permission Justifications

The following table explains exactly why each permission is required. No permission is requested beyond what is necessary for the single stated purpose.

| Permission | Why it is required |
|---|---|
| `storage` | Stores your model preference in `chrome.storage.local` and your optional API key in `chrome.storage.session`, both on your device only. No data is synced remotely. |
| `sidePanel` | Required to open and render the side panel UI in which token counts and cost estimates are displayed. |
| `activeTab` | Grants temporary access to the currently-focused tab when the user clicks the extension icon. Used solely to open the side panel for that tab. The tab's URL is not read by the extension. Unlike the broader `tabs` permission, `activeTab` does not expose other open tabs. |
| `scripting` | Required to programmatically inject the content script into `x.com` tabs that are navigated to the Grok chat path (`x.com/grok` or `x.com/i/grok`). Injection is path-gated: the script is never injected on any other `x.com` page. This avoids declaring a broad `x.com/*` host permission for the whole domain. |
| Host: `api.anthropic.com` | Required only when the user provides an Anthropic API key. Used solely to call Anthropic's official token-counting API on the user's behalf. No request is made without an explicit API key. |
| Host: `claude.ai`, `chatgpt.com`, `chat.openai.com`, `gemini.google.com`, `grok.com`, `chat.mistral.ai`, `perplexity.ai`, `copilot.microsoft.com`, `poe.com`, `chat.deepseek.com` | Required to inject the content script that reads visible conversation text on each supported AI platform. Access is limited to these specific domains only. `x.com` is handled via the `scripting` permission (path-gated injection) rather than a blanket host permission. No other websites are accessed. |

---

## Data Retention

Conversation text is held in memory only for the duration of the active browser session and is never written to disk. It is discarded when the panel is closed or the page is navigated away from.

Your Anthropic API key is stored in `chrome.storage.session` and is automatically cleared when the browser closes. It does not persist between browser sessions.

Your model preference is stored in `chrome.storage.local` until you click "remove key" in the panel, which clears all locally stored data including your model preference, setup state, and internal version marker.

---

## Children's Privacy

This extension does not knowingly collect any information from children under 13. It does not collect personal information from any user of any age.

---

## Changes to This Policy

If this privacy policy is updated, the new version will be published at this URL and the effective date above will be updated. Continued use of the extension after a policy change constitutes acceptance of the updated policy.

---

## Contact

For questions or concerns about this privacy policy, please [open an issue](https://github.com/roryweston26-source/github.com-roryweston26-ai-token-tracker/issues) on the extension's GitHub repository.
