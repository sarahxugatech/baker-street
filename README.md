# Baker Street

A cinematic, text-interactive Sherlock Holmes web app — run Ollama locally, then double-click to chat.

![Sherlock Holmes at 221B Baker Street](assets/hero.webp)

## Features

- Victorian conversation rendered with a typewriter-style reply plaque.
- British neural speech through Edge TTS, with browser speech synthesis as a fallback.
- A panoramic 221B room where Holmes walks between the desk, fireplace, and window.
- A violin scene with a synthesized D-minor air.
- A translucent visitor silhouette that reacts while the user types and Holmes speaks.
- Photo and layered SVG cartoon modes, with the visual preference saved locally.
- Responsive presentation for desktop and mobile, with no build step.

## How to run

The checked-in version uses a free local Ollama model; it does not request or store an Anthropic API key.

1. Install [Ollama](https://ollama.com/) and download the configured model:

   ```bash
   ollama pull llama3.1:8b
   ```

2. Allow a local `file://` page to reach Ollama, then start the service:

   ```bash
   OLLAMA_ORIGINS="*" ollama serve
   ```

3. Double-click `index.html`, type a message, and press Return.

If the Ollama desktop app is already running, quit it before starting the command above so the origin setting takes effect. To use a different local model, update the `MODEL` constant near the top of the inline script in `index.html`.

## Technology

- Single-file HTML with inline CSS and JavaScript
- Ollama browser API at `127.0.0.1:11434`
- Edge TTS with browser-native speech fallback
- Web Audio API for voice-reactive motion and violin synthesis
- SVG, CSS animations, and local visual assets
- No framework, package manager, server, or build step

## Project structure

```text
baker-street/
├── index.html                 # Complete application: markup, styles, and logic
├── README.md
└── assets/
    ├── room-panorama.webp     # Wide 221B environment
    ├── holmes-standing.webp   # Standing photo figure
    ├── holmes-violin-figure.webp
    ├── user-presence.webp     # Foreground visitor silhouette
    ├── scene-sofa.webp
    ├── holmes-listening.mp4
    ├── holmes-speaking.mp4
    ├── violin-playing.mp4
    └── supporting source images and animation clips
```

## Security

The repository contains no API key, token, password, or other secret. The current local-Ollama version needs no cloud credential. Browser `localStorage` is used only for the mute preference and the cartoon/photo preference, and those values remain on the visitor's own device.
