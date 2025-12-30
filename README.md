# 🎧 Voice Diary — AI Voice Journal Coach

> **AI Partner Catalyst Hackathon — ElevenLabs Challenge**

Voice Diary is a voice-first interactive diary coach that helps people turn daily conversations into beautiful journals.

Instead of forcing users to write, Voice Diary listens, asks gentle questions, and transforms spoken memories into:
- 📖 A personal diary entry
- 💌 A warm reflective letter from your AI companion

This project explores how **human voice + guided AI reflection** can create emotional, long-term memory artifacts.

---

## 🌟 The Problem

Many people want to keep a diary, but:
- They don't know how to start writing
- Digital notes feel cold and impersonal
- Physical journals are beautiful but time-consuming
- Typing on phones is tedious

As a result, diary-keeping becomes a burden instead of a healing habit.

---

## 💡 Our Solution

Voice Diary removes the friction. Users simply **talk**.

The AI companion "Pinky":
1. Listens to natural speech
2. Asks gentle follow-up questions to guide reflection
3. Generates a beautifully written diary entry
4. Writes a warm letter back to the user

This creates a full emotional feedback loop — not just recording life, but responding to it.

---

## 🧠 Core Features

| Feature | Description |
|---------|-------------|
| 🎙 **Voice Input** | Real-time speech recognition via Web Speech API |
| 💬 **Guided Conversation** | AI asks thoughtful questions to help you reflect |
| 📖 **Auto Diary Generation** | Transforms conversation into a personal diary |
| 💌 **AI Reflective Letter** | Pinky writes back with encouragement |
| 🐱 **Emotional Companion** | Animated cat mascot shows emotions |
| 🔊 **Voice Output** | Natural text-to-speech responses |
| 🌐 **Multi-language** | English & Traditional Chinese |

---

## 🛠 Tech Stack

### Google Cloud
- **Google Gemini API** — Conversational AI & diary generation

### ElevenLabs
- **ElevenLabs TTS API** — Natural, expressive voice synthesis
- Model: `eleven_flash_v2_5` for low-latency responses

### Frontend
- React 18 (single-file SPA)
- Web Speech API for voice input

---

## 🎮 Demo Mode

The deployed version runs in **Demo Mode** with pre-scripted conversations to ensure a stable experience for reviewers.

**Why Demo Mode?**
- Guarantees consistent functionality regardless of network conditions
- Avoids API quota limitations during evaluation
- Allows reviewers to experience the complete user flow reliably

**Full API Integration:**
The codebase includes complete implementation of:
- Google Gemini API for real-time conversational AI
- ElevenLabs TTS API for natural voice synthesis
- Automatic API key rotation for reliability

To enable live mode, simply set `testMode = false` in the code. The API integration is production-ready.

---

## ▶️ How to Run

This project is a single-file web app.

1. Clone the repository:
   ```bash
   git clone https://github.com/rainingsnow0914tw-ship-it/voice-diary.git
   ```

2. Open `index.html` in your browser

3. (Optional) Replace API keys in the script section:
   ```js
   const GOOGLE_API_KEY = "YOUR_GOOGLE_API_KEY";
   const ELEVENLABS_API_KEY = "YOUR_ELEVENLABS_API_KEY";
   ```

4. Start talking!

---

## 🎯 Use Cases

- People who struggle to start writing
- Emotional self-reflection & mental wellness
- Memory preservation for elders
- Creative journaling enthusiasts
- Human-AI interaction research

---

## 😶‍🌫️ Challenges & Human-AI Collaboration

The most difficult part of this project was not technical — it was human.

I do not come from a programming or IT background, yet I had to coordinate six different AI systems at the same time.

While not fully understanding the code, I still had to debug, evaluate outputs, and guide the collaboration flow between models.  
This meant designing the logic, testing behaviors, and correcting errors purely through reasoning and iteration — not traditional coding.

Another major challenge was producing the demo video.

Editing, storytelling, and translating an emotional experience into a clear two-minute narrative took far more effort than expected.

This project was built at the edge of my comfort zone — technically, emotionally, and creatively.

---

## 🚧 Future Roadmap

- [ ] Diary style customization (tone, length, themes)
- [ ] Cloud sync with Notion
- [ ] Long-term memory tracking
- [ ] Family sharing mode
- [ ] Print-friendly junk journal layouts

---

## 📽 Demo Video

🎬 [Watch on YouTube]([[https://youtu.be/kgTX8wX66qE?si=ZAc9N2YNhJi0TB9U]](https://youtu.be/kgTX8wX66qE?si=ZAc9N2YNhJi0TB9U))

---

## 👥 Team

Built for the **AI Partner Catalyst Hackathon** (ElevenLabs Challenge)

---

## 📄 License

MIT License

Copyright (c) 2025

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

---

## ❤️ Philosophy

> This is not about replacing humans with AI.
> It is about building AI that helps humans remember themselves.

AI should not replace memories — it should protect them.
