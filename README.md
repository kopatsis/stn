# Shorten Track

**Shorten Track** is a high-performance, full-featured URL shortener designed for speed, usability, and scalability. Users can instantly generate clean, short links in the format `https://shk.fm/xY_z1` and access powerful analytics and management tools. Built with a modern stack and designed to scale to billions of links.

**Live site:** [https://shortentrack.com](https://shortentrack.com)  
**Shortened links domain:** [https://shk.fm](https://shk.fm)

---

## 🔗 How It Works

Users can input any URL (up to 2048 characters), and Shorten Track returns a shortened version that is 9–12 characters long, including the domain. The unique ID at the end is 2–5 characters long and is generated using a custom Base64-like alphabet of 64 characters:

- `a-z`, `A-Z`, `0-9`, `-`, `_`

This allows for over 1 billion unique IDs with 5 characters. When usage approaches that limit, the system seamlessly supports 6-character IDs for further scalability.

---

## 🧱 Tech Stack

### 🔹 Frontend  
[SvelteKit SPA](https://github.com/kopatsis/redirectionFrontend)  
- Landing page with form to shorten URLs  
- URL history dashboard (searchable, paginated)  
- QR code generation and download  
- Analytics view with graphs (clicks over time, geography, devices, etc.)

### 🔹 Redirection Server  
[Go redirection microservice](https://github.com/kopatsis/redirection)  
- Redirects to full URLs from `shk.fm/ID`  
- Stores and retrieves shortened URLs in Redis for speed  
- Logs click data: IP (hashed), city, country, device, browser, QR scan detection, etc.  
- Uses MaxMind Geo2 MMDB for geolocation  

### 🔹 Backend  
[Go backend service](https://github.com/kopatsis/redirectBackend)  
- Manages users, URLs, and click data in PostgreSQL  
- Handles authentication (Firebase for now; migrating to proprietary system)  
- Processes Stripe payments for pro users  
- Exposes internal APIs used by the frontend  

---

## 👑 Pro Features (Paid Membership)

- Create custom short URLs (e.g. `/brads-site`)
- Export full URL history as CSV
- Access advanced analytics (beyond the free dashboard view)
- Export all click data per shortened URL as CSV (IPs are hashed and anonymized)
- Download ZIP of all QR codes associated with shortened URLs
- Bulk import/export via CSV/XLSX (coming soon)
- API access for automation (coming soon)

---

## 🚧 In Development

- Replacing Firebase auth with a custom secure system:
  - Rate limiting
  - Encrypted passwords
  - 2FA support
  - Cloudflare Turnstile verification
- Enhanced UI polish for pro-grade visual experience
- XLSX/CSV import/export features
- Zip archive download of QR codes for all shortened URLs
- API endpoints for managing URLs, exporting analytics, and uploading link batches
- Migration of backend to repository pattern for maintainability

---

## ? Any questions

> Fill out this form and [Contact Me Here](https://kopatsis.com#contact)  

---

