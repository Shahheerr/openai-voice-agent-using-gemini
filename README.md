# OpenAI Voice Agent using Gemini

This repository demonstrates a minimal voice agent built with Gemini (via the OpenAI Agents SDK). The agent listens to your microphone, sends audio to the Gemini model, and speaks back responses. It's a lightweight example to show how to wire up OpenAI Agents SDK voice features, record audio, and run an agent loop locally.

Project repo: https://github.com/Shahheerr/openai-voice-agent-using-gemini

## Features
- Microphone recording and audio playback
- Integration with Gemini models using the OpenAI Agents SDK
- Simple configuration via environment variables

## Requirements
- Python 3.13 or newer
- A Gemini-enabled OpenAI API key and (optional) a custom base URL

Dependencies are declared in `pyproject.toml`. Key dependencies include:
- openai (official OpenAI client)
- openai-agents[voice]
- sounddevice / pyaudio (for microphone I/O)
- python-decouple (for environment configuration)

## Quickstart

1. Clone the repository

2. Create a virtual environment and install dependencies

3. Set environment variables

4. Run the voice agent

Example (Windows PowerShell):

```powershell
git clone https://github.com/Shahheerr/openai-voice-agent-using-gemini.git
cd "openai-voice-agent-using-gemini\voice-agent"
python -m venv .venv; .\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -e .
# or: pip install -r requirements.txt if you generate one

# Set environment variables (PowerShell)
$env:GEMINI_API_KEY = 'your_api_key_here'
$env:GEMINI_BASE_URL = 'https://api.openai.com/v1'  # optional; set if you use a custom endpoint

# Run the agent
python run_voice_agent.py
```

Notes:
- The project uses `configuration/gemini_config.py` to configure the OpenAI / Gemini client. It reads `GEMINI_API_KEY` and `GEMINI_BASE_URL` from the environment.
- The example `pyproject.toml` pins `openai-agents[voice]` which exposes the voice helpers used by the code.

## Configuration

Edit or override `configuration/gemini_config.py` if you need a different model or run settings. By default it configures the agent to use `gemini-2.5-flash` via an async OpenAI client.

Environment variables expected:
- GEMINI_API_KEY - Your OpenAI/Gemini API key
- GEMINI_BASE_URL - Optional base URL for custom endpoints

## File overview
- `run_voice_agent.py` — entrypoint to start the voice agent loop
- `agent_voice.py` — main agent implementation and orchestration
- `recorder.py` — microphone recording helpers
- `configuration/gemini_config.py` — Gemini/OpenAI client and model configuration

Open the files to learn how audio is captured, encoded, and sent to the agent using the OpenAI Agents SDK voice integrations.

## Troubleshooting
- Microphone not detected: ensure your OS allows apps to access the microphone and the correct input device is selected. Try `sounddevice` examples or `pyaudio` utilities to verify.
- Permissions/driver issues on Windows with `pyaudio`: install the wheel matching your Python version or use `sounddevice` (which may work without PyAudio).
- API authentication errors: confirm `GEMINI_API_KEY` is set and valid.
- Model or API errors: check `GEMINI_BASE_URL` if you're routing through a proxy or private endpoint.

## Security notes
- Keep your API keys secret. Do not commit them to version control.

## Contributing
Pull requests are welcome. Open an issue if you want guidance or find a bug.

## License
This repo doesn't include an explicit license file. Add one if you want to grant permissions for reuse.

---

If you'd like, I can also:
- add a `requirements.txt` for easier install on Windows,
- add a short usage demo script or unit test, or
- expand the README with screenshots and sample audio clips.
