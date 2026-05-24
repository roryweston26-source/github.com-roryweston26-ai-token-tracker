[privacy-policy.html](https://github.com/user-attachments/files/28194239/privacy-policy.html)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>AI Token Tracker — Privacy Policy</title>
  <style>
    :root {
      --text:    #1a1a1a;
      --muted:   #555;
      --border:  #e0e0e0;
      --accent:  #1a73e8;
      --bg:      #ffffff;
      --surface: #f8f9fa;
    }
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Georgia, serif;
      max-width: 720px;
      margin: 0 auto;
      padding: 48px 28px 80px;
      color: var(--text);
      line-height: 1.75;
      background: var(--bg);
    }
    .header { border-bottom: 2px solid var(--border); padding-bottom: 24px; margin-bottom: 36px; }
    h1 { font-size: 26px; font-weight: 700; margin-bottom: 6px; }
    .meta { font-size: 13px; color: var(--muted); }
    h2 {
      font-size: 15px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.06em;
      color: var(--muted);
      margin-top: 44px;
      margin-bottom: 12px;
      padding-bottom: 6px;
      border-bottom: 1px solid var(--border);
    }
    p { font-size: 15px; color: #333; margin-bottom: 14px; }
    ul { margin: 0 0 14px 0; padding-left: 22px; }
    li { font-size: 15px; color: #333; margin-bottom: 7px; }
    .callout {
      background: var(--surface);
      border-left: 4px solid var(--accent);
      border-radius: 0 6px 6px 0;
      padding: 14px 18px;
      margin: 20px 0;
      font-size: 15px;
      color: #333;
    }
    .callout strong { color: var(--text); }
    table {
      width: 100%;
      border-collapse: collapse;
      font-size: 14px;
      margin: 16px 0 24px;
    }
    th {
      text-align: left;
      font-size: 11px;
      text-transform: uppercase;
      letter-spacing: 0.07em;
      color: var(--muted);
      padding: 8px 12px;
      background: var(--surface);
      border: 1px solid var(--border);
    }
    td {
      padding: 10px 12px;
      border: 1px solid var(--border);
      vertical-align: top;
      color: #333;
    }
    td:first-child { font-family: monospace; font-size: 13px; white-space: nowrap; color: var(--text); }
    a { color: var(--accent); text-decoration: none; }
    a:hover { text-decoration: underline; }
    .no { color: #c00; font-weight: 600; }
    .yes { color: #1a7340; font-weight: 600; }
  </style>
</head>
<body>

<div class="header">
  <h1>AI Token Tracker — Privacy Policy</h1>
  <div class="meta">Effective date: May 24, 2026 &nbsp;·&nbsp; Version 3.0</div>
</div>

<h2>Single Purpose</h2>
<p>
  AI Token Tracker has a single purpose: to read AI chat conversations already
  displayed in your browser and estimate the number of tokens, monetary cost, and
  water consumption associated with those conversations. All analysis is performed
  locally on your device. The extension does not have any secondary purpose.
</p>

<h2>Summary — What This Extension Does and Does Not Do</h2>
<div class="callout">
  <strong>Does not collect your data.</strong> Conversation text is read locally to
  count tokens and is never transmitted to any server controlled by this extension.
  No personal data, conversation content, browsing history, or usage statistics are
  collected, stored remotely, or shared with any third party.
</div>
<ul>
  <li><span class="no">Does not</span> transmit conversation text to any external server.</li>
  <li><span class="no">Does not</span> sell, rent, or share any user data with third parties.</li>
  <li><span class="no">Does not</span> track users across websites or sessions.</li>
  <li><span class="no">Does not</span> collect analytics, telemetry, or usage statistics.</li>
  <li><span class="no">Does not</span> use your data for advertising or profiling.</li>
  <li><span class="no">Does not</span> store conversation content between sessions.</li>
  <li><span class="no">Does not</span> make any network requests unless you provide an optional Anthropic API key.</li>
  <li><span class="yes">Does</span> store your optional API key and model preference locally on your device only, using <code>chrome.storage.local</code>.</li>
</ul>

<h2>Data the Extension Accesses</h2>

<p><strong>Conversation text (read-only, local only).</strong>
The extension reads the visible text content of AI chat pages you are already viewing — the same text visible to you on screen. This is done using a content script that runs inside your browser tab. The text is used only to count tokens and is never transmitted anywhere. It is not stored between sessions.</p>

<p><strong>Anthropic API key (optional, local only).</strong>
If you choose to enter an Anthropic API key, it is stored using <code>chrome.storage.local</code>, which stores data on your device only and never syncs it to Google's servers or any other server. The key is used solely to call Anthropic's official token-counting endpoint (<code>api.anthropic.com/v1/messages/count_tokens</code>) on your behalf. It is never sent to any server other than Anthropic's official API. You can delete the key at any time using the "remove key" button in the panel.</p>

<p><strong>Model preference (local only).</strong>
Your selected AI model is stored in <code>chrome.storage.local</code> so it persists between sessions. It is never transmitted anywhere.</p>

<p><strong>Active tab URL (read-only).</strong>
The extension reads the URL of your active tab to determine whether you are on a supported AI platform (e.g. claude.ai, chatgpt.com). No URL is stored or transmitted.</p>

<h2>Permission Justifications</h2>
<p>
  The following table explains exactly why each permission in the extension's
  manifest is required. No permission is requested beyond what is necessary for the
  single stated purpose.
</p>

<table>
  <thead>
    <tr>
      <th>Permission</th>
      <th>Why it is required</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>storage</td>
      <td>Stores your optional API key and model preference locally on your device using <code>chrome.storage.local</code>. No data is synced remotely.</td>
    </tr>
    <tr>
      <td>sidePanel</td>
      <td>Required to open and render the side panel UI in which token counts and cost estimates are displayed.</td>
    </tr>
    <tr>
      <td>activeTab</td>
      <td>Required to read the URL of your current tab to determine whether it is a supported AI platform.</td>
    </tr>
    <tr>
      <td>scripting</td>
      <td>Required to inject the content script that reads visible conversation text from the AI chat page for local token counting.</td>
    </tr>
    <tr>
      <td>tabs</td>
      <td>Required to identify the active tab and communicate between the side panel and the content script running on the AI chat page.</td>
    </tr>
    <tr>
      <td>Host: api.anthropic.com</td>
      <td>Required only if the user provides an Anthropic API key. Used solely to call Anthropic's official token-counting API on the user's behalf. No data is sent without the user explicitly providing their own API key.</td>
    </tr>
    <tr>
      <td>Host: claude.ai, chatgpt.com, chat.openai.com, gemini.google.com, grok.com, x.com, chat.mistral.ai, perplexity.ai, copilot.microsoft.com, poe.com, chat.deepseek.com</td>
      <td>Required to inject the content script that reads visible conversation text on each supported AI platform. Access is limited to these specific domains only. The extension does not access any other websites.</td>
    </tr>
  </tbody>
</table>

<h2>Third-Party Services</h2>
<p>
  The only third-party service this extension communicates with is the
  <strong>Anthropic API</strong> (<code>api.anthropic.com</code>), and only when
  the user has explicitly provided their own Anthropic API key. In that case, a
  short text sample is sent to Anthropic's token-counting endpoint to obtain an
  exact token count. This request is governed by
  <a href="https://www.anthropic.com/legal/privacy" target="_blank">Anthropic's Privacy Policy</a>.
  No other third-party services are contacted.
</p>
<p>
  If no API key is provided, the extension operates entirely offline — no network
  requests are made at any time.
</p>

<h2>Data Retention</h2>
<p>
  Conversation text is held in memory only for the duration of the current browser
  session and is discarded immediately when the side panel is closed or the page is
  navigated away from. It is never written to disk.
</p>
<p>
  Your API key and model preference remain in <code>chrome.storage.local</code>
  until you click "remove key" in the side panel, which clears all stored data
  immediately.
</p>

<h2>Children's Privacy</h2>
<p>
  This extension does not knowingly collect any information from children under 13.
  It does not collect personal information from any user of any age.
</p>

<h2>Changes to This Policy</h2>
<p>
  If this privacy policy is updated, the new version will be published at this URL
  and the effective date above will be updated. Continued use of the extension after
  a policy change constitutes acceptance of the updated policy.
</p>

<h2>Contact</h2>
<p>
  For questions or concerns about this privacy policy, please open an issue on the
  extension's GitHub repository or contact the developer directly at the email
  address listed in the Chrome Web Store listing.
</p>

</body>
</html>
