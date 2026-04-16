<div align="center">

<img src="https://img.shields.io/badge/KitabDaan-Free%20Book%20Exchange-2d6a4f?style=for-the-badge&logo=bookstack&logoColor=white" alt="KitabDaan"/>

# 📚 KitabDaan

### *"Give books a second life."*

**A free, zero-infrastructure book exchange platform for students in Classes 9–12.**  
Donate your old NCERT books. Find the ones you need. Earn points. Pay nothing.

<br/>

[![Live Site](https://img.shields.io/badge/🌐%20Live%20Site-View%20KitabDaan-2d6a4f?style=for-the-badge)](https://your-username.github.io/kitabdaan/)
[![Made with Love](https://img.shields.io/badge/Made%20with-❤️%20for%20Students-e88c4a?style=for-the-badge)](#)

<br/>

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Google Apps Script](https://img.shields.io/badge/Google%20Apps%20Script-4285F4?style=flat-square&logo=google&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google%20Sheets-34A853?style=flat-square&logo=google-sheets&logoColor=white)
![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-222222?style=flat-square&logo=github&logoColor=white)

</div>

---

## ✨ What is KitabDaan?

KitabDaan is a **community-driven book exchange** built specifically for Indian students in Classes 9–12. Every year, lakhs of NCERT books are left unused after board exams — KitabDaan gives them a second life.

- 📖 **Donors** list their old books for free
- 🔍 **Students** find and contact donors directly on WhatsApp
- ⭐ **Donors earn points** when their book is picked up
- 🎁 **Points are redeemable** for popular titles like The Alchemist, Atomic Habits, and more

Zero cost. Zero middlemen. Just books finding new homes.

---

## 🚀 Features

| Feature | Description |
|---|---|
| 📖 **Donate a Book** | List any Class 9–12 NCERT book with condition, city, and WhatsApp number |
| 🔍 **Browse & Filter** | Filter by class, subject, or search by title / city |
| 💬 **WhatsApp Connect** | One-tap button to message the donor directly — no sign-up needed |
| ⭐ **Points System** | Earn 10 points every time your donated book is picked up |
| 🎁 **Rewards Store** | Redeem points for popular books from the catalogue |
| 🔐 **Admin Panel** | Password-protected panel to manage all listings |
| ✅ **Mark as Taken** | Admin marks a book as taken → points are auto-awarded to the donor |
| ↩️ **Restore Listing** | Admin can un-mark a listing back to available |
| 🗑️ **Delete Listing** | Admin can permanently remove a listing with confirmation |
| 📊 **Live Stats** | Real-time count of total / available / taken books |
| 🔎 **Points Lookup** | Donors check their points balance by entering their phone number |
| ☁️ **Google Sheets Backend** | All data persists in a real database — works across all devices |

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | Vanilla HTML + CSS + JavaScript (single file, no framework, no build step) |
| **Backend** | Google Apps Script (serverless, free, runs on Google's infrastructure) |
| **Database** | Google Sheets (auto-created and managed by the script) |
| **Hosting** | GitHub Pages (free, CDN-backed, auto-deploys on push) |
| **Fonts** | Google Fonts — Instrument Serif + DM Sans |

---

## 🗂️ Project Structure

```
kitabdaan/
├── index.html        ← Entire frontend (single file, no framework)
├── books.json        ← NCERT book catalogue for Classes 9–12
├── Code.gs           ← Google Apps Script backend (deploy separately)
└── README.md
```

---

## ⚙️ Setup Guide

### 1. Create a Google Sheet

1. Go to [sheets.google.com](https://sheets.google.com) and create a new spreadsheet
2. Name it anything you like (e.g. `KitabDaan Database`)
3. The script will auto-create all columns on first run — **you don't need to add them manually**

### 2. Deploy the Apps Script Backend

1. Inside your Google Sheet, click **Extensions → Apps Script**
2. Delete any existing code and paste the full contents of `Code.gs`
3. At the top of the file, make sure the sheet name matches your tab:
   ```js
   const SHEET_NAME = 'Sheet1'; // ← match your tab name exactly
   ```
4. Click **Save** (Ctrl + S)
5. Click **Deploy → New deployment**
6. Set the following:
   - **Type:** Web App
   - **Execute as:** Me
   - **Who has access:** Anyone
7. Click **Deploy**, authorize when prompted, and **copy the Web App URL**

### 3. Update `index.html`

Find this line near the top of the `<script>` block:

```js
const SHEET_URL = "https://script.google.com/macros/s/YOUR_SCRIPT_ID/exec";
```

Replace it with your Web App URL from Step 2.

### 4. (Optional) Change the Admin Password

```js
const ADMIN_PASSWORD = "your-strong-password-here"; // ← change this
```

> ⚠️ **Do not commit your real password to a public GitHub repository.**

### 5. Push to GitHub Pages

```bash
git add index.html books.json README.md
git commit -m "feat: initial KitabDaan deployment"
git push
```

Your site will be live at `https://<your-username>.github.io/kitabdaan/` within a minute.

---

## 🔐 Admin Panel

Access the admin panel by:
- Clicking the **KitabDaan logo 5 times quickly** (secret shortcut), or
- Navigating directly to `/?page=admin`

### Admin Capabilities

| Action | What it does |
|---|---|
| **Mark Taken** | Sets status to `taken`, awards 10 points to the donor |
| **Restore** | Sets status back to `available`, removes points flag |
| **Delete** | Permanently removes the listing after confirmation |
| **Refresh** | Re-fetches all listings live from Google Sheets |
| **Search / Filter** | Filter by name, phone, city, book title, status, or class |

The sync badge shows **● Live** when connected to Google Sheets, or **⚠ Offline** when falling back to locally cached data.

---

## ⭐ How the Points System Works

```
Donor lists a book
        ↓
Student contacts them via WhatsApp
        ↓
Admin marks the listing as "taken"
        ↓
10 points recorded against the donor's phone number
        ↓
Donor visits Rewards page → enters phone number → sees balance
        ↓
Donor redeems points for a book from the catalogue
```

Points are stored **per phone number** in Google Sheets, so they persist across all devices and sessions.

---

## 📱 Adding New Reward Books

Open `index.html` and find the `REWARDS_CATALOGUE` array:

```js
const REWARDS_CATALOGUE = [
  { id:'r1', title:'The Alchemist', author:'Paulo Coelho', pts:30, emoji:'✨', cat:'fiction', bg:'#fef9ec' },
  // add more entries below ↓
  { id:'r9', title:'My New Book', author:'Author Name', pts:25, emoji:'📗', cat:'selfhelp', bg:'#e8f4ee' },
];
```

Available categories: `fiction` · `selfhelp` · `science` · `biography`

---

## 🗺️ Roadmap

- [ ] Email / WhatsApp notification to donor when book is marked taken
- [ ] Admin can export all listings to CSV
- [ ] Pagination for large listing tables
- [ ] Image upload for book cover photos
- [ ] PWA support — offline mode + installable on mobile

---

## 🤝 Contributing

Pull requests are welcome! Please **open an issue first** to discuss what you'd like to change.

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m 'feat: add your feature'`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** — free to use, modify, and distribute.

---

<div align="center">

*Built with ❤️ for students who believe knowledge should be free.*

[![GitHub stars](https://img.shields.io/github/stars/your-username/kitabdaan?style=social)](https://github.com/your-username/kitabdaan)
[![GitHub forks](https://img.shields.io/github/forks/your-username/kitabdaan?style=social)](https://github.com/your-username/kitabdaan/fork)

</div>
