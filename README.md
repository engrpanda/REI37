# REI37 — AI Companion

REI37 is an Android app: a stateful AI companion with a real personality, an
animated orb face with 16 emotions that reacts to both your question and his
own answer, long-term memory, voice in/out, a customizable hands-free wake
word, document learning, a floating on-screen buddy, screen-control
automation, a catalog of assistant/device/data features, and real smart-home
(ESP32) control over Wi-Fi.

He can think three ways: a built-in offline rule-based brain (no setup), a
real LLM downloaded and run **fully on your device** (Offline AI), or any of
nine online AI providers (Online AI) — switchable any time, side by side.

Everything you teach him is stored **on your device**. Your chat history,
memory, and location never leave your phone unless you turn Online AI on,
and even then only the message text is sent to your chosen provider.

- **Package:** `com.rei37.app`
- **Min Android:** 8.0 (API 26) · **Target:** 14 (API 34)
- **Repo:** https://github.com/engrpanda/REI37

### 📥 Download

**[Get the latest APK from Releases →](https://github.com/engrpanda/REI37/releases)**

---

## Table of contents
1. [What REI37 can do](#what-rei37-can-do)
2. [First run](#first-run)
3. [Talking to REI37](#talking-to-rei37)
4. [Voice: wake word, always listening, barge-in](#voice-wake-word-always-listening-barge-in)
5. [The three AI brains](#the-three-ai-brains)
6. [Offline AI — Manage models](#offline-ai--manage-models)
7. [Connecting an Online AI](#connecting-an-online-ai)
8. [Memory & documents](#memory--documents)
9. [Screen buddy & screen control](#screen-buddy--screen-control)
10. [More features (the Store)](#more-features-the-store)
11. [Smart home (ESP32)](#smart-home-esp32)
12. [Settings screen](#settings-screen)
13. [Quick commands](#quick-commands)
14. [Privacy](#privacy)
15. [Troubleshooting](#troubleshooting)
16. [License](#license)

---

## What REI37 can do

**Conversation & personality**
- Chats with a consistent, chosen personality (Friendly, Professional, Teacher, Character, or Emotionally aware)
- 16 facial emotions + natural blinking on an animated OpenGL orb; reacts to both what you say and what he's about to say
- Tap his body to cycle emotions by hand, or drive them with mood slash-commands
- Long-term memory that survives app restarts, with an editable "Your profile" card (name, age range, address, persona)
- Learns from your documents — import PDF, Word (`.docx`), `.txt`, `.md`, or `.csv` files and he answers from them

**Voice**
- Speech-to-text input and text-to-speech output, using your phone's free built-in voices
- Adjustable voice, pitch, speed, and listening (silence) timeout
- Hands-free wake word — default "hey REI37" / "hi Ray", or set your own custom phrase
- **Always listening** mode — skip the wake word entirely
- Experimental **barge-in** ("Interrupt me") — stop his reply the moment you start talking

**On-screen presence**
- A large, highlighted orb avatar on the home screen, with a "Summon me" switch right next to his name
- **Screen buddy** — flip that switch and he leaves the chat to float on top of every app as a draggable, tappable sprite
- **Screen control** — with Accessibility permission granted, he can tap and type inside other apps on your behalf

**Three AI brains**
- **Local brain** (default): built-in, rule-based, fully offline, zero setup
- **Offline AI**: a real LLM (Gemma, Qwen, Phi, SmolLM, FunctionGemma, …) downloaded once and run entirely on-device via llama.cpp / MediaPipe / LiteRT-LM — no internet needed afterward
- **Online AI**: nine cloud providers, several free with no card

**More features (catalog)**
- Assistant skills: alarms, calendar/morning briefing, calls & texts, opening apps, YouTube/Spotify, email, notes, ride-hailing, camera
- Device controls: Wi-Fi/flashlight/brightness toggles
- Tools: navigation, speed test, storage info, battery info
- Philippines live data: weather (PAGASA-credited), news (ABS-CBN by default), currency, fuel prices, earthquakes, volcano activity
- Safety: an offline emergency hotline directory
- Personalization: voice picker

**Smart home & extras**
- Real IoT control of ESP32 devices on your local Wi-Fi (on/off, read a sensor)
- Chat history with multiple saved sessions
- A home-screen widget for quick access
- A daily morning briefing notification (calendar + weather) at a time you choose
- Light / dark / system theme

---

## First run

1. **Onboarding** walks through: intro → your name → location/age (optional,
   can use GPS or type it in) → persona → an AI-setup choice (**Online AI**,
   recommended for fast setup with a free API key; or **Offline AI**, slower
   but fully private, needing a model download; or decide later).
2. Onboarding finishes by opening **More features**, so you can enable or
   disable each feature (with **Select all** requesting every needed
   permission in one batch) before you start chatting.
3. You land on the home screen: a big highlighted orb, a status pill showing
   which AI brain is active, and the chat below it.

---

## Talking to REI37

- Type in the box at the bottom and send, **or** tap the mic and talk — his
  eyes widen while he listens.
- He replies in chat and, if voice is on, speaks the reply aloud — his
  expression reacts to both your message and his own reply.
- Teach him facts naturally: "my name is …", "I live in …", "remember that …".
- Ask them back: "what's my name?", "where do I live?".
- Tap his body to cycle emotions, or use mood commands like `/happy`, `/sad`.
- Flip the **"Summon me"** switch beside his name to send him out as a
  floating screen buddy instead (see [below](#screen-buddy--screen-control)).

---

## Voice: wake word, always listening, barge-in

All under **Settings ▸ Voice & AI**:

- **Wake word** — turn it on and grant mic permission; say "hey REI37" (or
  "hey rei", "hi Ray", and similar pronunciations) while the app is open.
  You can say the whole request in one breath: "hey rei, what's the weather?".
- **Wake word phrase** — type your own custom phrase instead of the default;
  leave it blank to keep the built-in fuzzy "hey REI37 / hi Ray" detection.
- **Always listening** — skips the wake phrase entirely; anything the mic
  hears while the wake loop is active is treated as a command directly.
- **Interrupt me (experimental)** — while he's talking, the mic stays open;
  any speech immediately stops his reply and becomes your next message.
  ⚠️ This can pick up his own voice from the speaker (no echo cancellation on
  this audio path), so it's far more reliable with headphones/earbuds than
  over the speaker.
- **Voice & speech** (its own screen) — pick a TTS voice, tune pitch/speed,
  and set the listening (silence) timeout, 2–30 seconds.

Notes: the wake loop works while the app (or the screen buddy) is running in
the foreground — true background hotword detection would need a dedicated
hotword engine and always-on foreground service. It uses the mic continuously
while on, so it costs some battery.

---

## The three AI brains

Switch any time from the home screen's AI-source picker (tap the status
badge under REI37's name) or from Settings:

| Brain | Setup | Internet | Notes |
|---|---|---|---|
| **Local** | None | No | Built-in rule-based mock brain, always available, simple replies |
| **Offline AI** | Download a model once | No (after download) | Real LLM, runs fully on-device, needs storage + a capable phone |
| **Online AI** | Paste a free/paid API key | Yes | Nine providers, generally the smartest/fastest replies |

If Online AI is busy/over quota, or Offline AI takes too long, REI37 quietly
falls back to the local brain and says so.

---

## Offline AI — Manage models

**Settings ▸ Offline AI ▸ Manage models** lists every downloadable on-device
model, grouped into two sections:

- **✅ Ready to download — no sign-in needed:** community re-uploads of
  Gemma 3 (270M/1B/4B) and Gemma 3n (E2B/E4B), Qwen 2.5 (1.5B/3B) and Qwen3
  0.6B, Phi-3.5 Mini, and SmolLM 135M — all in formats the bundled engines
  (llama.cpp / MediaPipe / LiteRT-LM) run directly.
- **🔑 Requires a Hugging Face token:** currently just **FunctionGemma 270M
  Mobile Actions** (a function-calling model, not a chat model), since its
  repo is gate-locked on Hugging Face. Paste a free token from
  [huggingface.co/settings/tokens](https://huggingface.co/settings/tokens)
  under "Hugging Face token", and accept that model's license on its
  Hugging Face page first — the token alone doesn't bypass license acceptance.

Each entry shows its quantization, approximate size, a speed/quality rating
out of 10, and a device-fit tip (✅ good fit / 🟡 slow / 🟠 risky / ⛔ too big)
computed from your phone's RAM and free storage. **Download**, then **Load**
to bring it into memory — **Unload** frees the RAM back up. Downloads can be
**paused and resumed**. You can also **Import a local model file**
(`.gguf` / `.task` / `.litertlm`) if you already have one on your device.
A **Debug log** screen helps diagnose a model that fails to load.

---

## Connecting an Online AI

**Settings ▸ Online AI** — you add the key right in the app, no rebuild needed.

1. Tap **Provider** and pick one.
2. Tap **Setup instructions**, then **Get a free key** to open that
   provider's signup page.
3. Paste the key into the API key field. Optionally set a model override
   (leave blank for the sensible default).
4. Tap **Save**, then **Test** to confirm it works — a successful test turns
   on the Cloud AI switch automatically.
5. The home-screen badge switches to `<provider> — online`.

| Provider | Cost | Notes |
|---|---|---|
| OpenRouter | Free models available (`:free` suffix) | Wide model selection |
| Groq | Free tier, no card | Very fast |
| Google Gemini | Free tier, no card | |
| xAI (Grok) | Free signup credits | |
| OpenAI (ChatGPT) | Paid | Sometimes trial credit |
| Anthropic (Claude) | Paid | May include trial credit |
| Moonshot (Kimi) | Low cost | |
| DeepSeek | Very low cost | |
| Meta Llama API | Free preview | May need access approval |

Per-provider usage/limits are shown in **Settings ▸ Online AI ▸ Usage**.
Switch providers any time — each one's key is remembered separately.

---

## Memory & documents

Open the drawer ▸ **Memory** to see everything REI37 knows:

- A **"Your profile"** card up top — name, age range, address/area, and
  persona, each tap-to-edit directly, separate from the general facts list.
- **Saved facts** — things you taught him, or he picked up naturally from
  conversation — remove any with the ✕.
- **Imported documents**, each showing its section count — remove a file
  with ✕.

**Import a document**: Memory ▸ **Import a document**, pick a PDF/Word/text
file. He extracts the text, splits it into sections, and saves them —
related questions later pull the relevant sections into his answer
automatically. (Scanned/image-only PDFs have no extractable text.)

**Two ways to clear:**
- **Clear chat** — removes only the recent conversation; saved facts and
  documents are kept.
- **Forget everything** — wipes facts, documents, chat, and your profile
  permanently, and takes you back through first-time setup.

---

## Screen buddy & screen control

Both live in **Settings ▸ Screen & Automation** (and Screen buddy also has a
quick switch — "Summon me" — right next to REI37's name on the home screen):

- **Screen buddy**: he leaves the chat screen and floats on top of every app
  as a small animated, draggable sprite — tap to change his mood, double-tap
  to talk to him hands-free. His in-app avatar hides while he's out there so
  he's never shown twice. Needs the "draw over other apps" permission
  (Android prompts you), and on Android 13+, a notification permission for
  the persistent control.
- **Screen control**: with this on, REI37 can tap and type inside *other*
  apps for you (e.g. "open Facebook and search cats"), using Android's
  Accessibility service. Turning it on sends you to system Accessibility
  settings to grant it manually — Android requires this for any app that can
  act on your behalf on-screen.

---

## More features (the Store)

Open the drawer ▸ **More features** for a searchable, category-grouped,
4-column grid of everything REI37 can do beyond chat:

| Category | Examples |
|---|---|
| Assistant skills | Alarm, morning briefing (calendar), direct call/text, open apps, YouTube/Spotify default app, email, notes, ride-hailing, camera, persona |
| Device controls | Wi-Fi/flashlight/brightness toggles |
| Tools & diagnostics | Navigation, speed test, storage info, battery info |
| Philippines live data | Weather, news, currency, fuel prices, earthquakes, volcano activity |
| Safety | Offline emergency hotline directory |
| Personalize | Voice picker |

Tap a feature for its description, an example command, and an **Enable**
button; some request a runtime permission the first time (contacts for
calls/texts, location for navigation, camera permission, etc.). **Select
all / Deselect all** act on whatever the current search + category filter
shows, and request every permission those visible features need in one
combined batch rather than one at a time. This screen also opens
automatically at the end of first-time setup.

---

## Smart home (ESP32)

Control ESP32 devices (lights, fans, sensors) on your Wi-Fi.

**Set up** (Settings ▸ Smart Home ▸ ESP32 devices):
1. Wire your device (relay/LED/sensor) to an ESP32.
2. In Arduino IDE, install the ESP32 board package and open
   `esp32/rei37_esp32.ino`.
3. Put your Wi-Fi name + password in the sketch and flash the board.
4. Open Serial Monitor at 115200 baud and note the IP it prints
   (e.g. `192.168.1.50`).
5. Put your **phone on the same Wi-Fi** as the ESP32.
6. Add the device with a friendly name + that IP, then **Save & test**.
7. Say/type: "turn on the light", "what's the temperature".

**HTTP command protocol** (what the sketch implements):
```
Turn on:      GET /cmd?action=turn_on&device=NAME
Turn off:     GET /cmd?action=turn_off&device=NAME
Read sensor:  GET /sensor?device=NAME
```
The board can reply with any HTTP 200 (plain text is fine).

You can also manage devices from chat: `/device add light 192.168.1.50`,
`/device list`, `/device remove light`.

---

## Settings screen

Settings opens to a **category grid** (Help & About, Appearance, Voice & AI,
Offline AI, Response Timeout, Online AI, Memory, Screen & Automation, Smart
Home, Privacy & Data, About) — tap a tile to open that section in place; the
toolbar back arrow (or system back) returns to the grid instead of closing
Settings. Toggle switches inside each section stay as full-width rows;
navigation-only rows are compact tiles. Sliders and the API-key form are the
one exception to the grid, since a slider or text field needs real width to
be usable.

---

## Quick commands

Type any of these in the chat box:
```
/help                     show all commands
/happy /sad /angry ...    set a mood
/memories                 list what he remembers
/forget                   wipe his memory
/voice                    turn speaking on/off
/device add light 1.2.3.4 add an ESP32 device
/device list              show your devices
/device remove light      remove one
```

---

## Privacy

- All data is stored locally in a private app database (`rei37_memory.db`)
  plus app preferences. Nothing is uploaded to any server by default — chat
  history, saved facts, and your location never leave your phone.
- **Offline AI** models run entirely on-device once downloaded; nothing is
  sent anywhere for them to work. The screen buddy and screen control
  automation also run entirely on-device.
- **Clear chat** keeps your memory; **Forget everything** deletes it
  permanently and restarts onboarding.
- **Settings ▸ Privacy & Data** also has **Export data** (saves a text file
  of your profile + memories to app-specific storage) and a crash-log viewer.
- When **Online AI (Cloud)** is ON, only the text of that conversation is
  sent to the chosen provider to generate a reply — your stored memory is
  never uploaded.

---

## Troubleshooting

- **"Offline — built-in brain" won't change** — add a key under Settings ▸
  Online AI ▸ Provider and run **Test**, or load a model under Settings ▸
  Offline AI ▸ Manage models.
- **Online AI test fails** — check the key is in the API key field (not the
  model box), and that the provider has quota/credit.
- **Offline AI model won't load** — check Settings ▸ Offline AI ▸ Manage
  models ▸ Debug log; confirm the device-fit tip isn't ⛔ for that model.
- **Voice input does nothing** — most phones need internet (Google speech)
  plus mic permission granted.
- **Interrupt me keeps triggering itself** — expected on speaker audio (no
  echo cancellation); use headphones/earbuds, or turn it off.
- **Screen buddy switch won't stay on** — grant the "draw over other apps"
  permission when prompted, and (Android 13+) the notification permission.
- **Screen control does nothing** — it needs to be granted manually in
  system Accessibility settings; the toggle only opens that screen for you.
- **ESP32 won't connect** — phone and board must be on the **same Wi-Fi**;
  confirm the IP from Serial Monitor; try the device's URL in a browser.

---

## License

**[Creative Commons Attribution-NonCommercial 4.0 International](LICENSE) (CC BY-NC 4.0)**

You're free to download, use, and share REI37 for **non-commercial purposes**,
as long as you give credit and link back to this license. **Selling it, or
charging for access to it, is not allowed.** See the [LICENSE](LICENSE) file
for the full terms.

---

Made by **@engrpanda** — https://github.com/engrpanda/REI37
