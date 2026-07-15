# Server Form Overlay

[![License: Unlicense](https://img.shields.io/badge/license-Unlicense-blue.svg)](https://unlicense.org/)

> **Note:** This repository is a fork of my old project [Server_Form_Ui](https://github.com/yasserXd99/Server_Form_Ui) (account: yasserXd99). It is now maintained under my current GitHub account **YasserNull**.

---

## What is Server Form Overlay?

A **Minecraft Bedrock** addon that lets you place interactive buttons directly on the gameplay HUD screen using the server‑form overlay technique.  

![](https://github.com/YasserNull/server-form-overlay/raw/main/docs/images/screenshot2.jpg)
![](https://github.com/YasserNull/server-form-overlay/raw/main/docs/images/screenshot3.jpg)


## How it works

The core idea was inspired by **Ty-el's Settings Overlay UI Pack**, which made the settings screen appear as a transparent overlay on top of the game world.  
By applying the same property (`"is_showing_menu": false`) to the **server form** UI, and solving a series of technical challenges, we can keep a server‑form visible while the player moves, builds, and fights.  
Scripting API (`@minecraft/server-ui`) can then be used to make those buttons execute code.

A complete technical write‑up, findings, and bugs discovered on other screens (bed, crafting, chest, NPC) is available in the research paper.

## Pack details

- **Minecraft version:** 1.16+  
- **Works only with touch controls** – keyboard/mouse and controller are not supported.

## Usage notes

If you create custom buttons on the overlay form, you **must** add the following property to each button to prevent touch input from passing through to the game behind:

```json
"prevent_touch_input": true
```

Example button definition in your UI JSON:

```json
"my_button@common_buttons.dark_glyph_button": {
  "$dark_glyph_button|dark_button_assets": {
    "prevent_touch_input": true
  }
}
```

Also, do not use screen animations – they cause delays. Always set:

```json
"$screen_animations": [],
"$background_animations": []
```

# License

This project is released under the Unlicense – it is dedicated to the public domain.
You are free to use, modify, and distribute it for any purpose without any restrictions.

See the [License](LICENSE) file for the full text, or visit [unlicense.org](unlicense.org). 

# Research Paper

The comprehensive research document that started it all can be found here:

[overlay-technique-paper.md](docs/overlay-technique-paper.md)

Or in Arabic:

[overlay-technique-paper-ar.md](docs/overlay-technique-paper-ar.md)

It covers the discovery of the overlay technique, the properties that make it work, and a detailed bug report originally prepared for the Mojira Bug Tracker.

---

Shoutout to **Ty-el's** for the original **Settings Overlay UI Pack** that inspired this project.