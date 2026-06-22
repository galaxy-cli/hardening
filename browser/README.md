# Ultra-Private Firefox Browser Configuration

This repository provides the configuration steps and documentation for an advanced, hardened web browser setup. By combining an optimized open-source engine with aggressive script blocking and strict local state management, this configuration shields your data from 99% of modern corporate surveillance, cross-site trackers, and fingerprinting scripts.

---

## Components & Installation

### 1. The Engine: Mozilla Firefox
Firefox is chosen as the foundational web browser due to its open-source nature and robust configuration architecture (`about:config`), which allows deep manipulation of browser flags.
* **Action**: Download and install the latest stable version of [Firefox](https://www.firefox.com/en-US/).

### 2. The Hardening Layer: arkenfox user.js
The `arkenfox user.js` template is a configuration file that enforces strict privacy and security settings. It disables telemetry, activates native anti-fingerprinting configurations (RFB), and restricts hidden API access.
* **Action**:
  1. Locate your Firefox **Profile Directory** by navigating to `about:support` in the URL bar.
  2. Download the latest `user.js` file from the [official arkenfox GitHub repository](https://https://github.com/arkenfox/user.js/).
  3. Move the downloaded `user.js` file into your profile folder.
  4. Restart Firefox to load the configuration.

### 3. The Shield: uBlock Origin
uBlock Origin is used for wide-spectrum content filtering, preventing tracking networks and malicious advertisements from executing in the DOM.
* **Action**: Install the [uBlock Origin Firefox Add-on](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/). Keep filter lists updated to their default recommended values.

### 4. The Default Engine: DuckDuckGo
DuckDuckGo is the primary search tool to ensure queries are not tied to a permanent advertising identifier.
* **Action**: Navigate to `Settings -> Search` in Firefox and change the default search engine to **DuckDuckGo**.

---

## Session Management: Clear History on Close

To eliminate local state tracking and "zombie cookies," the environment is configured to wipe all volatile data upon browser shutdown.

### Configuration Steps
1. Open Firefox **Settings**.
2. Navigate to **Privacy & Security**.
3. Scroll down to the **History** section.
4. Set **Firefox will** to `Use custom settings for history`.
5. Check the box for **Clear history when Firefox closes**.
6. Click **Settings...** next to it and ensure the following are checked:
   * Browsing & download history
   * Cookies
   * Cache
   * Active logins
   * Form & search history
   * Site settings (Optional: uncheck if you want to keep persistent site-specific permissions)
