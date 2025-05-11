# gogtog

**gogtog** is a lightweight Arduino library for working with push-buttons connected to `INPUT_PULLUP` digital pins. It provides a **debounced toggle mechanism** that flips between `0` and `1` only when a confirmed press is detected.

---

## 🔧 Features

- Works with any digital pin configured as `INPUT_PULLUP`
- Returns a stable toggle value (`0` or `1`) **only when a change occurs**
- Ignores bouncing thanks to internal debounce logic
- Very lightweight – no dynamic memory or dependencies
- Configurable debounce time (default 5ms)

---

## 🚀 Why use gogtog?

This library is **especially well-suited for use in environments that require reliable digital toggles**, such as:

- Serial communication with **Max/MSP**, **PureData**, **Processing**, or other host environments
- Triggering discrete actions (e.g. scene switching, toggling states)
- Interfaces with physical buttons where you want to avoid repeated messages

Because the library **only returns a value when a change is confirmed**, it's perfect for **low-latency, noise-free control protocols** – especially over serial communication.

---

## 📦 Example

```cpp
#include <GogTog.h>

GogTog button(4, 5);  // pin 4, 5ms debounce

void setup() {
  button.begin();
}

void loop() {
  int state = button.update();
  if (state != -1) {
    // state is 0 or 1 (toggle result)
    // send to Serial, MIDI, OSC, etc.
  }
}
