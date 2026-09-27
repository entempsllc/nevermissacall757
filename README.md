# Never Miss A Call 757 — deploy

Live URL: https://nevermissacall757.com

## 1. Edit the 8 values
Open `index.html`, find `const CONFIG` near the bottom, and set:
bookingLink, paymentLink, phone, email, setupFee, foundingPrice, spotsLeft, guaranteeDays.

- Booking link: free Calendly (15-min event) or a Google Calendar appointment page.
- Payment link: Stripe → Payment Links → one-time product "Setup fee".

## 2. Push to GitHub (Git Bash)
Create an empty repo `nevermissacall757` on the entempsllc GitHub account first, then:
```bash
cd ~/OneDrive/Desktop/local-growth-stack
git init
git add .
git commit -m "Never Miss A Call 757 site"
git branch -M main
git remote add origin https://github.com/entempsllc/nevermissacall757.git
git push -u origin main
```
Repo → Settings → Pages → Source: Deploy from branch → `main` / root → Save.
The `CNAME` file already sets the custom domain.

## 3. Namecheap DNS
Domain List → nevermissacall757.com → Manage → Advanced DNS. Delete the default parking records, then add:

| Type | Host | Value |
| --- | --- | --- |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | entempsllc.github.io. |

## 4. Verify
```bash
nslookup nevermissacall757.com
```
Should return the four 185.199.x.153 IPs (can take 10 min–a few hours).

Then GitHub → Settings → Pages: once the DNS check passes, tick **Enforce HTTPS**.

On your phone:
- https://nevermissacall757.com loads
- "Free audit" opens your booking page
- "Claim a founding spot" opens Stripe checkout
- Tapping the phone number opens the dialer
