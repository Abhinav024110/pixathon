# AI_LOG.md — Pixathon AI Assistance Audit

**Project Title:** Human Check: The Vibe Check CAPTCHA  
**Team ID:** PX-VibeCheck  

---

## 🛠️ Tools Used

* **Gemini (Canvas):** Meta-prompt engineering, prompt refactoring, and hackathon rule synthesis.
* **VS Code AI / GitHub Copilot:** Core HTML5/CSS3 single-file architecture generation and JavaScript game loop implementation.
* **Stitch by Google Labs:** Conceptual design layout and HUD/UI framing.
* **PixelLab:** Pixel art theme guidelines and retro cat mascot asset design (`.pixel-cat`).
* **jsfxr / ElevenLabs:** Audio effect cues and sound design planning.

---

## 🔑 Key Prompts

### 1. Meta-Prompting (Core Loop & Guidelines)
> *"Given the attached Pixathon competition PDF, generate a structured prompt for VS Code AI to build a single-file interactive web puzzle game called 'Human Check: The Vibe Check CAPTCHA'."*
* **Purpose:** Initial architectural planning and constraint setting for single-file browser execution.

### 2. Core Game Loop Engine
> *"You are a Lead Frontend Engineer. Build a single-file browser game titled 'Human Check: The Vibe Check CAPTCHA' with a 30-second countdown timer, progress bar (1/3), pass/fail overlays, zero page reloads on retry, and responsive controls."*
* **Purpose:** Scaffolded the core state machine, overlay management, and main HUD timer loop.

### 3. Interactive Wire Untangle Logic (Level Math)
> *"Write an SVG-based cable tracing mini-game where the user drags a plug along a squiggly path. Track completion progress from 0% to 100% using SVG `getTotalLength()` and fail the attempt if the pointer drifts too far off the path."*
* **Purpose:** Implemented mathematical trajectory checking and continuous touch/mouse tracking.

### 4. Expansion & Content Humanization (Juice & Variety)
> *"Expand the game into 8 scenarios: Earbud Escape, Elevator Diplomacy (hold button), Song Rewind (slider precision), Camera Chase (clicking target), Midnight Microwave (precision timing), Goodbye Spiral (closing popups), Voice-Note Typos (string match), and Chore Dodger (2D falling object dodge). Make the tone sarcastic and human."*
* **Purpose:** Generated all 8 distinct interactive mechanics and comical copywriter microtext.

### 5. Microwave Delta Timing Precision
> *"Create a timing mini-game using `performance.now()` where a needle sweeps across a bar. The user must hit STOP within a tight yellow zone (between 350ms and 1800ms remaining before the final beep)."*
* **Purpose:** Added precision timing mechanics for Stage 5.

### 6. Chore-Dodging Physics Loop
> *"Build a mini-game using a 50ms interval collision loop. Spawn falling emojis from random X coordinates. Allow the player to move left/right with arrow keys or buttons, tracking 3 lives and invulnerability frames."*
* **Purpose:** Built the final boss survival game loop.

---

## ⚠️ When AI Got It Wrong

### **The Issue: Unsolvable Wire Path & Pointer Disconnect**
During the initial build of **Stage 1 (Earbud Escape)**, the AI generated quadratic SVG curve control points (`Q` path commands) that produced extreme sharp loops extending outside the viewBox. 

Additionally, the nearest-point search algorithm allowed the user to jump directly from the start point to the end point without following the intermediate cable curve, instantly clearing the stage without completing the untangle puzzle.

### **How We Fixed It**
1. **Visual Bounds:** Constrained random curve offsets to within `42px - 187px` on the Y-axis so path points remain cleanly within the 600x235 SVG canvas.
2. **Anti-Cheat Step Validation:** Introduced `permittedJump` checks against previous pointer coordinates to prevent teleportation across curve segments, forcing continuous manual tracing along the path length.