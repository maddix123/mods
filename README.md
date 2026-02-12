# AddonHub (Minecraft Add-ons Directory Clone)

A simple, modern static website inspired by platforms like **mc-addons.com**.

This project is intentionally lightweight so anyone can host it without backend setup.

---

## What you get

- Responsive homepage with:
  - Hero section
  - Featured add-on cards
  - Category/search/sort UI elements
  - Community/highlights panels
- Pure HTML + CSS (single `index.html`)
- Easy deployment to static hosts

---

## Quick start (run locally)

1. Open a terminal in this project folder.
2. Run a local server:

```bash
python3 -m http.server 8000
```

3. Open your browser at:

```text
http://localhost:8000
```

---

## Easy hosting guide (step-by-step)

Choose any method below.

## Option 1: GitHub Pages (free, beginner-friendly)

1. Create a new GitHub repository.
2. Upload `index.html` (and `README.md`) to the repository root.
3. Go to **Settings → Pages**.
4. Under **Build and deployment**:
   - Source: **Deploy from a branch**
   - Branch: **main**
   - Folder: **/ (root)**
5. Click **Save**.
6. Wait 1–2 minutes.
7. Open your live site URL:
   - `https://YOUR_USERNAME.github.io/YOUR_REPO_NAME/`

## Option 2: Netlify (drag-and-drop deploy)

1. Go to [https://app.netlify.com/drop](https://app.netlify.com/drop).
2. Drag your project folder (or just `index.html`) into the drop zone.
3. Netlify instantly publishes your site.
4. (Optional) Click **Site settings** to:
   - Set a custom site name
   - Connect a custom domain

## Option 3: Vercel (git-based deploy)

1. Push this project to GitHub/GitLab/Bitbucket.
2. Go to [https://vercel.com/new](https://vercel.com/new).
3. Import your repository.
4. Framework preset: **Other** (or leave auto-detected).
5. Build command: leave empty.
6. Output directory: leave empty.
7. Click **Deploy**.

## Option 4: Your own VPS (Ubuntu + Nginx)

1. SSH into your server.
2. Install Nginx:

```bash
sudo apt update
sudo apt install -y nginx
```

3. Copy your files to web root:

```bash
sudo mkdir -p /var/www/addonhub
sudo cp index.html /var/www/addonhub/
```

4. Create Nginx site config:

```bash
sudo nano /etc/nginx/sites-available/addonhub
```

5. Paste:

```nginx
server {
    listen 80;
    server_name YOUR_DOMAIN_OR_IP;

    root /var/www/addonhub;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

6. Enable config and reload Nginx:

```bash
sudo ln -s /etc/nginx/sites-available/addonhub /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx
```

7. Visit `http://YOUR_DOMAIN_OR_IP`.

---

## Customization tips

- Replace placeholder add-on cards with your real content.
- Add pages like `addons.html`, `submit.html`, and `about.html`.
- Add analytics (Plausible/GA) if you want traffic insights.
- Add a backend later only if you need uploads/accounts.

---

## File structure

```text
.
├── index.html
└── README.md
```

---

## License

Use freely for personal or commercial projects.
