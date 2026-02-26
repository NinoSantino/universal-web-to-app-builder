# Universal Web-to-App Builder

**Build desktop apps from any website on older macOS versions without upgrading**

---

## The Problem

[Pake](https://github.com/tw93/Pake) is an amazing Rust-based tool that converts any webpage into a native desktop app - lightweight, fast, and efficient (typically 5-10MB vs 100MB+ Electron apps).

**But there's a catch:**

- **Pake CLI requires macOS 12+ to build apps locally**
- Many developers, creators, and producers are on Catalina (10.15), Big Sur (11), or older systems
- The build tools (specifically esbuild and other dependencies) fail on older macOS versions with errors like `Symbol not found: _SecTrustCopyCertificateChain`

**This creates an artificial barrier:** people with older hardware can't create the tools they need to improve their workflows.

**But here's the good news:** You don't actually need to upgrade. You just need to build differently.

---

## The Solution: GitHub Actions

Pake already includes a **GitHub Actions workflow** that builds apps on cloud servers (running macOS 12+). This means:

- ✅ **No local CLI installation needed**
- ✅ **No macOS upgrade required**
- ✅ **Works from ANY macOS version** (even Catalina 10.15)
- ✅ **Finished apps run on macOS 10.15+**
- ✅ **Completely free** (GitHub Actions is free for public repos)

**You just configure the build in your browser, and GitHub's servers do all the heavy lifting.**

---

## How to Build Your Own Desktop Apps (Step-by-Step)

### Prerequisites

- Any website URL you want to turn into a desktop app
- That's it.

### Step 1: Fork the Pake Repository

1. Go to the [original Pake repo](https://github.com/tw93/Pake)
2. Click **Fork** (top right corner)
3. This creates your own copy of Pake in your GitHub account

### Step 2: Enable GitHub Actions

1. In your forked repo, go to the **Actions** tab
2. You'll see a message: _"Workflows aren't being run on this forked repository"_
3. Click **"I understand my workflows, go ahead and enable them"**

### Step 3: Run the Build Workflow

1. In the Actions tab, look at the left sidebar
2. Click **"Build App With Pake CLI"**
3. Click the **"Run workflow"** button (top right)
4. Fill in the form:

**Required Fields:**

- **Platform**: Select `macos-latest`
- **Website URL**: The webpage you want to turn into an app (e.g., `https://example.com`)
- **App name**: Name for your app (e.g., `MyAwesomeApp`)

**Optional Fields:**

- **Icon URL**: Leave empty to auto-fetch the website's icon, or provide a custom icon URL
- **Window width**: Default is `1200` (pixels)
- **Window height**: Default is `800` (pixels)
- **Start in fullscreen mode**: Leave unchecked (unless you want fullscreen)
- **Hide title bar** (macOS only): Check this for a cleaner look
- **Universal binary** (macOS only): Check this to support both Intel and Apple Silicon Macs
- **Package formats**: Leave empty for macOS builds (this is for Linux)

5. Click **"Run workflow"** at the bottom

### Step 4: Wait for the Build

- The build takes **10-15 minutes**
- You'll see it appear in the workflow runs list
- Watch the progress - it'll show green checkmarks as each step completes

### Step 5: Download Your App

1. Click on the completed workflow run (green checkmark)
2. Scroll to the bottom - look for the **"Artifacts"** section
3. Click on your app file (e.g., `MyAwesomeApp-macOS`)
4. It downloads as a .zip file

### Step 6: Install and Use

1. Unzip the downloaded file
2. Open the `.dmg` file
3. Drag the app to your Applications folder
4. Launch from Applications
   - **First launch:** Right-click → Open (to bypass macOS security warning)
   - **If it still blocks you:** Go to System Preferences → Privacy & Security → Click "Open Anyway"
5. Add to your Dock for quick access (right-click app icon → Options → Keep in Dock)

**That's it. You just built a desktop app on GitHub's cloud servers. Your old Mac didn't hold you back.**

---

## Real-World Example

I'm a music producer and sound engineer on macOS Catalina 10.15. I built **[TunebatAnalyzer](https://github.com/NinoSantino/Pake/releases)** - a desktop app for analyzing BPM and key of beats/instrumentals - using this exact method.

**Settings I used:**

- Platform: `macos-latest`
- URL: `https://tunebat.com/Analyzer`
- Name: `TunebatAnalyzer`
- Window: `1200x800`
- Hide title bar: ✅
- Universal binary: ✅

**Result:** A 9MB native macOS app that I use daily before recording sessions, built entirely on GitHub's servers.

---

## What Can You Build?

**Turn websites that DON'T have desktop apps into native macOS applications.**

### Good Use Cases:

- **Web tools you use daily** that only exist in browsers
- **Internal company dashboards** or admin panels
- **Niche tools** without official desktop versions
- **Custom web apps** you've built
- **Documentation sites** you reference constantly
- **Web-based calculators or analyzers** (like Tunebat)
- **Monitoring dashboards** for servers, analytics, etc.
- **Any browser-based workflow** you want quick dock access to

**If you're constantly opening a browser tab for something, turn it into an app instead.**

---

## Why Use Pake Instead of Electron?

| Feature           | Pake (Tauri/Rust)     | Electron           |
| ----------------- | --------------------- | ------------------ |
| **App Size**      | ~5-10MB               | 100-200MB+         |
| **Memory Usage**  | Low                   | High               |
| **Startup Speed** | Fast                  | Slower             |
| **Technology**    | Rust + native webview | Chromium + Node.js |
| **Performance**   | Native                | Heavier            |

**Pake apps are 20x smaller and way more efficient.**

---

## Troubleshooting

### "Build failed" - Check the logs

- Click on the failed workflow run
- Click on the "build" job
- Read the error message
- Common issues: invalid URL, incorrect settings, network timeout

### "Security warning when opening app"

- Right-click the app → Open (instead of double-clicking)
- macOS will ask for confirmation - click "Open"
- If it still blocks you: Go to System Preferences → Privacy & Security → Click "Open Anyway"
- This only happens on first launch

### "App won't run on my Mac"

- Make sure you're on macOS 10.15 (Catalina) or later
- If you selected Intel-only build, it won't work on Apple Silicon (and vice versa)
- Use "Universal binary" option to support both

### "Workflow not showing up"

- Make sure you enabled GitHub Actions in your fork
- Check that you forked the main Pake repo, not someone else's fork

---

## System Requirements

**To BUILD apps (using GitHub Actions):**

- Any macOS version (even 10.15 Catalina)
- Internet connection

**To RUN the finished apps:**

- macOS 10.15 (Catalina) or later
- Intel or Apple Silicon Mac (use Universal binary for compatibility)

---

## Philosophy

Not everyone has the latest hardware, and that shouldn't stop anyone from building useful tools.

This guide exists because I believe **technology should be accessible to everyone**, regardless of the age of their equipment. If you're a developer, creator, producer, or just someone who wants a better workflow - you deserve to build the tools you need.

**Your old Mac is still powerful. Don't let arbitrary system requirements tell you otherwise.**

---

## Contributing

Found a better way to do this? Have suggestions? Want to add examples?

- Open an issue
- Submit a pull request
- Share your own apps built with this method

Let's make this resource better together.

---

## Credits

- **Pake**: Built by [tw93](https://github.com/tw93/Pake) - the real hero here
- **Tauri**: The Rust framework that makes Pake possible
- **This guide**: Created by someone tired of being told their Mac is "too old"

---

## Examples Built With This Method

- [TunebatAnalyzer](https://github.com/NinoSantino/universal-web-to-app-builder) - Audio analysis tool for music producers

_Want your app listed here? Open an issue with a link to your release!_

---

**Built with Pake | Powered by Tauri & Rust | Accessible to everyone with an older Mac**
