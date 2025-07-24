# 8-bit Obscura

A Hugo-powered archive of obscure 8-bit games, bootlegs, and mostly Taiwan related video game articles.

Built with [Hugo](https://gohugo.io/) and the [Blowfish](https://github.com/nunocoracao/blowfish) theme.


## Getting Started

### 1. Clone the repo (with theme)

```bash
git clone --recurse-submodules https://github.com/daveflynn/8bitobscura.com.git
cd 8bitobscura.com
```

If you already cloned it without submodules:

```bash
git submodule update --init --recursive
```

---

## Build the Site

You’ll need [Hugo Extended](https://github.com/gohugoio/hugo/releases) installed.

```bash
hugo
```

The site will be generated in the `public/` directory.

---

## Manual Deployment

1. SSH into the server:

```bash
ssh user@ip
cd /opt/8bitobscura.com
```

2. Pull the latest changes:

```bash
git pull
git submodule update --init --recursive
```

3. Build the site:

```bash
hugo
```

4. Deploy the output:

```bash
sudo rsync -avz --delete public/ /var/www/8bitobscura.com/html/
sudo chown -R www-data:www-data /var/www/8bitobscura.com/html/
```

5. (Optional) Reload Nginx:

```bash
sudo systemctl reload nginx
```

---

## 🔐 License

All content © 2025 Dave Flynn. All rights reserved.
