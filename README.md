# 📚 KitabDaan

> Give your books a second life — and earn rewards for it.

KitabDaan is a modern web platform that enables students to donate academic books (Classes 9–12) and earn reward points when their books are successfully reused by others.

It combines **cloud storage, real-time listings, and a reward redemption system** into a seamless experience.

---

## 🌟 Key Features

### 📖 Book Donation System
- Simple form to list books for donation
- Structured selection (Class → Subject → Book)
- Book condition tracking (Good / Acceptable / Poor)
- Location-based listings

### ☁️ Cloud Storage Integration
- All listings stored in **Google Sheets via Apps Script**
- Real-time sync between users and admin
- Offline fallback using local storage

### 🎯 Reward Points System
- Earn **10 points** when your donated book is marked as taken
- Points are linked to your phone number
- Live points lookup system

### 🎁 Rewards Catalogue (Redeem System)
- Use points to redeem books like:
  - Atomic Habits
  - The Alchemist
  - Rich Dad Poor Dad
  - And more...
- Smart UI disables redeem if points are insufficient
- Instant deduction on redemption

### 🔍 Browse & Discover
- Filter books by class and subject
- Search by book name or city
- WhatsApp integration for direct contact

### 🛠️ Admin Panel
- View all listings (cloud synced)
- Mark books as **taken / available**
- Automatically trigger reward points
- Delete or manage listings
- Live sync status indicator

---

## 🧠 How It Works

1. User donates a book via the form  
2. Data is stored in **cloud (Google Sheets)**  
3. Book appears in public listings  
4. When someone takes the book:
   - Admin marks it as **taken**
   - Donor receives **+10 points**  
5. User can:
   - Check points via phone number  
   - Redeem books from catalogue 🎁  

---

## 🛠️ Tech Stack

| Layer        | Technology |
|-------------|-----------|
| Frontend    | HTML, CSS, JavaScript |
| Backend     | Google Apps Script |
| Database    | Google Sheets |
| Storage     | Cloud + Local Storage (fallback) |
| Hosting     | Static Hosting (Page.gd / GitHub Pages) |

---

## ⚡ Core Highlights

- 🚀 **No traditional backend required**
- 🔄 **Real-time cloud sync**
- 📱 **Fully responsive UI**
- ⚡ **Fast & lightweight**
- 🧩 **Hybrid storage (cloud + local fallback)**

---

## 📂 Project Structure
