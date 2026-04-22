# My Media for Alexa + Home Assistant Demo
<img width="572" height="323" alt="image" src="https://github.com/user-attachments/assets/91871b7b-9100-45a8-b0a0-768ddba92583" />

A community example showing how to integrate **[My Media for Alexa](https://www.mymediaalexa.com/)** [webhook events](https://bizmodeller-docs--1-3-153-4-3xdaagpb.web.app/my-media-for-alexa/webhook.html) with **Home Assistant** to create a polished dashboard experience.

This project demonstrates how to use webhook playback events to power a Lovelace dashboard card with:

* Now Playing status
* Album artwork
* Track / artist / album / playlist details
* Quick launch controls
* Pause / Resume / Next / Stop buttons
* Alexa device selection

## What This Solves

Home Assistant can launch Alexa commands, but My Media webhook events now make it possible to build a true dashboard showing:

- now playing
- artwork
- playback state
- quick controls


Special thanks to the My Media for Alexa developer for adding webhook support.

---

## Quick Start

1. Enable My Media webhook support
2. Import helpers
3. Add webhook automation
4. Add command script
5. Paste Lovelace card

---

## Requirements

### Home Assistant

Recommended recent version of Home Assistant.

### My Media for Alexa

Webhook support enabled.

### Custom Cards

Install via HACS:

* `button-card`
* `stack-in-card` (recommended)

### Alexa Command Path

This example uses a Home Assistant script that sends text commands to Alexa devices.

Most users will already have one of these options:

* Alexa Media Player integration
* Existing custom Alexa command script
* Other Alexa TTS / command workflow

---

## How It Works

## 1. My Media sends webhook events

Examples:

* `track_start`
* `playlist_start`
* `pause`
* `resume`
* `stop`
* `error`

## 2. Home Assistant automation receives webhook

Webhook endpoint:

```text
/api/webhook/mymedia_webhook
```

## 3. Automation stores event data in helpers

Examples:

* current track
* artist
* album
* artwork URL
* playback state

## 4. Lovelace card displays everything live

---

# Setup

## Step 1 — Create Helpers

Create these helpers in Home Assistant.

## Input Boolean

```text
input_boolean.mymedia_playing
input_boolean.mymedia_paused
input_boolean.mymedia_failed
```

## Input Text

```text
input_text.mymedia_track
input_text.mymedia_artist
input_text.mymedia_album
input_text.mymedia_playlist
input_text.mymedia_device
input_text.mymedia_artwork_url
input_text.mymedia_last_event
input_text.mymedia_error
input_text.mymedia_query
```

Recommended max length:

* artwork URL = 255
* most others = 100 to 120

## Input Select

```text
input_select.mymedia_mode
```

Options:

```text
play
play the album
play music by
shuffle music by
play playlist
```

```text
input_select.alexa_device
```

Examples:

```text
bedroom
office
oak
downstairs
house
```

Use names your Alexa command service expects.

## Input Datetime

```text
input_datetime.mymedia_event_time
```

---

# Step 2 — Add Webhook Automation

Create an automation that listens for:

```text
mymedia_webhook
```

Store incoming payload values into helpers.

Update playback booleans based on event type.

See:

```text
homeassistant/automations/mymedia_webhook_receiver.yaml
```

---

# Step 3 — Add Alexa Command Script

This repo includes:

```text
homeassistant/scripts/issue_alexa_command.yaml
```

Used to send commands such as:

```text
ask My Media to play music by Justin Hayward
pause
resume
next
stop
```

---

# Step 4 — Add Lovelace Card

Dashboard card YAML:

```text
homeassistant/lovelace/mymedia_dashboard_card.yaml
```

---

# Features

## Launcher

Choose:

* mode
* search text
* Alexa device

Then press:

```text
Go
```

## Live Now Playing

Displays:

* artwork
* track
* artist
* album
* playlist
* device
* status

## Transport Controls

* Pause
* Resume
* Next
* Stop

---

# Notes

## Artwork Refresh

Artwork URLs may be cached by browsers.

This example appends a timestamp query string to force refresh.

## Device Names

Use whatever Alexa device names your existing HA script supports.

---

# Included Files

```text
homeassistant/
├── automations/
├── scripts/
├── lovelace/
```

---

# Credits

* My Media for Alexa developer for webhook support
* Home Assistant community
* Alexa Media Player contributors

---

![Home Assistant](https://img.shields.io/badge/Home%20Assistant-Compatible-blue)
![License](https://img.shields.io/badge/license-MIT-green)
