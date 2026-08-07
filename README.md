<div align="center">

# 🤖 REI37 — AI Companion

**A stateful AI companion for Android — real personality, 16 emotions, long-term memory, voice, a floating screen buddy, recordable macros, and real smart-home control.**

[![Status: Beta](https://img.shields.io/badge/status-beta-red.svg)](#-beta-status)
[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Android-3DDC84?logo=android&logoColor=white)](#)
[![Min SDK](https://img.shields.io/badge/Min%20Android-8.0%20(API%2026)-blue)](#)
[![Latest release](https://img.shields.io/github/v/release/engrpanda/REI37?include_prereleases&label=latest%20release&color=orange)](https://github.com/engrpanda/REI37/releases)
[![Downloads](https://img.shields.io/github/downloads/engrpanda/REI37/total?label=downloads&color=success)](https://github.com/engrpanda/REI37/releases)

### 📥 [**Download the latest APK →**](https://github.com/engrpanda/REI37/releases)

</div>

---

## 🧪 Beta status

**REI37 is still in beta (`0.1.1-beta`) and needs more real-world testing.**
Most features work as described below, but with this many moving parts —
on-device AI models, screen automation, background alert polling, several
third-party API integrations — expect rough edges: an occasional crash, a
feature that behaves differently on your specific phone/OEM skin, or a
description that's slightly ahead of (or behind) what's actually implemented.

If something breaks, behaves oddly, or just doesn't match what this README
says, please [open an issue](https://github.com/engrpanda/REI37/issues) with
your device model, Android version, and what you were doing — that's exactly
the kind of feedback this beta needs. Screen control/macro features in
particular are accessibility-based and OEM camera/UI layouts vary a lot, so
real-device reports are the only way those get more reliable.

---

## 📲 Installing: about the Play Protect warning

When you try to install the APK, Google Play Protect will very likely show
**"App blocked to protect your device."** This is expected — it's not a sign
anything's wrong with the app. Play Protect's on-device scanner flags any
brand-new APK from outside the Play Store that requests sensitive
permissions (Screen Control's Accessibility service, direct SMS/calls,
notification access, drawing over other apps), no matter what it actually
does with them, because that exact combination is also common in malware.
Since REI37 isn't listed on Google Play, it has no install history yet for
Play Protect to trust.

**To install anyway:**
1. Open the **Play Store** app.
2. Tap your **profile icon** (top right) ▸ **Play Protect**.
3. Tap the **settings gear** icon (top right of that screen).
4. Turn **off** "Scan apps with Play Protect."
5. Install the REI37 APK — the warning should be gone.
6. **Turn "Scan apps with Play Protect" back on afterward.** You only need
   it off for this one install, and it's genuinely useful protection for
   everything else on your phone.

Exact wording/steps vary a little by Android version and phone brand, but
it's always under Play Store ▸ your profile ▸ **Play Protect**.

Would rather not disable it at all? You can instead
[report this specific warning as a false positive to Google](https://support.google.com/faqs/answer/9313070)
— free, no Play Store listing required, just not immediate or guaranteed.

---

REI37 is an Android app: a stateful AI companion with a real personality, an
animated orb face with 16 emotions that reacts to both your question and his
own answer, long-term memory, voice in/out, a customizable hands-free wake
word, document learning, a floating on-screen buddy, screen-control
automation (including recordable macros), condition-triggered automation and
saved workflows, a catalog of assistant/device/data features, and real
smart-home control over Wi-Fi (ESP32 or Home Assistant).

He can think three ways: a built-in offline rule-based brain (no setup), a
real LLM downloaded and run **fully on your device** (Offline AI), or any of
14 online AI providers plus Ollama and any custom OpenAI-compatible endpoint
(Online AI) — switchable any time, side by side.

Everything you teach him is stored **on your device**. Your chat history,
memory, and location never leave your phone unless you turn Online AI on,
and even then only the message text (or a screenshot, for Vision) is sent to
your chosen provider.

<div align="center">

| | |
|---|---|
| 📦 **Package** | `com.rei37.app` |
| 📱 **Min Android** | 8.0 (API 26) · **Target:** 14 (API 34) |
| 🔗 **Repo** | [github.com/engrpanda/REI37](https://github.com/engrpanda/REI37) |

</div>

---

## 📋 Table of contents
1. [🧪 Beta status](#-beta-status)
2. [📲 Installing: about the Play Protect warning](#-installing-about-the-play-protect-warning)
3. [✨ What REI37 can do](#-what-rei37-can-do)
4. [🚀 First run](#-first-run)
5. [💬 Talking to REI37](#-talking-to-rei37)
6. [🎙️ Voice: wake word, always listening, barge-in](#️-voice-wake-word-always-listening-barge-in)
7. [🧠 The three AI brains](#-the-three-ai-brains)
8. [📦 Offline AI — Manage models](#-offline-ai--manage-models)
9. [☁️ Connecting an Online AI](#️-connecting-an-online-ai)
10. [🗂️ Memory & documents](#️-memory--documents)
11. [🕹️ Screen buddy, screen control & macros](#️-screen-buddy-screen-control--macros)
12. [⚙️ Automation: rules & saved workflows](#️-automation-rules--saved-workflows)
13. [💬 Notification auto-reply](#-notification-auto-reply)
14. [🛍️ More features (the Store)](#️-more-features-the-store)
15. [🏠 Smart home: ESP32 & Home Assistant](#-smart-home-esp32--home-assistant)
16. [🇵🇭 Philippines live data & alerts](#-philippines-live-data--alerts)
17. [⚙️ Settings screen](#️-settings-screen)
18. [⌨️ Quick commands](#️-quick-commands)
19. [🔒 Privacy](#-privacy)
20. [🛠️ Troubleshooting](#-troubleshooting)
21. [📄 License](#-license)

---

## ✨ What REI37 can do

**Conversation & personality**
- Chats with a consistent, chosen personality (Friendly, Professional, Teacher, Character, or Emotionally aware)
- 16 facial emotions + natural blinking on an animated OpenGL orb; reacts to both what you say and what he's about to say
- Tap his body to cycle emotions by hand, or drive them with mood slash-commands
- Long-term memory that survives app restarts, with an editable "Your profile" card (name, age range, address, persona)
- Learns from your documents — import PDF, Word (`.docx`), `.txt`, `.md`, or `.csv` files and he answers from them
- Encrypted memory export/import, protected by a passphrase you choose, for moving your saved facts and documents to a new phone
- "On this day" recall — every so often, an older saved fact or preference resurfaces in the morning briefing

**Voice**
- Speech-to-text input and text-to-speech output, using your phone's free built-in voices
- Adjustable voice, pitch, speed, and listening (silence) timeout
- Hands-free wake word — default "hey REI37" / "hi Ray", or set your own custom phrase
- **Always listening** mode — skip the wake word entirely
- Experimental **barge-in** ("Interrupt me") — stop his reply the moment you start talking
- Optional realistic **cloud voice** (ElevenLabs, opt-in), alongside the always-free on-device voice — falls back automatically if it's ever unavailable

**On-screen presence**
- A large, highlighted orb avatar on the home screen, with a "Summon me" switch right next to his name
- **Screen buddy** — flip that switch and he leaves the chat to float on top of every app as a draggable, tappable sprite
- **Screen control** — with Accessibility permission granted, he can tap and type inside other apps on your behalf
- **Vision** — with Screen Control and Online AI both on, he can look at your current screen and describe it or answer a question about it
- **Macro recorder** — record yourself doing something once (open an app, tap, type) and replay it later by name, with optional different typed values each run

**Three AI brains**
- **Local brain** (default): built-in, rule-based, fully offline, zero setup
- **Offline AI**: a real LLM (Gemma, Qwen, Phi, SmolLM, FunctionGemma, …) downloaded once and run entirely on-device via llama.cpp / MediaPipe / LiteRT-LM — no internet needed afterward
- **Online AI**: 14 cloud providers (several free with no card), plus Ollama (your own server) and any custom OpenAI-compatible endpoint

**Automation**
- **Condition-triggered rules** ("when X happens, do Y") — fires on a Wi-Fi connect/disconnect, a battery level threshold, an ESP32 sensor reading, or a calendar event starting soon
- **Saved workflows** — turn a multi-step command into a reusable one, then run, schedule, or list it later; REI37 also offers to save one himself after you repeat the same few-step sequence
- **Macros** — see On-screen presence above
- Optional **automation announcements** — REI37 summons himself and gives a heads-up about a minute before any automation fires, then confirms once it's done

**More features (catalog)**
- Assistant skills: alarms, calendar/morning briefing, calls & texts (with per-contact scheduling), notification auto-reply, opening apps, YouTube/Spotify, email, notes, ride-hailing, camera, persona, macros
- Device controls: Wi-Fi/flashlight/brightness toggles, vision
- Tools: navigation, speed test, storage info, battery info
- Philippines live data: weather (PAGASA-credited), news (ABS-CBN by default), currency, fuel prices, earthquakes, volcano activity, PAGASA weather/cyclone alerts, GDACS-based disaster alerts
- Safety: an offline emergency hotline directory
- Personalization: voice picker, cloud voice (ElevenLabs)

**Smart home & extras**
- Real IoT control of ESP32 devices on your local Wi-Fi (on/off, read a sensor), with devices groupable into rooms so one command controls several at once
- A real **Home Assistant** backend as an alternative to ESP32 — REI37's light/thermostat/lock commands control your actual smart home
- Chat history with multiple saved sessions
- A home-screen widget for quick access
- A daily morning briefing notification (calendar + weather) at a time you choose
- Weather-driven idle mood — his idle face reacts to real storm/heavy-rain conditions where you are
- Light / dark / system theme

---

## 🚀 First run

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

## 💬 Talking to REI37

- Type in the box at the bottom and send, **or** tap the mic and talk — his
  eyes widen while he listens.
- He replies in chat and, if voice is on, speaks the reply aloud — his
  expression reacts to both your message and his own reply.
- Teach him facts naturally: "my name is …", "I live in …", "remember that …".
- Ask them back: "what's my name?", "where do I live?".
- Tap his body to cycle emotions, or use mood commands like `/happy`, `/sad`.
- Flip the **"Summon me"** switch beside his name to send him out as a
  floating screen buddy instead (see [below](#screen-buddy-screen-control--macros)).
- Quick-start suggestion chips appear the first time chat is empty (or after
  "New chat") — real commands you can tap instead of typing.

---

## 🎙️ Voice: wake word, always listening, barge-in

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
- **Cloud voice (opt-in)** — turn on ElevenLabs under More features for a
  more realistic spoken voice; falls back to the free on-device voice
  automatically if it's ever unavailable.

Notes: the wake loop works while the app (or the screen buddy) is running in
the foreground — true background hotword detection would need a dedicated
hotword engine and always-on foreground service. It uses the mic continuously
while on, so it costs some battery.

---

## 🧠 The three AI brains

Switch any time from the home screen's AI-source picker (tap the status
badge under REI37's name) or from Settings:

| Brain | Setup | Internet | Notes |
|---|---|---|---|
| **Local** | None | No | Built-in rule-based mock brain, always available, simple replies |
| **Offline AI** | Download a model once | No (after download) | Real LLM, runs fully on-device, needs storage + a capable phone |
| **Online AI** | Paste a free/paid API key | Yes | 14 providers plus Ollama/Custom, generally the smartest/fastest replies |

If Online AI is busy/over quota, or Offline AI takes too long, REI37 quietly
falls back to the local brain and says so.

---

## 📦 Offline AI — Manage models

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

## ☁️ Connecting an Online AI

**Settings ▸ Online AI** — you add the key right in the app, no rebuild needed.

1. Tap **Provider** and pick one.
2. Tap **Setup instructions**, then **Get a free key** to open that
   provider's signup page. Picking Ollama or Custom instead prompts you for
   its address right away.
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
| Mistral AI | Free experiment tier | |
| Together AI | Several always-free models | |
| Cohere | Free trial key | |
| OpenAI (ChatGPT) | Paid | Sometimes trial credit |
| Anthropic (Claude) | Paid | May include trial credit |
| Moonshot (Kimi) | Low cost | |
| DeepSeek | Very low cost | |
| Meta Llama API | Free preview | May need access approval |
| Ollama | Free | Runs on hardware you already own — enter its LAN address |
| Custom | Depends | Any other OpenAI-compatible endpoint (self-hosted proxy, etc.) |

Per-provider usage/limits are shown in **Settings ▸ Online AI ▸ Usage**.
Switch providers any time — each one's key is remembered separately.

---

## 🗂️ Memory & documents

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

**Encrypted export/import**: Settings ▸ Privacy & Data ▸ Export/Import data,
protected by a passphrase you choose at export time. That passphrase is
never itself stored — losing it means the backup can't be recovered.

---

## 🕹️ Screen buddy, screen control & macros

All in **Settings ▸ Screen & Automation** (Screen buddy also has a quick
switch — "Summon me" — right next to REI37's name on the home screen):

- **Screen buddy**: he leaves the chat screen and floats on top of every app
  as a small animated, draggable sprite — tap to change his mood, double-tap
  to talk to him hands-free, long-press for a menu (open the app, or
  stop/resume his hovering). His in-app avatar hides while he's out there so
  he's never shown twice. Needs the "draw over other apps" permission
  (Android prompts you), and on Android 13+, a notification permission for
  the persistent control.
- **Screen control**: with this on, REI37 can tap and type inside *other*
  apps for you (e.g. "open Facebook and search cats"), using Android's
  Accessibility service. Turning it on sends you to system Accessibility
  settings to grant it manually — Android requires this for any app that can
  act on your behalf on-screen. He never taps or types into a field flagged
  as a password, and stays hands-off on a small denylist of banking/payment
  apps no matter what's asked.
- **Vision**: with Screen Control and Online AI both on, ask "what's on my
  screen" and a screenshot is sent to your chosen provider to describe it or
  answer a question about it.
- **Macro recorder** (More features ▸ Macros): tap **Start Recording**, then
  do something manually — open an app, tap, type — and tap **Stop & Save**
  with a name. REI37 replays it later on request, and since a macro is saved
  as a workflow under the hood, it also works with `/workflow run <name>`
  and can be scheduled from that card's Automate tab. Replay with different
  typed values: `/workflow run <name> :: value :: value`.

---

## ⚙️ Automation: rules & saved workflows

- **Condition-triggered rules**: `/automate add <name> <type> <config> ::
  <command>` fires a saved command when a condition becomes true — a Wi-Fi
  network connecting/disconnecting, a battery level threshold, an ESP32
  sensor reading, or a calendar event starting soon. Checked on a timer
  (~every 15 minutes), not instant push.
- **Saved workflows**: after a multi-step command runs, save it with
  `/workflow save <name>` and run it again later with `/workflow run
  <name>` — list them with `/workflow list`, remove with `/workflow remove
  <name>`. REI37 also offers to save one himself after you repeat the same
  few-step sequence twice.
- **Automation announcements** (Settings toggle): REI37 auto-summons
  himself and speaks a heads-up about a minute before any automation fires,
  then speaks again once it's actually done — so you don't have to be
  watching the chat to know it happened.

---

## 💬 Notification auto-reply

Opt-in and off by default — nothing is read until you turn it on and choose
specific apps.

1. Grant Notification access (More features ▸ Notification auto-reply).
2. Choose which specific apps REI37 is allowed to read notifications from.
3. When an allowed app gets a new message, REI37 waits a few seconds (so a
   manual reply you send in the meantime wins), then drafts and sends a
   short, honest, non-committal reply via that app's own reply action —
   never claiming to know things it doesn't, and rate-limited so it won't
   spam a conversation.
4. Once it's logged a few notifications, ask "what are my notification
   patterns" for your top senders, top apps, and busiest hours.

This needs **Online AI** — there's no offline/local version of the reply
drafting yet.

---

## 🛍️ More features (the Store)

Open the drawer ▸ **More features** for a searchable, category-grouped,
4-column grid of everything REI37 can do beyond chat:

| Category | Examples |
|---|---|
| Assistant skills | Alarm, morning briefing (calendar), direct call/text (with per-contact Automate tab), notification auto-reply, open apps, YouTube/Spotify default app, email, notes, ride-hailing, camera, persona, macros |
| Device controls | Wi-Fi/flashlight/brightness toggles, vision |
| Tools & diagnostics | Navigation, speed test, storage info, battery info |
| Philippines live data | Weather, news, currency, fuel prices, earthquakes, volcano activity, PAGASA alerts, disaster alerts |
| Safety | Offline emergency hotline directory |
| Personalize | Voice picker, cloud voice (ElevenLabs) |

Tap a feature for its description, an example command, and an **Enable**
button; some request a runtime permission the first time (contacts for
calls/texts, location for navigation, camera permission, etc.). **Select
all / Deselect all** act on whatever the current search + category filter
shows, and request every permission those visible features need in one
combined batch rather than one at a time. This screen also opens
automatically at the end of first-time setup.

Send Message and Make Calls each have their own **Automate** tab with one
card per contact: pick straight from your saved Contacts, write that
contact's message, and give it its own independent schedule.

---

## 🏠 Smart home: ESP32 & Home Assistant

**ESP32** — control lights, fans, and sensors on your Wi-Fi.

Set up (Settings ▸ Smart Home ▸ ESP32 devices):
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
`/device list`, `/device remove light`. **Rooms**: tag several devices with
the same room name (`/device room light livingroom`) and one command
controls all of them together.

**Home Assistant** — a real backend alternative to your own ESP32 sketches,
via Home Assistant's local REST API:
```
/homeassistant setup <url> <token>       connect your server
/homeassistant map <alias> <entity_id>   link a friendly name to an entity
```
Once mapped, REI37's light/thermostat/lock commands control your actual
smart home instead of the launch-intent stub. Only accepts a plain `http://`
address for a local host, since the token would otherwise go out
unencrypted.

---

## 🇵🇭 Philippines live data & alerts

Under More features ▸ Philippines live data:

- **Weather, news, currency, fuel prices, earthquakes, volcano activity** —
  quick lookups, e.g. "what's the weather", "any earthquakes".
- **PAGASA Alerts** (opt-in, background notifications): checks PAGASA's
  Weather Advisory and Tropical Cyclone Bulletin pages every ~15 minutes and
  notifies you the moment either one changes. The flood-specific advisory
  isn't covered — PAGASA has no static page or feed for it to poll the same
  way; severe weather that would cause flooding is usually still caught by
  the other two.
- **Disaster Alerts** (opt-in, background notifications): checks GDACS's
  (Global Disaster Alert and Coordination System) public feed every ~15
  minutes and notifies you of a new or updated earthquake, tropical cyclone,
  flood, or volcano alert affecting the Philippines. This exists because
  NDRRMC's own site blocks automated requests (a Cloudflare bot challenge),
  so there's no NDRRMC page or feed this app can poll directly — GDACS
  covers the same hazard types as the closest working alternative.

Both alert types are checked on a timer, not true instant push.

---

## ⚙️ Settings screen

Settings opens to a **category grid** (Help & About, Appearance, Voice & AI,
Offline AI, Response Timeout, Online AI, Memory, Screen & Automation, Smart
Home, Privacy & Data, About) — tap a tile to open that section in place; the
toolbar back arrow (or system back) returns to the grid instead of closing
Settings. Toggle switches inside each section stay as full-width rows;
navigation-only rows are compact tiles. Sliders and the API-key form are the
one exception to the grid, since a slider or text field needs real width to
be usable.

---

## ⌨️ Quick commands

Type any of these in the chat box:
```
/help                              show all commands
/happy /sad /angry /sleepy ...     set a mood
/memories                          list what he remembers
/forget                            wipe his memory
/voice                             turn speaking on or off
/device add light 192.168.1.50     add an ESP32
/device list                       show your devices
/device remove light               remove one
/device room light livingroom      group a device into a room
/workflow save name                save the last plan as a reusable workflow
/workflow run name                 run a saved workflow
/workflow run name :: v :: v       replay with different typed values
/workflow list                     show saved workflows
/workflow remove name              remove one
/automate add name type config :: command   add a "when X happens, do Y" rule
/homeassistant setup url token     connect a Home Assistant server
/homeassistant map alias entityid  link a friendly name to an entity
/macro record                      start recording a manual demo (needs Screen Control)
/macro stop name                   save what you just did as a replayable macro
/macro cancel                      discard the current recording
```

---

## 🔒 Privacy

- All data is stored locally in a private app database (`rei37_memory.db`)
  plus app preferences. Nothing is uploaded to any server by default — chat
  history, saved facts, and your location never leave your phone.
- **Offline AI** models run entirely on-device once downloaded; nothing is
  sent anywhere for them to work. The screen buddy, screen control
  automation, and macro recorder also run entirely on-device.
- **Clear chat** keeps your memory; **Forget everything** deletes it
  permanently and restarts onboarding.
- **Settings ▸ Privacy & Data** also has **Export data** (saves a text file
  of your profile + memories to app-specific storage), encrypted
  export/import, and a crash-log viewer.
- When **Online AI (Cloud)** is ON, only the text of that conversation is
  sent to the chosen provider to generate a reply — your stored memory is
  never uploaded.
- **Vision** (opt-in): a screenshot is sent to your chosen Online AI
  provider only when you ask REI37 to look at your screen.
- **Notification auto-reply** (opt-in, off by default): reads notification
  text only from apps you explicitly allow, and keeps a local log
  (sender/app/time) used solely for rate-limiting and the insights summary.
  A reply's text is sent to your chosen Online AI provider to draft it.
- **Cloud voice** (opt-in): spoken replies are sent as text to ElevenLabs
  instead of using the on-device voice, falling back automatically if that
  ever fails.
- **Home Assistant** (opt-in): its URL and bearer token are stored in
  encrypted on-device storage and sent only to the local server you
  configured — never to any AI provider.
- **PAGASA Alerts / Disaster Alerts** (opt-in): each only reads its own
  public feed on a timer; nothing about you or your location is sent
  anywhere.

---

## 🛠️ Troubleshooting

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
- **Screen control / macros do nothing** — Screen Control needs to be
  granted manually in system Accessibility settings; the toggle only opens
  that screen for you.
- **A recorded macro stops working** — macros identify each tap/field by
  its visible text; if that app's layout changes (an update, a redesign),
  re-record it. This is the same trade-off any accessibility-based
  automation has.
- **PAGASA/Disaster Alerts never fire** — they're checked on a timer
  (~every 15 minutes), not instant push, and only notify when something
  actually changes.
- **ESP32 won't connect** — phone and board must be on the **same Wi-Fi**;
  confirm the IP from Serial Monitor; try the device's URL in a browser.
- **Home Assistant won't connect** — only a plain `http://` local address
  is accepted (not a public HTTPS URL), to keep the token from leaving your
  network unencrypted.

---

## 📄 License

**[Creative Commons Attribution-NonCommercial 4.0 International](LICENSE) (CC BY-NC 4.0)**

You're free to download, use, and share REI37 for **non-commercial purposes**,
as long as you give credit and link back to this license. **Selling it, or
charging for access to it, is not allowed.** See the [LICENSE](LICENSE) file
for the full terms.

---

Made by **@engrpanda** — https://github.com/engrpanda/REI37
