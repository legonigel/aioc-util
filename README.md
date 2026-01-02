# aioc-util

`aioc-util` is a command-line tool for configuring the [AIOC](https://github.com/skuep/AIOC) device, viewing its internal registers, and changing them (including setting the PTT source).

This utility is modernized from the original script by Hrafnkell Eiríksson TF3HR.

## Requirements

- Python 3.7+
- [hid](https://pypi.org/project/hid/) Python package

## Installation

You can install the package directly from the source directory:

```bash
pip install .
```

### Windows Users

On Windows, you need to provide the `hidapi.dll` library. Download the Windows release build of the [hidapi](https://github.com/libusb/hidapi) project (from the Releases page), locate `hidapi.dll`, and copy it into the directory where you run the `aioc-util` command (or ensure it is in your PATH).

### Linux Users

You likely need to install the hidapi library using your package manager:

```bash
sudo apt install libhidapi-hidraw0
```

Also, you may need udev rules to access the device without root permissions.

```bash
sudo cp udev/rules.d/91-aioc.rules /etc/udev/rules.d/
sudo udevadm control --reload
sudo udevadm trigger
```

## Usage

After installation, the `aioc-util` command is available:

```bash
aioc-util --help
```

### Examples

**Dump registers:**
```bash
aioc-util --dump
```

**Set PTT1 source to VPTT and store:**
```bash
aioc-util --ptt1 VPTT --store
```

**Key radio (PTT on):**
```bash
aioc-util --set-ptt1-state on
```

**Set Foxhunt message:**
```bash
aioc-util --foxhunt-message "CQ FOX" --store
```
