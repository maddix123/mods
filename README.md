# AddonHub (Minecraft Add-ons Directory Clone)

A modern static website inspired by **mc-addons.com**.

This project is pure static (HTML/CSS), so it is very easy to host on aaPanel.

---

## Quick local preview

```bash
python3 -m http.server 8000
```

Then open: `http://localhost:8000`

---

# aaPanel Hosting Guide (Clear Step-by-Step)

If you are hosting with **aaPanel**, follow these exact steps in order.

## Before you start

You need:

- aaPanel installed on your VPS
- Your server public IP
- A domain name (recommended)
- Access to your DNS provider (Cloudflare, Namecheap, GoDaddy, etc.)

---

## Step 1) Point domain to your server

In your DNS panel, add these records:

1. Root domain record
   - Type: `A`
   - Host/Name: `@`
   - Value: `YOUR_SERVER_IP`
2. Optional www record
   - Type: `A`
   - Host/Name: `www`
   - Value: `YOUR_SERVER_IP`

> If you use Cloudflare, start with **DNS only** (gray cloud) until SSL works.

Wait a few minutes for propagation.

---

## Step 2) Open aaPanel

1. Visit your aaPanel URL, usually:
   - `http://YOUR_SERVER_IP:7800`
2. Log in.
3. Install suggested packages if prompted.

---

## Step 3) Install required app

In aaPanel **App Store**, install:

- **Nginx** ✅ required

Optional (not required for this static site):

- PHP
- Pure-Ftpd

---

## Step 4) Create your website in aaPanel

1. Go to **Website** → **Add site**.
2. Domain: `example.com` (replace with your real domain).
3. Root directory: keep default or set to:
   - `/www/wwwroot/example.com`
4. PHP version: choose **Static**.
5. Submit.

---

## Step 5) Upload website files

Upload `index.html` into your site root.

Target path example:

```text
/www/wwwroot/example.com/index.html
```

Upload options:

- aaPanel File manager
- SFTP/FTP
- Git pull on server

---

## Step 6) Confirm Nginx settings

In **Website** list → your domain → **Settings**:

- Root path is correct (`/www/wwwroot/example.com`)
- Index includes `index.html`

Nginx index line should contain:

```nginx
index index.html index.htm index.php;
```

---

## Step 7) Enable SSL (HTTPS)

1. Website **Settings** → **SSL**.
2. Select **Let's Encrypt**.
3. Select your domain (`example.com`, optionally `www.example.com`).
4. Click **Apply**.
5. Turn on **Force HTTPS**.

---

## Step 8) Open firewall/security ports

Make sure these ports are open:

- `80` (HTTP)
- `443` (HTTPS)
- `7800` (aaPanel login panel, optional but common)

You may need to open ports in:

- aaPanel security settings
- Cloud VPS firewall/security group (AWS/Lightsail/DO/etc.)

---

## Step 9) Test website

Check in browser:

- `http://example.com`
- `https://example.com`

If site is not loading:

1. Verify DNS A record points to correct IP.
2. Verify `index.html` exists in the root folder.
3. Verify Nginx is running in aaPanel.
4. Verify ports 80/443 are open.
5. Retry after DNS propagation delay.

---

## Step 10) How to update site later

When you edit the site:

1. Replace `/www/wwwroot/example.com/index.html`
2. Hard refresh browser (`Ctrl + F5`)
3. If still old, clear CDN/browser cache

---

## Minimal file structure

```text
.
├── index.html
└── README.md
```

---

## License

Free for personal and commercial use.
