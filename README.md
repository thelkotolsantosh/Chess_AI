# ♟ Chess AI

A complete, professional browser-based Chess game with an AI opponent powered by **Minimax + Alpha-Beta Pruning**.

Built with pure **HTML5 · CSS3 · Vanilla JavaScript** — zero dependencies, zero frameworks.

---

## 🎮 Live Demo

> Deploy on Netlify → [See deployment guide below](#-deploying-to-netlify)

---

## ✨ Features

### Game Engine
- ✅ Full legal move generation for all 6 piece types
- ✅ Check & Checkmate detection
- ✅ Stalemate detection
- ✅ Castling (King-side & Queen-side)
- ✅ En passant
- ✅ Pawn promotion (player chooses piece)
- ✅ Algebraic notation (move history)

### AI Opponent
- ✅ Minimax algorithm with Alpha-Beta pruning
- ✅ Piece-Square Tables for positional play
- ✅ MVV-LVA move ordering (Most Valuable Victim / Least Valuable Attacker)
- ✅ 4 difficulty levels (depth 1–4)
- ✅ Checkmate seeking — exploits mistakes aggressively

### UI / UX
- ✅ Custom SVG pieces — Elephant 🐘 · Horse 🐴 · Camel 🐪 · King Crown 👑 · Queen Crown 👸
- ✅ Legal move highlights (dots + capture rings)
- ✅ Last move highlight
- ✅ Check highlight (red flash)
- ✅ Position evaluation bar
- ✅ Move history panel
- ✅ Captured pieces display with material advantage
- ✅ Flip board
- ✅ Undo move
- ✅ Responsive design (desktop · tablet · mobile)

---

## 🗂 Project Structure

```
chess-ai/
│
├── index.html          ← Complete game (HTML + CSS + JS in one file)
├── style.css           ← Extracted styles (reference)
├── script.js           ← Extracted JavaScript (reference)
│
├── ai/
│   ├── minimax.js      ← Minimax + Alpha-Beta algorithm explained
│   ├── evaluation.js   ← Board evaluation + Piece-Square Tables
│   └── moveGenerator.js← Legal move generation for all pieces
│
├── assets/
│   ├── pieces/         ← SVG piece assets (elephant, horse, camel, crowns)
│   └── sounds/         ← (Optional) move/capture sound effects
│
├── .gitignore
├── netlify.toml        ← Netlify deploy config
└── README.md
```

---

## 🤖 How the AI Works

### Phase 1 — Move Generation
Every legal move is generated for the current position. Pseudo-legal moves (ignoring check) are filtered by simulating each move and verifying the king isn't left in check.

### Phase 2 — Evaluation Function
The board is scored in centipawns:

| Piece  | Value |
|--------|-------|
| Pawn   | 100   |
| Knight | 320   |
| Bishop | 330   |
| Rook   | 500   |
| Queen  | 900   |
| King   | 20000 |

Plus **Piece-Square Table** bonuses rewarding good squares (center control, king safety, rook open files, etc.)

### Phase 3 — Minimax
The AI explores a game tree `N` levels deep, assuming:
- **Maximizer (White)** always picks the highest score
- **Minimizer (Black)** always picks the lowest score

### Phase 4 — Alpha-Beta Pruning
Cuts branches that can't affect the result — reduces nodes searched by ~90% vs plain minimax, enabling deeper searches in the same time.

### Phase 5 — Move Ordering
Captures and promotions are tried first (MVV-LVA heuristic), dramatically improving pruning effectiveness.

---

## 🚀 Deploying to Netlify

### Option A — Drag & Drop (fastest)
1. Go to [netlify.com](https://netlify.com) and sign in
2. Drag the entire `chess-ai/` folder onto the Netlify dashboard
3. Done — your site is live in seconds ⚡

### Option B — GitHub + Netlify (recommended)
1. Push this repo to GitHub (see below)
2. Log into [netlify.com](https://netlify.com)
3. Click **"Add new site"** → **"Import an existing project"**
4. Connect your GitHub account
5. Select this repository
6. Build settings:
   - **Build command:** *(leave empty)*
   - **Publish directory:** `.` (root)
7. Click **Deploy site**

Every `git push` to `main` will auto-deploy 🎉

---

## 🐙 Pushing to GitHub

```bash
# 1. Create a new repo on github.com (don't initialize with README)

# 2. In your terminal:
git init
git add .
git commit -m "🎉 Initial commit — Chess AI"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/chess-ai.git
git push -u origin main
```

---

## 🛠 Local Development

No build step needed — just open the file:

```bash
# Option 1: open directly
open index.html

# Option 2: local server (recommended to avoid CORS issues)
npx serve .
# or
python3 -m http.server 8080
```

---

## 📚 Learning Resources

This project teaches:
- DOM manipulation & event handling
- SVG drawing & animation
- Game loop design
- Recursive algorithms (Minimax)
- Tree search optimization (Alpha-Beta)
- Heuristic evaluation functions
- Chess programming fundamentals

---

## 📄 License

MIT License — free to use, modify, and distribute.

---

## 🙏 Credits

Built with ❤️ using pure HTML5 · CSS3 · Vanilla JavaScript.  
Chess engine: Minimax algorithm with Alpha-Beta pruning.  
Piece art: Custom SVG (Elephant · Horse · Camel · King Crown · Queen Crown).
