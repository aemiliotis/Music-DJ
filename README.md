# Music-DJ

https://aemiliotis.github.io/Music-DJ/

# 🎧 LogicTech Music DJ

> **Escape Room Audio Sequencer** — a browser-based audio player that plays different music per step, with fade in/out, loop or sequence modes, and a portable `.lgt` project format that only stores file paths.

[![Made with JavaScript](https://img.shields.io/badge/Made%20with-JavaScript-f7df1e?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![No dependencies](https://img.shields.io/badge/Dependencies-none-88ffaa?style=for-the-badge)](#)
[![Single file](https://img.shields.io/badge/Single--file-HTML-ff8c42?style=for-the-badge)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)

---

## 📖 Table of Contents

- [What is it?](#-what-is-it)
- [Why "Music DJ"?](#-why-music-dj)
- [Features](#-features)
- [Screenshots / Layout](#-screenshots--layout)
- [Quick Start](#-quick-start)
- [Home Folder System](#-home-folder-system)
- [How to Use](#-how-to-use)
- [Project File (.lgt)](#-project-file-lgt)
- [Typical Escape Room Use Cases](#-typical-escape-room-use-cases)
- [Playing on Mobile with Bluetooth](#-playing-on-mobile-with-bluetooth)
- [Playing on PC with Line-Out to Amplifier](#-playing-on-pc-with-line-out-to-amplifier)
- [Browser Support](#-browser-support)
- [Keyboard Shortcuts](#-keyboard-shortcuts)
- [Tips & Best Practices](#-tips--best-practices)
- [Troubleshooting](#-troubleshooting)
- [Privacy](#-privacy)
- [License](#-license)
- [Credits](#-credits)

---

## 🎯 What is it?

**LogicTech Music DJ** is a single HTML file that turns any modern browser into a live audio sequencer for escape rooms, theatre cues, or themed installations.

You build a list of **steps**. Each step has a **mode** and a set of **MP3/WAV/etc. files**. You press play — the app plays the current file with a smooth fade in, and at the end either:

- **loops** the same file forever (`loop` mode), or
- advances to the **next file** in the same step, and when the step ends, moves to the **next step** (`sequence` mode).

Perfect for controlling ambience that changes as players progress through your escape room.

---

## 💡 Why "Music DJ"?

Because you're the DJ. You decide:

- Which track plays **when** (per step)
- Whether it **repeats** or **flows** into the next
- How **loud** it is, how long the **fade** is
- When to **jump** to the next file or next step with a single tap

All without writing any code.

---

## ✨ Features

### 🎵 Core Audio

- **Step sequencer** — unlimited steps, unlimited files per step
- **Per-step mode** — `loop` or `sequence`
- **Fade in / fade out** — adjustable 0 – 3000 ms slider
- **Live volume control** — slider + mute/unmute from the footer
- **Auto-advance** — end of file → next file → next step, seamlessly
- **Jump controls** — next MP3 / next step / play from any step / stop
- **Background play friendly** — audio keeps playing while you interact with the page

### 🏠 Home Folder System

- Pick **one home folder** — all audio lives inside it (any subfolder structure is fine)
- The `.lgt` project file stores only **relative paths** (`Halloween/scream.mp3`), not absolute ones
- Move the project and the audio folder to **any other machine** — same relative structure means it just works
- **Reconnect All** wizard: pick the home folder once on load → all files relink in one pass

### 💾 Save / Load

- **`.lgt` project format** — tiny, obfuscated, path-only
- **Save** remembers the last filename you used (defaults to `project1.lgt` on first save)
- **Load** restores step structure, modes, fade, volume — then asks for the home folder
- Works entirely offline — no server, no upload, no tracking

### 📱 Cross-Device

- Runs on **any modern browser** (Chrome, Edge, Opera, Brave for full features)
- **Responsive UI** — adapts to phone, tablet, and desktop
- **Touch-friendly** — big tap targets, no hover-only controls
- **Bluetooth audio** works out of the box — pair the device to any BT speaker
- **Line-out to amplifier** on PC — full stereo output through the 3.5 mm jack or USB DAC

### 🎨 Interface

- **Dark escape-room aesthetic** — LogicTech orange on deep navy
- **Live stats** — steps, files, linked count, currently playing file
- **Status badge** — Ready / Playing / Loaded / Saved
- **Toast notifications** — clear feedback on every action
- **Help manual** — built-in `?` button with the full user guide

### 🔒 Content Unlock Modal

- Google Forms iframe on first visit
- **Only a real submission** hides it forever (`localStorage` flag)
- "I just want to try it →" closes it just for this session — it will show again next time

---

## 🖼 Screenshots / Layout

```
┌─────────────────────────────────────────────────────────────────────┐
│  🏠 Home folder  ▶ from  🎚 fade          ? (help)                  │  ← top bar
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│   🎵 Step 1  [3 files]     🔁 loop | ➡ sequence  ⏭ next mp3  ⏩ … │
│   ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐           │
│   │  🎵 file │  │  🎵 file │  │  🎵 file │  │ + add mp3│           │
│   └──────────┘  └──────────┘  └──────────┘  └──────────┘           │
│                                                                     │
│   🎵 Step 2  [2 files]     🔁 loop | ➡ sequence  ⏭ next mp3  ⏩ … │
│   ┌──────────┐  ┌──────────┐  ┌──────────┐                         │
│   │  🎵 file │  │  🎵 file │  │ + add mp3│                         │
│   └──────────┘  └──────────┘  └──────────┘                         │
│                                                                     │
├─────────────────────────────────────────────────────────────────────┤
│  🎵 Steps: 2  🎧 Files: 5  ✅ Linked: 5  ▶ Now: scream             │
│  🔊 [========●] 80%  🔈    📐 Ready                                │
│  ➕ Add Step | ▶ Play  ⏹ Stop  ⏭ Next MP3  ⏩ Next Step | 💾 Save … │  ← footer
└─────────────────────────────────────────────────────────────────────┘
```

---

## 🚀 Quick Start

1. **Download** the single HTML file (`music-dj.html` or similar) and put it anywhere — it doesn't need a server.
2. **Open** it in Chrome, Edge, Opera, or Brave (Firefox/Safari have limited folder access — see [Browser Support](#-browser-support)).
3. Click **🏠 Set Folder** in the top-left and pick the folder that holds all your audio.
4. Click **➕ Add Step** to create your first step.
5. Click **＋ add mp3**, tick the files you want in this step, then **＋ Add Selected**.
6. Repeat for as many steps as you need.
7. Click **▶ Play** or the **▶ GO** button and enjoy.
8. Click **💾 Save** to download a `.lgt` project file you can reuse forever.

That's it. No install, no login, no build step.

---

## 🏠 Home Folder System

The app is built around a **single home folder** that contains every audio file the project uses. This has several advantages:

- **Portable** — move `MyEscapeRoom/` (folder + `.lgt`) to any machine and it just works.
- **Predictable** — all paths stored in the `.lgt` are **relative** to the home folder.
- **One-click relink** — after loading a project, pick the home folder once and every file is relinked.
- **Organized** — you're free to use subfolders: `Step1/intro.mp3`, `Halloween/scream.mp3`, `Ambient/rain.ogg`, etc.

Example home folder:

```
MyEscapeRoom/                    ← home folder (this is what you pick)
├── Step1/
│   ├── intro.mp3
│   └── heartbeat.mp3
├── Step2/
│   └── scream.mp3
├── Ambient/
│   ├── rain.ogg
│   └── wind.mp3
└── Victory/
    └── fanfare.mp3
```

The `.lgt` will store `Step1/intro.mp3`, `Step2/scream.mp3`, etc. — never the full disk path.

---

## 🎮 How to Use

### Building a Step

1. Click **➕ Add Step**.
2. Choose the step's mode:
   - **🔁 loop** — the same file repeats forever. Use for background ambience.
   - **➡ sequence** — the files play one after the other, then the next step starts.
3. Click **＋ add mp3** to browse the home folder and tick the files you want.
4. Click **＋ Add Selected**.

### Playing

- **Click any file card** to play it immediately with a fade-in.
- **▶ GO** starts from the step chosen in the "from" dropdown.
- **⏭ next mp3** jumps to the next file inside the current step.
- **⏩ next step** jumps to the first file of the next step.
- **⏹ Stop** fades out the current audio.
- **Space** toggles play/stop.

### Fade and Volume

- **🎚 fade** slider (top-left) — set fade duration from 0 to 3000 ms.
- **🔊 volume** slider (footer) — live volume; affects currently-playing audio immediately.
- **🔈 mute** button — one-tap mute/unmute; remembers the previous volume.

### Saving and Loading

- **💾 Save** — downloads `<lastFilename>.lgt`. Defaults to `project1.lgt` the first time.
- **📂 Load** — pick a `.lgt`; the app restores steps, modes, fade, and volume; then asks for the home folder to relink everything.
- **🔗 Reconnect All** — visible when any file is missing; pick the home folder once and everything relinks.

---

## 📦 Project File (`.lgt`)

The `.lgt` file is a tiny obfuscated text file that stores:

- Step structure (which files belong to which step)
- Each step's mode (`loop` or `sequence`)
- Relative path + filename of every audio file
- Fade duration
- Volume level
- The name of the home folder (as a hint, not a requirement)

It does **not** store:

- Audio data (no MP3 bytes)
- Absolute disk paths
- Any user info, network calls, or cookies

You can safely email, back up, or version-control `.lgt` files.

---

## 🎭 Typical Escape Room Use Cases

### 1. Progressive Ambience

As players solve puzzles, the music changes.

- **Step 1**: soft intro (`loop`)
- **Step 2**: tension building (`sequence`)
- **Step 3**: victory fanfare (`sequence`)

Each step's files sit in their own subfolder for easy editing.

### 2. Puzzle-Triggered Cues

Place the page on a tablet near the GM. Click file cards manually to fire specific sounds — door creak, scream, alarm. Use the per-file cards as an on-demand soundboard.

### 3. Multi-Room Timeline

Build one `.lgt` per room and load the correct one on each machine. All rooms reference the same home folder on a shared drive (or per-machine local copy).

### 4. Theatre Cue Sequences

Line up cue after cue in a single step in `sequence` mode, and press **▶ GO**. When the last cue ends, the next step (the next act) begins automatically.

### 5. Loop the Room Theme

Use `loop` mode on a single file per step. Each step is a different room theme. Jump between themes with **⏩ next step**.

---

## 📱 Playing on Mobile with Bluetooth

The app works **unchanged** on phones and tablets — the mobile browser is the player.

### Setup

1. **Pair** your phone/tablet to the Bluetooth speaker, soundbar, or headset as usual (system Bluetooth settings).
2. Open the `.html` file in **Chrome for Android** (desktop Chrome and Edge also work on tablets).
3. If you copied the project to your phone, pick the **home folder** stored on the phone's storage.
4. Tap **▶ GO** — audio routes through Bluetooth automatically.

### Recommended Workflow for Live Use

- **Disable battery optimization** for the browser so the tab isn't killed mid-session.
- **Keep the screen on** — Settings → Display → Screen timeout → Never (or very long).
- **Do Not Disturb ON** — avoid notification sounds mixing into the room audio.
- **Turn on Airplane mode with Bluetooth re-enabled** — prevents calls and messages from interrupting playback.
- **Use a dedicated device** if possible — a spare tablet or old phone that lives in the room.
- **Pre-charge the BT speaker** and keep the charger nearby.

### Bluetooth Fade Tip

Some Bluetooth speakers have a small latency (100–300 ms) and occasionally cut the very first millisecond of audio when starting. Because the app **fades in from 0 volume**, you won't hear a click — but if you want the very first beat intact, set the fade to a small value like **100–200 ms** and press Play half a second before you need the sound.

### Hands-Free Use

- Pair a **Bluetooth presenter remote** (the kind with arrow keys) to advance **⏭ next mp3** or **⏩ next step** without touching the screen. The arrow keys are already wired.

---

## 🖥 Playing on PC with Line-Out to Amplifier

This is the highest-fidelity setup and the one most escape rooms with a fixed audio system use.

### Setup

1. Open the HTML file in **Chrome / Edge / Opera / Brave** on the PC.
2. Set the home folder to your audio directory.
3. Connect the PC's audio output to your amplifier:
   - **3.5 mm jack → RCA / 6.3 mm** cable for most amps
   - **USB DAC → RCA** if you want better signal-to-noise
   - **Optical / HDMI** if the amp supports it and you have a digital output
4. Set the system output device correctly in Windows: **Settings → System → Sound → Output**.
5. In the app, set volume slider to **100%** and use the amplifier's gain knob to set the room level.

### Pro Tips for Line-Out

- **Set the OS volume to 100%** and control the final level on the amplifier. This gives the cleanest signal-to-noise ratio.
- **Disable Windows sound effects / enhancements** (Spatial Sound, Loudness Equalization, etc.) for uncolored playback.
- **Disable sleep** and **screen saver** while the app is running.
- **Disable notification sounds** — Windows → System → Notifications → turn off (or enable Focus Assist).
- **Use `chrome --kiosk file:///C:/path/to/music-dj.html`** to launch in kiosk mode for a dedicated playback screen.
- **Never close the laptop lid** — set "Do nothing" when lid is closed.
- If you want the app to run forever, add it to the **Startup folder** or a scheduled task that launches Chrome in kiosk mode at boot.

### Multi-Channel / Multiple Amps

If you want different audio in different rooms:

- Open the HTML file in **multiple Chrome windows**, one per amp.
- Load a different `.lgt` in each window (one per room).
- Each window uses its own audio path — no interference.

### Latency Considerations

Chrome's audio output latency is normally around 20–50 ms on modern hardware, which is imperceptible for ambience. If you're syncing to a live performance, you can still use the app for triggering — just leave the fade low and hit Play manually on the beat.

---

## 🌐 Browser Support

| Feature | Chrome | Edge | Opera | Brave | Firefox | Safari |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| Folder picker (home folder) | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ |
| Audio playback | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Save/Load `.lgt` | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Auto relink from home folder | ✅ | ✅ | ✅ | ✅ | ⚠ | ⚠ |
| Bluetooth routing | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

**Recommended:** Chrome, Edge, Opera, or Brave.  
Firefox and Safari can't access folder contents by name, so the home-folder system won't work. They can still play audio if you pick files manually, but you'll lose the one-click relink.

**Note:** On Neocities and other static hosts, the app works because it never touches the server — everything happens locally in the browser.

---

## ⌨ Keyboard Shortcuts

| Key | Action |
|---|---|
| `Space` | Play / Stop |
| `→` | Next MP3 in current step |
| `Ctrl` + `→` | Next step |
| `Esc` | Close modals / deselect |
| `F1` | Open Help manual |

---

## 💡 Tips & Best Practices

- **Organize audio in subfolders** per step or per theme. It makes editing trivial and keeps the `.lgt` readable.
- **Keep filenames consistent** — the relink wizard matches by exact filename, so `scream.mp3` must stay `scream.mp3`.
- **Use `.mp3` files at 128–320 kbps** — good quality, small enough to load fast.
- **Test the whole sequence once** before going live. Press **▶ GO** on the first step and let it run to the end.
- **Save a "demo" `.lgt` and a "live" `.lgt`** — swap between them without rebuilding.
- **Back up the home folder** to a USB stick alongside the `.lgt`. If the show machine dies, you can be back up in 30 seconds.
- **Set the fade to 0** if you need instant cues (e.g. a loud jump-scare). Fade is smooth only when you want it.
- **Turn off browser notifications** — Chrome → Settings → Privacy → Site Settings → Notifications → Block all, at least for `file://`.
- **Disable power-saving features on the machine** during live use.
- **Label your BT speaker** — in a multi-room setup it's easy to pair the wrong one.

---

## 🛠 Troubleshooting

**The "＋ add mp3" button says "🏠 set home folder first"**
Click **🏠 Set Folder** in the top-left and pick your home folder.

**After loading a `.lgt`, files show "not linked"**
Click **🔗 Reconnect All** in the footer. Pick the home folder. The app walks it and relinks by relative path.

**Audio doesn't play**
- Click somewhere on the page first (browsers require a user gesture before playing sound).
- Check the volume slider in the footer and the system volume.
- On macOS, check System Settings → Sound → Output.

**File plays but no sound from the amplifier**
- Confirm the OS output device is the amplifier, not the laptop speakers.
- Check the amplifier's input selector.
- Try a different audio cable.

**Bluetooth audio is delayed or choppy**
- Move the device closer to the speaker.
- Avoid 2.4 GHz Wi-Fi congestion (Bluetooth shares the band).
- Disable other Bluetooth devices nearby.

**`.lgt` won't load**
- Make sure the file wasn't renamed to `.txt`.
- Try `Load` in Chrome (Safari sometimes blocks the picker).


**"Folder picker not supported in this browser"**
You're on Firefox or Safari. Switch to Chrome, Edge, Opera, or Brave.

---

## 🔒 Privacy

- The app runs **100% offline** in your browser.
- No audio is uploaded anywhere.
- The only network request is the optional Google Forms iframe in the email modal.
- The `.lgt` file is a plain text file you control — nothing phones home.
- `localStorage` is used only to remember whether you've submitted the email form.

---

## 📄 License

MIT License — see `LICENSE` file.

You're free to use, modify, and redistribute this software, including for commercial escape room installs, as long as you keep the copyright notice.

---

## 🙏 Credits

- **Author:** [LogicTech](https://logictech.neocities.org)
- **Email:** logictechgreece@gmail.com
- **Phone:** +30 694 771 4420
- **Fonts:** [Space Mono](https://fonts.google.com/specimen/Space+Mono) & [Rajdhani](https://fonts.google.com/specimen/Rajdhani) via Google Fonts
- **Icons:** Native Unicode emoji — no icon library required

---

<p align="center">
  Built for escape rooms, theatre cues, and every place where the music has to change on cue.
  <br>
  <strong>🎧 Set the folder. Add your files. Press play.</strong>
</p>
```
