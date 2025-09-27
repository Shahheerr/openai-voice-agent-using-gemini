# 🎙️ Voice Agent Project

An **AI-powered voice assistant** built with [OpenAI Agents SDK](https://github.com/openai/agents),  
capable of listening to your **voice input**, processing it with an intelligent agent, and responding back in **natural-sounding speech**.

---

## 📂 Project Structure
voice_agent_project/
│
├── configuration/
│ └── gemini_config.py # model config (e.g., GPT, Gemini)
│
├── recorder.py # handles recording & playback
├── agent_voice.py # agent + voice pipeline
└── run_voice_agent.py # main entry point

---

## ⚡ Features
- Record and playback audio locally  
- Send your voice input to an AI Agent  
- Custom **TTS voice settings** (tone, speed, emotion, personality)  
- Play back AI’s spoken response in real-time  
- Modular design: easy to extend or swap models  

---

## 🚀 Getting Started

### 1️⃣ Clone the repo
```bash
git clone https://github.com/your-username/voice_agent_project.git
cd voice_agent_project
2️⃣ Install dependencies

We use uv for package management:
uv add "openai-agents[voice]==0.1.0" sounddevice numpy matplotlib
3️⃣ Set your API key

Either export it:
export OPENAI_API_KEY="your_api_key_here"
Or enter it securely at runtime when prompted.

4️⃣ Run the project
python run_voice_agent.py

🎛️ Configuration

Model selection is handled via:

# configuration/gemini_config.py
gemini_model = "gpt-4.1-nano"


You can replace "gpt-4.1-nano" with any supported model (e.g. "gpt-4.1", "gemini-pro", etc.).
🧠 Workflow Overview

Recorder → Captures audio chunks from mic

Playback → Plays recorded audio back

Agent → Processes text using OpenAI Agent SDK

Voice Pipeline → Converts AI’s response to voice with custom TTS settings

Speaker → Plays the final AI-generated voice

flowchart LR
    A[🎤 User Voice Input] --> B[📥 Recorder]
    B --> C[🤖 Agent]
    C --> D[🔊 Voice Pipeline]
    D --> E[🎧 Speaker Output]

🎨 Example TTS Settings
custom_tts_settings = TTSModelSettings(
    instructions="""
    Personality: upbeat, friendly, persuasive guide.
    Tone: Friendly, clear, reassuring.
    Tempo: Relatively fast, with natural pauses.
    Emotion: Warm, supportive.
    """
)

💡 Future Improvements

Real-time streaming (continuous conversation)

Multi-agent voice workflows

Web UI for browser-based recording

Save conversations to audio files

📜 License

MIT License © 2025
