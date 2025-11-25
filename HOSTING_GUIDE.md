# German Flashcard App - Hosting Guide

## 🌐 Complete Hosting Solutions

This guide covers **3 hosting options** from easiest to most advanced:

1. **GitHub Pages** (FREE, Easiest, 5 minutes setup)
2. **Home Router + WireGuard VPN** (FREE, Moderate complexity)
3. **Cloud Hosting** (FREE or $3-5/month, Easy)

---

## 📋 Table of Contents

- [Option 1: GitHub Pages (RECOMMENDED)](#option-1-github-pages-recommended)
- [Option 2: Home Router + WireGuard VPN](#option-2-home-router--wireguard-vpn)
- [Option 3: Other Cloud Hosting](#option-3-other-cloud-hosting-options)
- [Domain Setup](#domain-setup)
- [Security Best Practices](#security-best-practices)

---

## Option 1: GitHub Pages (RECOMMENDED)

### ✅ Why GitHub Pages?

- **100% FREE** - No cost ever
- **HTTPS included** - Automatic SSL certificate
- **Easy setup** - 5 minutes
- **Reliable** - 99.9% uptime
- **Custom domain support** - Free
- **No server management** - GitHub handles everything
- **Perfect for static sites** - Your flashcard app is HTML/CSS/JS only

### 🚀 Step-by-Step Setup

#### Step 1: Prepare Your Repository

Your flashcard app is already in GitHub! We just need to enable Pages.

#### Step 2: Enable GitHub Pages

**Option A: Via GitHub Website**

1. Go to your repository:
   - Personal: `https://github.com/{username}/Telekom-Projects`
   - Telekom: `https://github.com/{username}ghi-oss/Telekom-Projects`

2. Click **Settings** tab

3. Scroll to **Pages** (left sidebar under "Code and automation")

4. Under **Source**, select:
   - Branch: `master`
   - Folder: `/ (root)`
   - Click **Save**

5. Wait 1-2 minutes

6. Your site will be live at:
   ```
   https://{username}.github.io/Telekom-Projects/German-Flashcard-App/flashcard.html
   ```

**Option B: Using Command Line**

```bash
# Your repository is already set up, just enable Pages
# Visit the GitHub website and follow Option A above
# (Pages cannot be enabled via command line)
```

#### Step 3: Access Your App

Your flashcard app is now live at:

```
https://YOUR-USERNAME.github.io/Telekom-Projects/German-Flashcard-App/flashcard.html
```

**Bookmark this URL** and access it from anywhere!

### 🌐 Add Custom Domain (Optional)

If you want your own domain like `flashcards.yourdomain.com`:

#### Get a Domain

**Free Options:**
- **Freenom** - Free domains (.tk, .ml, .ga, .cf, .gq)
- **DuckDNS** - Free subdomain (e.g., yourname.duckdns.org)
- **Afraid.org** - Free DNS service

**Paid Options (Recommended):**
- **Namecheap** - $8-12/year (.com, .net)
- **Google Domains** - $12/year
- **Cloudflare Registrar** - $8-10/year (at-cost pricing)

#### Configure Custom Domain

1. **In Your Domain Provider:**

   Add a CNAME record:
   ```
   Type: CNAME
   Name: flashcards (or @ for root domain)
   Target: {username}.github.io
   TTL: 3600
   ```

2. **In GitHub Repository Settings → Pages:**

   - Enter your custom domain: `flashcards.yourdomain.com`
   - Check "Enforce HTTPS" (wait 10 minutes after DNS setup)

3. **Wait 5-30 minutes** for DNS propagation

4. **Access your site:**
   ```
   https://flashcards.yourdomain.com/German-Flashcard-App/flashcard.html
   ```

### 📱 Create Shortened URL

Make it easier to access:

1. **Create an index redirect:**

```bash
# Create a simple index.html in the root
cat > index.html << 'EOF'
<!DOCTYPE html>
<html>
<head>
    <meta http-equiv="refresh" content="0; url=German-Flashcard-App/flashcard.html">
    <title>Redirecting to Flashcard App...</title>
</head>
<body>
    <p>Redirecting to Flashcard App... <a href="German-Flashcard-App/flashcard.html">Click here if not redirected</a></p>
</body>
</html>
EOF

git add index.html
git commit -m "Add redirect to flashcard app"
git push origin master
git push telekom master
```

Now access via: `https://{username}.github.io/Telekom-Projects/`

---

## Option 2: Home Router + WireGuard VPN

### 📍 Why This Option?

- **Private access only** - Not public
- **Use home internet** - No hosting costs
- **Full control** - Your hardware
- **Learning opportunity** - Network skills

### ⚠️ Requirements

- **Home router with WireGuard support** OR
- **Raspberry Pi / PC running 24/7**
- **Static public IP** OR **Dynamic DNS service**
- **Port forwarding capability** on router
- **Basic Linux knowledge**

### 🔧 Setup Process

#### Part 1: Set Up Web Server on Home Network

**Option A: Using Existing PC/Laptop**

1. **Install a simple web server:**

   **On Windows:**
   ```cmd
   # Download and install Python (already have it)
   # Navigate to your project folder
   cd "C:\path\to\your\project"

   # Start simple web server
   python -m http.server 8080
   ```

   **On Linux:**
   ```bash
   # Navigate to project folder
   cd /path/to/German-Flashcard-App

   # Start web server
   python3 -m http.server 8080
   ```

2. **Find your local IP:**
   ```cmd
   ipconfig  # On Windows
   ifconfig  # On Linux/Mac
   ```

   Example: `192.168.1.100`

3. **Test locally:**
   ```
   http://192.168.1.100:8080/flashcard.html
   ```

**Option B: Using Raspberry Pi (Recommended for 24/7)**

1. **Install Nginx:**
   ```bash
   sudo apt update
   sudo apt install nginx
   ```

2. **Copy files to web directory:**
   ```bash
   sudo cp -r German-Flashcard-App /var/www/html/
   ```

3. **Start Nginx:**
   ```bash
   sudo systemctl start nginx
   sudo systemctl enable nginx
   ```

4. **Test locally:**
   ```
   http://RASPBERRY_PI_IP/German-Flashcard-App/flashcard.html
   ```

#### Part 2: Set Up WireGuard VPN

**On Your Home Server (Raspberry Pi or PC):**

1. **Install WireGuard:**

   **Ubuntu/Debian:**
   ```bash
   sudo apt update
   sudo apt install wireguard
   ```

   **Windows:**
   Download from: https://www.wireguard.com/install/

2. **Generate server keys:**
   ```bash
   wg genkey | tee server_private.key | wg pubkey > server_public.key
   ```

3. **Create WireGuard config:**
   ```bash
   sudo nano /etc/wireguard/wg0.conf
   ```

   Add this configuration:
   ```ini
   [Interface]
   Address = 10.0.0.1/24
   ListenPort = 51820
   PrivateKey = YOUR_SERVER_PRIVATE_KEY

   # Enable IP forwarding
   PostUp = iptables -A FORWARD -i wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
   PostDown = iptables -D FORWARD -i wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE

   [Peer]
   # This will be your phone/laptop
   PublicKey = CLIENT_PUBLIC_KEY
   AllowedIPs = 10.0.0.2/32
   ```

4. **Enable IP forwarding:**
   ```bash
   sudo sysctl -w net.ipv4.ip_forward=1
   echo "net.ipv4.ip_forward=1" | sudo tee -a /etc/sysctl.conf
   ```

5. **Start WireGuard:**
   ```bash
   sudo wg-quick up wg0
   sudo systemctl enable wg-quick@wg0
   ```

**On Your Client Device (Phone/Laptop):**

1. **Install WireGuard client:**
   - **Android:** Play Store → WireGuard
   - **iOS:** App Store → WireGuard
   - **Windows/Mac/Linux:** https://www.wireguard.com/install/

2. **Generate client keys:**
   ```bash
   wg genkey | tee client_private.key | wg pubkey > client_public.key
   ```

3. **Create client config:**
   ```ini
   [Interface]
   PrivateKey = YOUR_CLIENT_PRIVATE_KEY
   Address = 10.0.0.2/24
   DNS = 8.8.8.8

   [Peer]
   PublicKey = YOUR_SERVER_PUBLIC_KEY
   Endpoint = YOUR_PUBLIC_IP:51820
   AllowedIPs = 10.0.0.0/24
   PersistentKeepalive = 25
   ```

4. **Import config** into WireGuard app

#### Part 3: Configure Router Port Forwarding

1. **Access your router** (usually `192.168.1.1` or `192.168.0.1`)

2. **Find Port Forwarding section** (varies by router)

3. **Add port forwarding rule:**
   ```
   External Port: 51820
   Internal IP: YOUR_SERVER_LOCAL_IP (e.g., 192.168.1.100)
   Internal Port: 51820
   Protocol: UDP
   ```

4. **Save and reboot router**

#### Part 4: Get Your Public IP

**Option A: Static IP (Check with ISP)**
```bash
curl ifconfig.me
```

**Option B: Dynamic DNS (Recommended)**

Free services:
- **DuckDNS** - https://www.duckdns.org
- **No-IP** - https://www.noip.com
- **FreeDNS** - https://freedns.afraid.org

**DuckDNS Setup Example:**

1. Create account at https://www.duckdns.org
2. Create subdomain: `yourname.duckdns.org`
3. Install DuckDNS updater:

   ```bash
   # Create update script
   echo url="https://www.duckdns.org/update?domains=yourname&token=YOUR_TOKEN&ip=" | curl -k -o ~/duckdns/duck.log -K -

   # Add to crontab (runs every 5 minutes)
   crontab -e
   */5 * * * * ~/duckdns/duck.sh >/dev/null 2>&1
   ```

4. Use `yourname.duckdns.org:51820` in WireGuard client config

### 🔒 Security Considerations

1. **Change default ports** (use something other than 51820)
2. **Use strong keys** (WireGuard generates these automatically)
3. **Limit AllowedIPs** to only what's needed
4. **Enable firewall:**
   ```bash
   sudo ufw allow 51820/udp
   sudo ufw enable
   ```
5. **Regular updates:**
   ```bash
   sudo apt update && sudo apt upgrade
   ```

### 📱 Accessing Your App via VPN

1. **Connect to WireGuard** on your device
2. **Open browser** and navigate to:
   ```
   http://10.0.0.1:8080/flashcard.html
   ```
   (Or the internal IP of your server)

---

## Option 3: Other Cloud Hosting Options

### Free Options

#### A. Netlify (Easiest)

1. **Sign up:** https://www.netlify.com (free account)

2. **Deploy via drag-and-drop:**
   - Drag your `German-Flashcard-App` folder to Netlify
   - Get instant URL: `yourapp.netlify.app`

3. **Or deploy from GitHub:**
   ```bash
   # Install Netlify CLI
   npm install -g netlify-cli

   # Deploy
   cd German-Flashcard-App
   netlify deploy
   ```

4. **Custom domain:** Add for free in Netlify settings

**Features:**
- Unlimited bandwidth
- Automatic HTTPS
- Custom domains free
- Easy to update

#### B. Vercel

1. **Sign up:** https://vercel.com (free account)

2. **Deploy:**
   ```bash
   # Install Vercel CLI
   npm install -g vercel

   # Deploy
   cd German-Flashcard-App
   vercel
   ```

3. **Get URL:** `yourapp.vercel.app`

#### C. Cloudflare Pages

1. **Sign up:** https://pages.cloudflare.com

2. **Connect GitHub repository**

3. **Configure:**
   - Build command: (leave empty)
   - Output directory: `German-Flashcard-App`

4. **Deploy automatically** on every push

**Features:**
- Unlimited bandwidth
- Fast global CDN
- Free SSL
- Custom domains

#### D. Firebase Hosting

1. **Install Firebase CLI:**
   ```bash
   npm install -g firebase-tools
   ```

2. **Login:**
   ```bash
   firebase login
   ```

3. **Initialize:**
   ```bash
   cd German-Flashcard-App
   firebase init hosting
   ```

4. **Deploy:**
   ```bash
   firebase deploy
   ```

5. **Get URL:** `yourapp.web.app`

### Cheap Paid Options ($3-5/month)

#### A. DigitalOcean Droplet

- **$4/month** for basic VPS
- **Full control** over server
- **1TB bandwidth**
- **SSH access**

#### B. Linode

- **$5/month** for Nanode
- Similar to DigitalOcean
- Great documentation

#### C. Vultr

- **$3.50/month** for smallest instance
- Global locations

---

## Domain Setup

### Free Domain Options

#### 1. DuckDNS (Subdomain)

1. Visit https://www.duckdns.org
2. Sign in with GitHub/Google
3. Create subdomain: `yourname.duckdns.org`
4. Point to your IP
5. **FREE forever**

#### 2. Freenom (Full Domain)

1. Visit https://www.freenom.com
2. Search for available domain
3. Get FREE domain (.tk, .ml, .ga, .cf, .gq)
4. Configure DNS
5. **Free for 12 months** (renewable)

### Paid Domain Options (Recommended)

| Provider | Price/Year | Features |
|----------|------------|----------|
| Namecheap | $8-12 | Easy management, free WhoisGuard |
| Google Domains | $12 | Simple interface, Google integration |
| Cloudflare | $8-10 | At-cost pricing, fast DNS |
| Porkbun | $9-11 | Cheap, includes SSL |

### Domain Configuration

**For GitHub Pages:**
```
Type: CNAME
Name: www (or @)
Value: yourusername.github.io
```

**For Custom Server:**
```
Type: A
Name: @ (root domain)
Value: YOUR_SERVER_IP
```

**For WireGuard VPN:**
```
Type: A
Name: vpn
Value: YOUR_HOME_PUBLIC_IP
```

---

## Security Best Practices

### For Public Hosting (GitHub Pages, Netlify, etc.)

1. **Use HTTPS only** (enabled by default)
2. **No sensitive data** in the app (it's client-side)
3. **Regular updates** to your code
4. **Monitor access** via analytics if needed

### For Home Hosting + VPN

1. **Strong WireGuard keys** (automatically generated)
2. **Change default ports**
3. **Firewall rules:**
   ```bash
   sudo ufw default deny incoming
   sudo ufw default allow outgoing
   sudo ufw allow 51820/udp
   sudo ufw enable
   ```
4. **Regular system updates:**
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
5. **Fail2ban** (optional, for additional security):
   ```bash
   sudo apt install fail2ban
   ```
6. **Disable unnecessary services**
7. **Use non-root user** for running services
8. **Backup configurations** regularly

### General Security

1. **No passwords in code** (your app doesn't need any)
2. **Keep local storage private** (already handled by browser)
3. **Regular backups** of your vocabulary files
4. **Monitor logs** (if self-hosting)

---

## Comparison Table

| Feature | GitHub Pages | Home + VPN | Cloud Hosting |
|---------|--------------|------------|---------------|
| **Cost** | FREE | FREE | FREE or $3-5/mo |
| **Setup Time** | 5 minutes | 2-3 hours | 10 minutes |
| **Difficulty** | Easy | Advanced | Easy |
| **Maintenance** | None | Regular | Minimal |
| **Uptime** | 99.9% | Depends on you | 99.9% |
| **Speed** | Fast (CDN) | Depends on ISP | Fast (CDN) |
| **Privacy** | Public | Private | Public |
| **Custom Domain** | Yes (free) | Yes (need DNS) | Yes (free) |
| **HTTPS** | Automatic | Manual setup | Automatic |
| **Skills Needed** | Git basics | Networking, Linux | Git basics |

---

## Recommended Solution

### For Most Users: **GitHub Pages**

**Why?**
- Already using GitHub
- Zero cost
- Zero maintenance
- Professional hosting
- Fast global CDN
- Automatic HTTPS

**Setup:**
1. Enable GitHub Pages (5 minutes)
2. Done!

**URL:**
```
https://{username}.github.io/Telekom-Projects/German-Flashcard-App/flashcard.html
```

### For Private Access: **Home + WireGuard VPN**

**Why?**
- Keep data private
- Learn networking skills
- No ongoing costs

**Best for:**
- Learning purposes
- Complete privacy
- Technical users

---

## Quick Start Commands

### Enable GitHub Pages NOW:

```bash
# Your repository is already on GitHub
# Just enable Pages via GitHub website:
# Settings → Pages → Source: master branch → Save
# Wait 2 minutes, then visit:
# https://{username}.github.io/Telekom-Projects/German-Flashcard-App/flashcard.html
```

### Test Locally First:

```bash
# Navigate to your app
cd "C:\path\to\your\project\German-Flashcard-App"

# Start local server
python -m http.server 8080

# Open browser:
# http://localhost:8080/flashcard.html
```

---

## Troubleshooting

### GitHub Pages not working?

- Check Settings → Pages is enabled
- Wait 2-3 minutes for deployment
- Clear browser cache (Ctrl+Shift+Delete)
- Try incognito/private mode

### WireGuard not connecting?

- Check port forwarding is correct
- Verify firewall allows UDP port
- Confirm public IP is correct
- Check WireGuard is running: `sudo wg show`

### Domain not working?

- Wait 24-48 hours for DNS propagation
- Check DNS configuration: `nslookup yourdomain.com`
- Verify CNAME/A record is correct
- Try different DNS server (8.8.8.8)

---

## Next Steps

1. **Choose your hosting option** (recommend GitHub Pages)
2. **Follow the setup guide** for your chosen option
3. **Test access** from different devices
4. **Bookmark the URL** for easy access
5. **(Optional) Set up custom domain**

---

## Support & Resources

### GitHub Pages
- Docs: https://docs.github.com/pages
- Status: https://www.githubstatus.com

### WireGuard
- Official site: https://www.wireguard.com
- Setup guide: https://www.wireguard.com/quickstart
- Community: r/WireGuard

### Domain Registrars
- Namecheap: https://www.namecheap.com
- DuckDNS: https://www.duckdns.org
- Freenom: https://www.freenom.com

---

**Need Help?** Open an issue on GitHub or refer to the specific hosting provider's documentation.

**Happy Hosting! 🚀**
