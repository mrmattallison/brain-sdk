# Sandbox Firmware Wrapper (`sandbox`)

This directory contains:
- `main.cpp`: selected app entrypoint
- `apps/blink.*`: default Pico LED blink app
- `CMakeLists.txt`: `sandbox` target definition
- `README.md`: wrapper notes

Hardware test app implementations live in `test/apps/`.

## Switching active app

Edit `sandbox/main.cpp`:
- change the include from `#include "apps/blink.h"` to another header in `sandbox/apps/`
- change the instantiated class in `main()`

Then rebuild:
```bash
cmake --build build --target sandbox -j4
```
