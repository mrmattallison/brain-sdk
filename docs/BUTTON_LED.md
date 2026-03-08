# BUTTON_LED Component

## Overview
`ButtonLed` is a dedicated helper for the illuminated button LED on Brain (`GPIO_BRAIN_BUTTON_1_LED`).
It wraps `Led` in `LedMode::kSimple`, so it is intentionally on/off only (no PWM dimming API).

## Features
- Fixed simple GPIO behavior (no PWM mode switching)
- Basic control: `on()`, `off()`, `toggle()`
- Blink support: finite blink, duration blink, continuous blink
- Optional callbacks for state changes and blink-end events

## Usage
```cpp
#include "brain-ui/button-led.h"

brain::ui::ButtonLed button_led;
button_led.init();

button_led.on();
button_led.blink_duration(800, 120);

while (true) {
    button_led.update();
}
```

## API Reference
- `ButtonLed(uint gpio_pin = GPIO_BRAIN_BUTTON_1_LED)`
- `void init()`
- `void on()`
- `void off()`
- `void toggle()`
- `void blink(uint times, uint interval_ms)`
- `void blink_duration(uint duration_ms, uint interval_ms)`
- `void start_blink(uint interval_ms)`
- `void stop_blink()`
- `void update()`
- `bool is_on() const`
- `bool is_blinking() const`
- `void set_on_state_change(std::function<void(bool)> callback)`
- `void set_on_blink_end(std::function<void()> callback)`

## Notes
- `update()` must be called regularly for blink timing.
- Intended for the built-in illuminated button LED.
