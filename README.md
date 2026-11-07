# DJI Mavic 3 RC231 (RC-N1) to Gamepad Interface

This project allows you to connect your DJI Mavic 3 RC231 (RC-N1) remote controller to your PC via a USB serial port and emulate a virtual gamepad (`vgamepad` or `vjoy`). This is useful for using your drone controller in simulators or other PC applications.

## Prerequisites

Make sure you have Python installed on your system. You will also need to install the required Python packages depending on which driver you plan to use.

### Required Libraries

*   **pyserial** (Required for serial communication)
*   **vgamepad** (Default driver for Xbox 360 controller emulation) *or* **pyvjoy** (Alternative vJoy driver)

You can install them via pip:

```bash
pip install pyserial vgamepad
# OR for vJoy:
pip install pyserial pyvjoy
```

---

## Quick Start (Using `start.bat`)

To make starting the interface easy on Windows, a batch script has been provided. 

1. Place `start.bat` in the same directory as `main.py`.
2. Double-click **`start.bat`** (or run it from your command prompt) to launch the script automatically.

### Example `start.bat` Content

```bat
@echo off
TITLE DJI RC231 Gamepad Bridge
python main.py
pause
```

If you need to specify a specific COM port or driver, you can edit the `start.bat` file and pass command-line arguments:

```bat
@echo off
python main.py --port COM3 --driver vgamepad
pause
```

---

## Command Line Arguments

You can configure the script using the following options:

*   `-p`, `--port`: RC Serial Port (leave empty to auto-scan, e.g., `COM3`).
*   `--driver`: Driver type (`vgamepad` or `vjoy`). Default is `vgamepad`.
*   `-d`, `--device`: VJoy Device ID (Only needed when using the `vjoy` driver). Default is `1`.
*   `-i`, `--invert`: Invert axis (`lv`, `lh`, `rv`, `rh`, or `cam`). Default is `['lv', 'rv']`.

### Usage Examples

Run with auto-port detection and default settings:
```bash
python main.py
```

Run specifying a COM port and inverting specific axes:
```bash
python main.py -p COM4 -i lv rv rh
```

---

## Controls & Features

*   **Sticks:** Left and right joysticks map directly to the virtual gamepad axes.
*   **Camera Dial (`cam`):** 
    *   Pushing the camera dial past limits triggers special gamepad button presses (e.g., button Y to restart a race or button B to recover the drone in specific simulator setups).
