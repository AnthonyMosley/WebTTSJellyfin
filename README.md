# Jellyfin Live Subtitle TTS

A browser-based accessibility tool that **reads Jellyfin subtitles out loud in real time**, synced to active playback.

This app was built to help viewers who **can hear audio but struggle to read subtitles**, without requiring audio-described tracks or modifying media files.

It runs entirely in the browser and works with **embedded or external subtitles** managed by Jellyfin (including Bazarr).

---

## ✨ Features

- 🔊 **Live text-to-speech** from Jellyfin subtitles
- ⏱️ **Real-time sync** with playback position
- 🧠 **Automatic sync correction** with manual override
- 🎙️ **Voice selection** (Microsoft voices supported)
- 🚫 Filters out subtitle garbage:
  - ASS/SSA formatting tags (`{\i1\b1}`)
  - Vector/drawing instructions (`m 1400 136 l 1741 135 …`)
  - Bracketed sound cues (`[music]`, `(sighs)`)
- 🔁 **Automatically reloads** when a new episode starts
- 🧩 Works with:
  - Embedded subtitles
  - Bazarr-managed subtitles
  - Transcoded or direct-play media
- 🔐 **No hardcoded API keys**

---

## 🧠 How It Works (High Level)

1. Connects to a Jellyfin server using the user’s credentials or API token
2. Detects active playback sessions
3. Determines the currently selected subtitle track
4. Fetches the subtitle stream (VTT) from Jellyfin
5. Parses subtitle cues
6. Reads dialogue aloud using the browser’s Text-to-Speech engine
7. Continuously synchronizes speech timing with playback position

All logic runs **client-side**. No media is streamed through this app.

---

## 🚀 Usage

1. Download or clone this repository
2. Open `index.html` in a modern browser
3. Enter your Jellyfin server details
4. Select an active playback session
5. Press **Start**

That’s it.

> ⚠️ Some browsers may restrict network requests when opening files directly.  
> If requests fail, opening the file via a simple local web server may be required.

---

## 🎛️ Controls & Settings

- **Voice selector**  
  Choose any available browser TTS voice (Microsoft Mark recommended)

- **Speech rate**  
  Adjust how fast subtitles are read

- **Sync offset (±5s)**  
  Manually correct subtitle timing differences

- **Auto Sync**  
  Gradually adapts timing to correct drift during playback

- **Session picker**  
  Choose which active Jellyfin playback session to follow

---

## 🖥️ Supported Clients

Works with any Jellyfin client that reports playback position, including:

- Jellyfin Web
- Chromecast
- Android / Android TV
- Desktop browsers

Not limited to Chromecast.

---

## 🧩 Known Limitations

- Uses the **Web Speech API**
  - Voice quality depends on browser and OS
  - Microsoft voices are best on Edge / Windows
- Requires subtitle tracks to exist
- Playback sync accuracy depends on Jellyfin’s reported playback position
- Some subtitle files contain malformed or non-dialogue cues, which are filtered automatically

---

## ❤️ Accessibility First

This project exists to make subtitled media more accessible for:
- Low-vision viewers
- Dyslexia
- Reading fatigue
- Shared viewing experiences

If it helps someone enjoy a show they otherwise couldn’t, it’s doing its job.

---

## 🛠️ Development Notes

- Pure HTML + JavaScript
- No frameworks
- No backend
- Designed for transparency and hackability

---

## 📜 License

MIT License  
Use it, fork it, improve it, share it.

---

## 🙌 Acknowledgements

- Jellyfin community
- Web Speech API
- Bazarr
- Everyone who wants subtitles without barriers
