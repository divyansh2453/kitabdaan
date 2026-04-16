# 📚 KitabDaan — Free Book Exchange

> *"Give books a second life."*

KitabDaan is a free, zero-infrastructure book exchange platform for students in Classes 9–12. Anyone can donate their old NCERT books, and anyone can find one they need — all for free. Donors earn reward points when their book is picked up, redeemable for popular titles.

**Live site:** https://divyansh2453.github.io/kitabdaan/

---

## ✨ Features

| Feature | Description |
|---|---|
| 📖 **Donate a book** | List any Class 9–12 NCERT book with condition, city, and WhatsApp number |
| 🔍 **Browse & filter** | Filter by class, subject, or search by title / city |
| 💬 **WhatsApp connect** | One-tap button to message the donor directly |
| ⭐ **Points system** | Earn 10 points when your book is marked as taken |
| 🎁 **Rewards store** | Redeem points for popular books (Alchemist, Atomic Habits, etc.) |
| 🔐 **Admin panel** | Password-protected panel to manage all listings |
| ✅ **Mark as taken** | Admin marks books taken → points auto-awarded |
| ↩ **Restore listing** | Admin can un-mark a listing back to available |
| 🗑 **Delete listing** | Admin can permanently remove a listing (with confirmation) |
| 📊 **Live stats** | Real-time count of total / available / taken books |
| 🔎 **Points lookup** | Donors can check their points by entering their phone number |

---

## 🗂 Project Structure

```
kitabdaan/
├── index.html      ← Entire frontend (single file, no framework)
├── books.json      ← NCERT book catalogue (Class 9–12)
├── Code.gs         ← Google Apps Script backend (deploy separately)
└── README.md
```

---

## 🚀 Setup Guide

### 1. Deploy the Google Apps Script backend

This gives KitabDaan a real database so listings persist across devices.

1. Go to [script.google.com](https://script.google.com) and create a new project.
2. Delete any existing code and paste the contents of **`Code.gs`**.
3. Click **Deploy → New deployment**.
4. Set:
   - **Type:** Web App
   - **Execute as:** Me
   - **Who has access:** Anyone
5. Click **Deploy** and copy the **Web App URL**.

### 2. Update `index.html`

Open `index.html` and find this line near the top of the `<script>` block:

```js
const SHEET_URL = "https://script.google.com/macros/s/YOUR_SCRIPT_ID/exec";
```

Replace it with your Web App URL from Step 1.

### 3. (Optional) Change the admin password

In `index.html`, find:

```js
const ADMIN_PASSWORD = "kitabdaan2024";
```

Change this to a strong password. **Do not commit your real password to a public GitHub repo.** Consider using a `.env` approach or GitHub Secrets if you automate deployment.

### 4. Push to GitHub Pages

```bash
git add index.html books.json README.md
git commit -m "feat: working admin panel with Google Sheets backend"
git push
```

Your site will be live at `https://<your-username>.github.io/kitabdaan/` within a minute.

---

## 🔐 Admin Panel

Access the admin panel by:
- Clicking the **KitabDaan** logo **5 times quickly** (secret shortcut), or
- Navigating directly to `/?page=admin` and using the password.

### Admin capabilities

| Action | What it does |
|---|---|
| **Mark taken** | Sets status to `taken`, awards 10 points to the donor's record in the sheet |
| **Restore** | Sets status back to `available`, removes points flag |
| **Delete** | Permanently removes the listing after confirmation |
| **Refresh** | Re-fetches all listings from Google Sheets |
| **Search / filter** | Filter by name, phone, city, book title, status, or class |

The sync badge in the top-right of the panel shows **● Live** when connected to the sheet, or **⚠ Offline** when using locally-cached data.

---

## ⭐ How the Points System Works

```
Donor lists a book
       ↓
Someone contacts them on WhatsApp
       ↓
Admin marks the listing as "taken"
       ↓
10 points are recorded against the donor's phone number in the sheet
       ↓
Donor visits the Rewards page → enters their phone number → sees their points
       ↓
Donor redeems points for a book from the catalogue
```

Points are stored **per phone number** in the Google Sheet, so they persist across devices. The donor just needs to enter their WhatsApp number on the Rewards page to check.

---

## 🛠 Tech Stack

- **Frontend:** Vanilla HTML + CSS + JS (single file, no build step, no framework)
- **Backend:** Google Apps Script (serverless, free, runs on Google's infrastructure)
- **Database:** Google Sheets (auto-created on first run)
- **Hosting:** GitHub Pages (free, CDN-backed)
- **Fonts:** Google Fonts (Instrument Serif + DM Sans)

---

## 📱 How to Add New Reward Books

Open `index.html` and find the `REWARDS_CATALOGUE` array:

```js
const REWARDS_CATALOGUE = [
  { id:'r1', title:'The Alchemist', author:'Paulo Coelho', pts:30, emoji:'✨', cat:'fiction', bg:'#fef9ec' },
  // add more here ↓
  { id:'r9', title:'My New Book', author:'Author Name', pts:25, emoji:'📗', cat:'selfhelp', bg:'#e8f4ee' },
];
```

Categories available: `fiction`, `selfhelp`, `science`, `biography`.

---

## 🗺 Roadmap

- [ ] Email/WhatsApp notification to donor when book is marked taken
- [ ] Admin can export listings to CSV
- [ ] Pagination for large listing tables
- [ ] Image upload for book cover photos
- [ ] PWA support (offline + installable)

---

## 🤝 Contributing

Pull requests are welcome! Please open an issue first to discuss what you'd like to change.

---

## 📄 License

MIT — free to use, modify, and distribute.

---

*Built with ❤️ for students who believe knowledge should be free.*
