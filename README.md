<div align="center">

<img src="myurllogo.png" alt="URLz Logo" width="100" height="100"/>

# URLz — Custom Link Shortener

### *Create Memorable Short Links, Instantly — urlz.site/anything*

[![Live Demo](https://img.shields.io/badge/🚀_Live_Demo-Visit_App-00bcd4?style=for-the-badge)](https://urlz.site/)
[![PWA](https://img.shields.io/badge/PWA-Installable-4CAF50?style=for-the-badge&logo=googlechrome&logoColor=white)](https://urlz.site/)
[![Author](https://img.shields.io/badge/Author-Manikandan_N-ff6b6b?style=for-the-badge&logo=github)](https://github.com/manikandan-n-07)

</div>

---

## Table of Contents

- [What is Custom URLz?](#what-is-custom-urlz)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Setup and Deployment](#setup-and-deployment)
- [How to Use](#how-to-use)
- [Configuration](#configuration)
- [Pages Overview](#pages-overview)
- [Security Notes](#security-notes)
- [Contributing](#contributing)
- [Author](#author)

---

## What is Custom URLz?

**URLz** is a sleek, serverless custom URL shortener that lets you create clean, branded short links on your own domain — instantly. Instead of random characters, you choose a meaningful path like `urlz.site/event-signup` or `urlz.site/portfolio`. Powered by Google Apps Script as a zero-cost backend and deployed as a Progressive Web App, URLz works beautifully on desktop and mobile.

> *"Turn any long link into a custom, memorable URL — your domain, your rules."*

---

## Features

| Feature | Description |
|---|---|
| 🔗 **Custom Short Links** | Choose your own slug — create branded URLs like `urlz.site/your-keyword` |
| ✅ **Real-Time Slug Availability Check** | Instantly checks if your chosen link ID is already taken before you submit |
| 🌐 **Live URL Validation** | Validates destination URL format on the fly with instant feedback |
| ⏱️ **Deployment Countdown** | Visual 30-second countdown shows exactly when your new link goes live |
| 🕐 **Session Link History** | All links created in the current session are saved and displayed with copy buttons |
| 📋 **One-Click Copy** | Copy your short link to clipboard instantly with a single button |
| 🔍 **Search Page** | Dedicated search interface to look up existing short links |
| 🔐 **Admin Panel** | Password-protected admin login page for link management |
| ✉️ **Contact Form** | Built-in validated contact form with real-time submission feedback via Google Apps Script |
| 📱 **PWA (Installable)** | Install URLz on your phone or desktop and use it like a native app |
| 🌌 **Animated Background** | Immersive Vanta.js animated birds background with a deep-space theme |
| 🔒 **DevTools Protection** | Right-click and developer shortcut keys are disabled in production |

---

## Tech Stack

```
Frontend         →  HTML5 · CSS3 · Vanilla JavaScript · Poppins (Google Fonts)
Animated BG      →  Vanta.js (Birds) · Three.js
Backend          →  Google Apps Script (serverless proxy)
Link Storage     →  Google Sheets (via Apps Script)
Contact Form     →  Google Apps Script Web App
Deployment       →  GitHub Pages
PWA              →  Service Worker · Web App Manifest
SEO              →  Schema.org JSON-LD · Open Graph · Sitemap · Robots.txt
```

---

## Project Structure

```
custom_url/
│
├── index.html                      # Main app — URL shortener interface
├── admin.html                      # Admin login panel
├── search.html                     # Search existing short links
├── 404.html                        # Custom 404 error page
├── links.json                      # Local link map (slug → destination)
│
├── manifest.json                   # PWA manifest configuration
├── sw.js                           # Service Worker for offline support
├── robots.txt                      # SEO robots configuration
├── sitemap.xml                     # XML sitemap for search engines
│
├── src/
│   └── img/
│       ├── myurllogo.png           # App logo
│       └── loading.gif             # Loading animation
│
├── myurllogo.png                   # Root-level logo (for PWA manifest)
├── loading.gif                     # Root-level loading GIF
│
└── .github/
    └── workflows/
        └── static.yml              # GitHub Pages auto-deployment workflow
```

---

## Setup and Deployment

### Prerequisites

- A Google account (for the Apps Script backend)
- A custom domain (optional — defaults to GitHub Pages URL)
- A GitHub repository with GitHub Pages enabled

### 1. Clone the Repository

```bash
git clone https://github.com/manikandan-n-07/custom_url.git
cd custom_url
```

### 2. Configure the Google Apps Script Backend

URLz uses **two** Google Apps Script deployments as a serverless backend:

| Variable | File | Purpose |
|---|---|---|
| `APPS_SCRIPT_URL` | `index.html` | Handles slug availability checks & link creation (writes to Google Sheets) |
| `CONTACT_SCRIPT_URL` | `index.html` | Receives and logs contact form submissions |

Steps to set up:
1. Open [script.google.com](https://script.google.com) and create your Apps Script projects.
2. Write your script to handle `checkSlug` and `createLink` actions backed by Google Sheets.
3. Deploy each project as a **Web App** (Execute as: Me, Access: Anyone).
4. Copy the deployed Web App URLs into `index.html`:

```javascript
const APPS_SCRIPT_URL    = 'YOUR_APPS_SCRIPT_WEB_APP_URL_HERE';
const CONTACT_SCRIPT_URL = 'YOUR_CONTACT_SCRIPT_URL_HERE';
```

### 3. Set Your Custom Domain

Update the base domain in `index.html`:

```javascript
const CUSTOM_DOMAIN_BASE = 'https://your-domain.com/';
```

Also update all `meta`, `og:url`, `canonical`, and `schema.org` references in `index.html` to match your domain.

### 4. Deploy to GitHub Pages

Push to your repository. The included `.github/workflows/static.yml` workflow automatically deploys to GitHub Pages on every push to `main`.

```bash
git add .
git commit -m "Initial deployment"
git push origin main
```

Your app will be live at:
```
https://your-username.github.io/custom_url
```

Or at your custom domain if configured in GitHub Pages settings.

---

## How to Use

**Creating a Short Link:**

1. Open the app and navigate to the **Create Link** section.
2. Enter the **Destination URL** — the long link you want to shorten.
3. Type your **Custom Short URL (Link ID)** — e.g., `event-signup` or `portfolio/2025`.
4. Optionally add your **email** for link management notifications.
5. The app checks slug availability in real-time as you type.
6. Click **Create & Deploy Short Link**.
7. Watch the animated loading sequence, then get your ready-to-share short link.
8. A **30-second countdown** shows when the link goes fully live on the server.
9. Click **Copy** to copy the short URL to your clipboard instantly.

**Allowed characters in Link IDs:** `a-z`, `0-9`, `-` (dash), `_` (underscore), `/` (forward slash). Minimum 3 characters.

---

## Configuration

| Setting | Location | Description |
|---|---|---|
| `APPS_SCRIPT_URL` | `index.html` | Google Apps Script URL for link creation & slug checks |
| `CONTACT_SCRIPT_URL` | `index.html` | Google Apps Script URL for contact form submissions |
| `CUSTOM_DOMAIN_BASE` | `index.html` | Your custom domain base (e.g., `https://urlz.site/`) |
| Admin credentials | `admin.html` | Update the admin login logic in the admin panel script |
| Link map | `links.json` | Static JSON file mapping slugs to destination URLs (for reference/fallback) |
| PWA name | `manifest.json` | App name, short name, theme color, and icon paths |

---

## Pages Overview

| Page | File | Description |
|---|---|---|
| **Home / Shortener** | `index.html` | Main interface for creating custom short links |
| **Search** | `search.html` | Look up existing short links by slug or keyword |
| **Admin** | `admin.html` | Password-protected panel for managing stored links |
| **404** | `404.html` | Custom error page shown for unknown or invalid slugs |

---

## Security Notes

- The Apps Script backend handles all link creation and storage — no sensitive credentials are exposed in the frontend.
- DevTools access is restricted in production: right-click, F12, Ctrl+Shift+I/J/C, and Ctrl+U are all disabled to protect the source.
- Drag-and-drop is also disabled to prevent source snooping.
- For the admin panel, use robust server-side authentication for production deployments rather than client-side password checks.
- Consider adding a `.gitignore` to keep local config files out of version control:

```gitignore
.env
*.local
```

---

## Contributing

Contributions are welcome! Here's how to get started:

```bash
# 1. Fork the repository
# 2. Create a feature branch
git checkout -b feature/your-feature-name

# 3. Commit your changes
git commit -m "Add: your feature description"

# 4. Push and open a Pull Request
git push origin feature/your-feature-name
```

Ideas for contribution: dark/light mode toggle, link expiry dates, click analytics dashboard, QR code generation for each short link, bulk link import from CSV.

---

## Author

<div align="center">

# Manikandan N

*Full Stack Developer & Creator of Custom URLs*

[![GitHub](https://img.shields.io/badge/GitHub-@manikandan--n--07-181717?style=flat-square&logo=github)](https://github.com/manikandan-n-07)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Manikandan_N-0077B5?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/manikandan-n-35a1bb294)
[![Email](https://img.shields.io/badge/Email-manilunar07@gmail.com-D14836?style=flat-square&logo=gmail)](mailto:manilunar07@gmail.com)

</div>

---

