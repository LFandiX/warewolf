# ⚔️ ALVERIX — Game Realm

> A collection of browser-based multiplayer games built with vanilla HTML/CSS/JS and Firebase Realtime Database. No downloads, no installs — just share a code and play.

---

## 🎮 Games

### ⚔️ Elemental Duel
> *2–6 players · Card Strategy · Real-time*

Draw elemental cards, exploit weaknesses, and be the last warrior standing.

- 8 elements (Fire, Water, Thunder, Earth, Wind, Shadow, Holy, Ice) + 3 Rare cards (Meteor, Barrier, Alchemy)
- Elemental advantage system (+50% damage)
- Status effects: Burn, Stun, Freeze, Shield, Immune
- Dead players spectate until game ends
- Comeback mechanic for low-HP players
- Real-time multiplayer via room code

---

### 🐺 Werewolf
> *4–12 players · Social Deduction · Real-time*

Classic Werewolf / Mafia — night falls, wolves hunt, villagers discuss and vote.

- Roles: Werewolf, Villager, Doctor, Detective
- Wolf-only night chat
- Configurable player count and phase timers
- Real-time voting and execution

---

### 💬 How Well Do You Know Me?
> *3–8 players · Party / Social · Real-time*

Answer questions about each other, vote for who fits best, and see who truly knows their friends.

- 60+ unique questions shuffled each session
- Kahoot-style leaderboard after each round
- Real-time emoji reactions across all devices
- Fun end stats (Most Voted, Best Guesser, The Mystery One, etc.)
- Host controls: pause, skip, configure rounds & timer

---

## 📁 Folder Structure

```
/
├── index.html                  # Game Hub landing page
├── elemental-duel.html         # Elemental Duel game    
│── rules.html                  # Element guide & rules
├── warewolf.html               # Werewolf game          
└── howwell.html                # How Well Do You Know Me
           
```

---

## 🛠️ Tech Stack

| Technology | Usage |
|---|---|
| HTML / CSS / JS | All game UI and logic (no frameworks) |
| Firebase Realtime Database | Real-time multiplayer sync |
| GitHub Pages | Hosting |
| Hostinger DNS | Custom domain `alverix.site` |
| Google Fonts | Cinzel, Exo 2, Crimson Pro |

---

## 🔥 Firebase Setup

Each game needs its own Firebase Realtime Database, or you can share one project across all games.

**1. Create a Firebase project**
- Go to [console.firebase.google.com](https://console.firebase.google.com)
- Create a new project → Enable **Realtime Database** → Start in **Test mode**

**2. Get your config**
- Project Settings → Your Apps → Web App → SDK Config

**3. Paste config into each game file**

Find this block near the top of the `<script>` in each game's HTML:

```js
const FIREBASE_CONFIG = {
  apiKey: "GANTI_API_KEY_KAMU",
  authDomain: "GANTI.firebaseapp.com",
  databaseURL: "https://GANTI-default-rtdb.firebaseio.com",
  projectId: "GANTI",
  storageBucket: "GANTI.appspot.com",
  messagingSenderId: "GANTI",
  appId: "GANTI"
};
```

Replace with your actual config values.

**4. Restrict your API key** *(recommended)*

Go to [Google Cloud Console](https://console.cloud.google.com) → APIs & Services → Credentials → Browser key → HTTP referrers, then add:

```
https://alverix.site/*
https://LFandiX.github.io/*
http://localhost/*
```

---

## 🚀 Deploy to GitHub Pages

**1. Push to GitHub**
```bash
git init
git add .
git commit -m "initial commit"
git branch -M main
git remote add origin https://github.com/LFandiX/alverix.git
git push -u origin main
```

**2. Enable GitHub Pages**
- Repo → Settings → Pages → Source: `main` branch → `/ (root)`

**3. Custom domain (optional)**
- Add `alverix.site` in the Custom Domain field
- At your DNS provider (Hostinger), add a CNAME record:
  ```
  Type:  CNAME
  Name:  @  (or www)
  Value: lfandix.github.io
  ```
- Wait 10–30 minutes for DNS propagation and HTTPS certificate

---

## 🗂️ Database Security Rules

For production, replace the default Test Mode rules in Firebase with:

```json
{
  "rules": {
    "rooms": {
      "$roomId": {
        ".read": true,
        ".write": true,
        ".validate": "newData.hasChildren(['phase', 'players'])"
      }
    }
  }
}
```

---

## 📸 Preview
<img width="1899" height="864" alt="image" src="https://github.com/user-attachments/assets/5ec7abab-615c-4228-bd2d-0c0a9db13a9e" />


---

## 👤 Credits

Made by **[@LFandiX](https://github.com/LFandiX)**

---

## 📄 License

This project is open source for personal and educational use.
Feel free to fork and build your own game realm!
