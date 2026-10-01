# Privacy Through Being Average: A Rational Guide to Firefox

Most modern browser hardening guides turn you into a digital outlier. By tweaking hundreds of hidden settings, installing dozens of niche extensions, and spoofing your user agent, you don't actually hide—you just create a highly specific, unique fingerprint that stands out like a neon sign. 

True browser privacy isn't about building an impenetrable fortress; **it’s about blending seamlessly into the crowd.** This repository outlines a minimalist philosophy: minimizing your browser's uniqueness while maximizing actual privacy benefits by doing the bare amount necessary.

---

## The Core Philosophy: "Blend In"

When it comes to tracking, **uniqueness is your enemy.** If your browser looks exactly like millions of other stock installations, tracking scripts cannot reliably identify you across different websites. 

This guide focuses strictly on the "Big Three" pillars of rational privacy without breaking the web or turning your browser into a maintenance nightmare.

---

## The 3-Step Setup

To achieve an optimal, average, yet highly private footprint, you only need to do three things:

### 1. Stick to Stock Settings
Leave your deep configuration alone. Avoid changing advanced `about:config` flags unless you absolutely know the trade-offs. The closer you stay to the baseline of standard users, the larger your crowd is.

### 2. Enable Strict Enhanced Tracking Protection
Firefox has built-in protections that do the heavy lifting for you without making you look unusual.
1. Open Firefox **Settings**.
2. Navigate to **Privacy & Security**.
3. Under *Enhanced Tracking Protection*, select **Strict**.

*Why this works:* In Strict mode, Firefox automatically blocks known fingerprinters, isolates cookies to prevent cross-site tracking, and subtly masks common fingerprinting vectors (like spoofing CPU core counts or randomizing canvas data) under a standardized umbrella.

### 3. Install uBlock Origin
The absolute best defense against tracking is preventing tracking scripts from loading in the first place. If a tracker can't execute its code, it can't measure your fingerprint.
* Install the official extension via [uBlock Origin](https://ublockorigin.com).
* Keep it on its default filter lists. Adding dozens of custom lists can make your network request patterns unique and accidentally break websites.

---

## Cosmetic Customization & Bloat

A common misconception is that changing your browser's visual interface alters your digital fingerprint. **It does not.** 

External websites and tracking scripts cannot see your internal user interface, your theme choices, or your home screen layout. Feel free to strip away the clutter:

* ✅ **Safe to change:** Disabling Pocket, removing shortcuts, turning off home screen recommendations, and hiding the bookmarks bar.
* ✅ **Safe to change:** Switching between Light, Dark, or colorful interface themes.
* ❌ **Avoid changing:** The actual dimensions of your viewing window. Avoid using strange, non-standard window sizes when browsing sensitive sites, as JavaScript *can* read your viewable screen dimensions.

Tailor the cosmetics to your liking to minimize visual bloat—your underlying privacy footprint remains safely average.

---

## What to Avoid

To maintain your "average" status, avoid these common privacy traps:
* **Extension Bloat:** Do not install multiple ad-blockers, privacy badges, or script-disablers. Each extension adds unique side-effects that scripts can detect. Stick to just uBlock Origin.
* **Aggressive Fingerprint Resistance (`resistFingerprinting`):** While Mozilla's advanced `privacy.resistFingerprinting` flag is incredibly secure, it forces extreme behaviors (like letterboxing your window and locking your timezone to UTC). This can break major websites and immediately flags you as an extreme privacy user.

---

## Summary

| Action | Impact on Privacy | Impact on Uniqueness |
| :--- | :--- | :--- |
| **ETP Strict Mode** | 🟢 High Protection | 🟢 Blends in with standard Firefox pool |
| **uBlock Origin (Default)** | 🟢 High Protection | 🟢 Standard network blocklists |
| **Removing Home Screen Bloat** | ⚪ Neutral | ⚪ Completely hidden from websites |
| **Dozens of Privacy Extensions**| 🔴 Unpredictable | 🔴 Makes your browser highly unique |

By doing less, you achieve more. Stay stock, stay strict, block the trackers, and disappear into the average user base.