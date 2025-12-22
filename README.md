# Short-url
# 🌐 Custom Link – URL Shortener & Redirect Service

**Custom Link** is a sleek, modern web-based URL shortener built with HTML, CSS, and JavaScript.  
It allows users to create **custom short URLs** with memorable slugs (custom IDs), track generated links, and seamlessly redirect visitors to the original destination.  
The system integrates with **Google Apps Script** as a lightweight backend for deployment, storage, and link validation.

---

## 📋 Table of Contents

1. [Introduction](#introduction)  
2. [Live Demo](#live-demo)  
3. [Features](#features)  
4. [Project Structure](#project-structure)  
5. [Installation & Setup](#installation--setup)  
6. [Usage Guide](#usage-guide)  
7. [Dependencies](#dependencies)  
8. [Configuration](#configuration)  
9. [How Redirection Works](#how-redirection-works)  
10. [Contact & Support](#contact--support)

---

## 🧩 Introduction

**Custom Link** enables anyone to generate custom short URLs under their own domain — for example:

```
https://urlz.site/event-register
```

This helps make links more readable and shareable while maintaining control over your brand or domain.

The tool includes a **responsive modern UI**, real-time **slug validation**, a **history tracker**, and animated visual effects using **Vanta.js**.  
It is completely front-end driven, making it deployable on **GitHub Pages** or any static hosting service.

---

## 🚀 Live Demo

👉 [Try it here](https://custom-longurl.github.io/short-url/) *(Replace with your live link if hosted)*

---

## ✨ Features

- ✅ **Custom Short Link Creation** – Generate your own URL slugs (IDs).  
- ⚙️ **Backend Integration** – Connects with Google Apps Script for link deployment and storage.  
- 🔍 **Real-Time Validation** – Checks slug availability before creation.  
- 📜 **Link History Tracker** – View and copy your previously generated links.  
- 💫 **Interactive Background** – Dynamic Vanta.js Birds animation.  
- 📧 **Contact Form** – Built-in message form that integrates with a Google Apps Script endpoint.  
- 🧠 **Smart Error Handling** – Displays live validation, progress, and success animations.  
- 🌗 **Modern UI** – Space-themed, dark mode aesthetic built with pure CSS.  

---

## 🗂️ Project Structure

```
.
├── index.html          # Main web interface for creating custom links
├── 404.html            # Dynamic redirect handler for shortened links
├── myurllogo.png       # Project logo/favicon
├── loading.gif         # (Optional) Used for loading animations
└── links.json          # Auto-generated JSON file for link mapping (handled by Google Apps Script)
```

---

## ⚙️ Installation & Setup

You can deploy **Custom Link** easily on **GitHub Pages** or any static host.

### 1. Clone or Download
```bash
git clone https://github.com/yourusername/short-url.git
cd short-url
```

### 2. Update Configuration
In `index.html`, locate these constants near the top of the `<script>` section:

```js
const APPS_SCRIPT_URL = 'YOUR_GOOGLE_SCRIPT_DEPLOYMENT_URL';
const CUSTOM_DOMAIN_BASE = 'https://yourdomain.com/';
const CONTACT_SCRIPT_URL = 'YOUR_CONTACT_FORM_SCRIPT_URL';
```

Replace them with your actual Google Apps Script deployment URLs and your domain name.

### 3. Deploy on GitHub Pages
1. Push the project to your GitHub repository.  
2. Go to **Settings → Pages → Branch → main → /root**.  
3. Your app will be live at `https://yourusername.github.io/short-url/`.

---

## 💡 Usage Guide

1. **Enter a long URL** — The destination link to shorten.  
2. **Choose a custom short ID** (slug) — Only letters, numbers, `-`, `_`, `/` allowed.  
3. *(Optional)* **Add your email** for management or notifications.  
4. Click **Create & Deploy Short Link**.  
5. Wait ~30 seconds for the link to activate.  
6. Your link appears under **History**, and you can copy it instantly.

---

## 🧱 Dependencies

| Library | Purpose |
|----------|----------|
| [Three.js](https://threejs.org/) | 3D rendering required by Vanta.js |
| [Vanta.js Birds Effect](https://github.com/tengbao/vanta) | Animated particle background |
| [Google Apps Script](https://developers.google.com/apps-script) | Backend for link creation and contact forms |
| Pure HTML, CSS, JS | Front-end logic and design |

---

## 🛠️ Configuration

**index.html:**
- Customize theme colors in the `:root` CSS variables section.  
- Modify `CUSTOM_DOMAIN_BASE` to point to your own domain.  
- Update schema.org metadata for SEO (website title, description, etc.).  

**404.html:**
- Handles all redirects automatically.
- Fetches `links.json` dynamically to resolve custom short links.

---

## 🔁 How Redirection Works

1. When someone visits a short link like  
   ```
   https://urlz.site/my-product
   ```
2. The `404.html` script captures the path (`/my-product`).
3. It fetches a live JSON file (`links.json`) maintained by Google Apps Script.
4. If found, the user is redirected instantly to the corresponding long URL.
5. If not, a friendly error message appears with a link to return to the main page.

---

## 💬 Contact & Support

Built by **Manikandan N**.  
📧 **Email:** [manilunar07@gmail.com](mailto:manilunar07@gmail.com)  

For questions or support, use the built-in **Contact Form** on the site.
