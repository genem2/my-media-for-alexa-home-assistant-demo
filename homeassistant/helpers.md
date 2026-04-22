
# Home Assistant Helpers

Create the following helpers in Home Assistant.

Go to:

**Settings → Devices & Services → Helpers**

---

# Input Boolean

Use these to track playback state.

- `input_boolean.mymedia_playing`
- `input_boolean.mymedia_paused`
- `input_boolean.mymedia_failed`

---

# Input Text

Use these to store metadata and user input.

| Helper | Suggested Max Length |
|---|---|
| `input_text.mymedia_track` | 120 |
| `input_text.mymedia_artist` | 120 |
| `input_text.mymedia_album` | 120 |
| `input_text.mymedia_playlist` | 120 |
| `input_text.mymedia_device` | 100 |
| `input_text.mymedia_artwork_url` | 255 |
| `input_text.mymedia_last_event` | 100 |
| `input_text.mymedia_error` | 255 |
| `input_text.mymedia_query` | 120 |

---

# Input Select

## `input_select.mymedia_mode`

Options:

- `play`
- `play the album`
- `play music by`
- `shuffle music by`
- `play playlist`

## `input_select.alexa_device`

Use names that match your Alexa command script.

Examples:

- `bedroom`
- `office`
- `oak`
- `downstairs`
- `house`

---

# Input Datetime

Used to store the last webhook event time.

- `input_datetime.mymedia_event_time`

Enable:

- Date
- Time

---

# Notes

## Naming

All helpers use the `mymedia_` prefix so they are easy to find in Home Assistant.

## Editable Values

Most helpers should remain editable so users can manually test values during setup.

## Artwork URL Limit

Home Assistant UI currently limits `input_text` helpers to 255 characters, which is sufficient for most artwork URLs.
