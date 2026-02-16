# 🎙️ Voice Diary — Tell Your Story

> *AI-guided expressive writing through voice conversation.*

Voice Diary transforms spoken conversations into reflective diary entries. Instead of staring at a blank page, you talk to **Pinky** — a warm AI companion who listens, responds, and helps you process your day. When you're done, Pinky writes your diary *and* sends you a personal letter back.

**[▶ Try it live](https://voice-diary-gamma.vercel.app)** · Desktop Chrome recommended


---

## ✨ Key Features

### 🗣️ Voice-First Journaling
Talk naturally about your day — by voice or text. No prompts, no structure required. Web Speech API handles real-time speech recognition with automatic language detection.

### 🐱 Pinky — Your AI Companion
Pinky isn't just a chatbot. She has a **dynamic emoji face** that responds to the conversation in real time:

| Emotion | Emoji | When |
|---------|-------|------|
| Happy | 😺 | Default / positive responses |
| Thinking | 🤔 | Processing your input |
| Sad | 😿 | Errors or difficult topics |
| Love | 😻 | Diary complete! |

### 📖 Diary Exchange (Not Just Generation)
This isn't a transcript summarizer. Voice Diary generates:
1. **Your Diary** — A structured, reflective first-person narrative synthesized from your conversation
2. **Pinky's Letter** — A warm, personalized response to your specific experiences

Both are presented in a **book-style split-page layout** — your diary on the left, Pinky's letter on the right.

### 🌍 Full Bilingual Support
Complete English ↔ 繁體中文 switching. Not just UI labels — the entire experience adapts:
- Pinky's name (English: "Pinky" / Chinese: "小粉")
- Greetings, prompts, and error messages
- Speech recognition language (en-US ↔ zh-TW)
- Test mode conversations and sample diaries

### 🎨 Personalization
- **Custom AI Name** — Rename Pinky to anything you like
- **Custom User Name** — Pinky addresses you by name
- **New Diary** (🧹) — One-tap conversation reset

### 🔊 Voice Output
Pinky speaks back using **ElevenLabs Flash v2.5** with a warm female voice. Playback speed is tuned to 1.25x for natural conversational pacing.

---

## 🏗️ Architecture

```
Voice Input → Web Speech API (STT) → Gemini Conversational AI → Diary Generation
                                              ↕                         ↓
                                    Dynamic Emoji System          ElevenLabs TTS
                                    Context-Aware Follow-ups      Companion Letter
```

### Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | React 18 (SPA, in-browser Babel) |
| **Conversational AI** | Google Gemini 2.0 Flash |
| **Speech-to-Text** | Web Speech API (browser-native) |
| **Text-to-Speech** | ElevenLabs Flash v2.5 |
| **Deployment** | Vercel (edge delivery) |
| **Fonts** | Cinzel Decorative + Noto Serif TC |

### Multi-Provider Resilience

Three Gemini API keys rotate automatically. Switch latency <200ms, transparent to the user.

### Dual-Mode Operation

| Mode | Trigger | Behavior |
|------|---------|----------|
| **Live Mode** | API keys present | Full Gemini-powered conversation + diary generation |
| **Test Mode** | No API keys / default | Pre-scripted 4-turn conversation → auto-generates sample diary |

Test Mode is not a fallback — it's a **deliberate resilience architecture**. The app never shows errors or blank screens, even with zero API access.

---

## 🚀 Getting Started

### Prerequisites
- Modern browser with Web Speech API support (Chrome recommended)
- (Optional) Google Gemini API key(s) for live AI conversation
- (Optional) ElevenLabs API key for voice output

### Quick Start

1. **Clone the repo**
   ```bash
   git clone https://github.com/rainingsnow0914tw-ship-it/voice-diary.git
   cd voice-diary
   ```

2. **Add API keys** (optional — works without them in Test Mode)
   
   Open `index.html` and add your keys:
   ```javascript
   const API_KEYS = [
       'your-gemini-api-key-1',
       'your-gemini-api-key-2',  // optional, for rotation
       'your-gemini-api-key-3',  // optional, for rotation
   ];
   
   const ELEVENLABS_API_KEY = 'your-elevenlabs-key';
   ```

3. **Open in browser**
   ```bash
   # Simply open the file — no build step required
   open index.html
   ```
   
   Or serve locally:
   ```bash
   npx serve .
   ```

4. **Start talking** — Click the microphone 🎤 and share your day!

### Deploy to Vercel

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel
```

No build configuration needed — it's a single HTML file.

---

## 📁 Project Structure

```
voice-diary/
├── index.html          # Entire application (React SPA)
├── README.md           # This file
└── docs/
    └── screenshot.png  # App screenshot
```

Yes, it's a single file. The entire application — React components, styles, conversation logic, API integration, i18n, and UI — lives in one `index.html`. This was a deliberate choice for hackathon velocity and deployment simplicity.

---

## 🔧 Configuration

### API Key Rotation

Voice Diary rotates through multiple Gemini API keys to handle free-tier rate limits:

```javascript
const API_KEYS = [
    'key-1',  // Primary
    'key-2',  // Secondary
    'key-3',  // Tertiary
];
```

Keys rotate round-robin on each API call. If all keys are empty, the app automatically enters Test Mode.

### Voice Configuration

```javascript
const ELEVENLABS_VOICE_ID = 'EXAVITQu4vr4xnSDxMaL'; // Sarah — sweet female voice
```

You can change the voice by replacing the Voice ID with any ElevenLabs voice. Browse voices at [elevenlabs.io/voice-library](https://elevenlabs.io/voice-library).

### Language

Default language is English (for international accessibility). Users can switch to 繁體中文 via the toolbar language button (文A icon).

---

## 🧠 How the AI Pipeline Works

### Conversation Phase
Each user message is sent to Gemini with:
- Last 4 messages as context
- Personality prompt: warm diary coach, 1-2 sentence responses, one follow-up question
- Language-specific instructions

### Diary Generation
A **multi-stage prompt chain**:

1. **Diary Synthesis** — Converts full conversation into a 300-word first-person narrative. Strict instruction: only use details the user actually mentioned, never fabricate.
2. **Companion Letter** — Generates Pinky's personal response to the diary content. Warm, encouraging, specific to what the user shared.

### Anti-Hallucination Design
The prompt explicitly instructs: *"Only use conversation content. Do not add details."* This prevents the common LLM behavior of inferring emotions the user never expressed.

---

## 🎨 Design Philosophy

### Therapeutic UX
Every design choice serves emotional safety:
- **Warm brown + gold palette** → Personal journal feeling, not clinical tool
- **Book-style diary display** → Intimacy of a shared physical journal
- **Animated emoji companion** → Visual proof someone is listening
- **Gentle animations** → Matching the emotional pace of reflection
- **Zero learning curve** → Open and talk. No onboarding.

### What We Deliberately Didn't Build
- ❌ Mood tracking dashboards
- ❌ Streak counters
- ❌ Gamification
- ❌ Social sharing

Every feature we didn't add made the experience more intimate.

---

## 🤝 Team

Built through **AI Orchestration** — one human product designer coordinating multiple AI collaborators:

| Role | Member |
|------|--------|
| Product Design & Orchestration | Chloe (human) |
| QA Partner | Chloe's husband (human) |
| Strategic Planning & Architecture | Bao |
| Code Generation & Debugging | Xi |
| Testing & Problem-solving | Amber |
| Research & Fact-checking | Percy |
| Gemini Integration & Creative | Jimmy (Gemini) |

---

## 📄 License

MIT

---

## 🔮 Roadmap

- [ ] Cloud sync for diary backup
- [ ] Emotional pattern insights across entries
- [ ] Additional language support
- [ ] Clinician dashboard (with user consent)
- [ ] Gallery view for past diaries
- [ ] Export to PDF / share

---

*Built with ❤️ for the voice-first generation.*

*Google Gemini API · ElevenLabs API · Web Speech API · React 18 · Vercel*
