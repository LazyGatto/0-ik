# Voron 0.2 Klipper Configuration

This repository contains a reworked, modular set of Klipper configuration files
for a Voron 0.2 printer. The goal is to keep the live printer setup and the
version-controlled sources in sync while making it easy to understand what each
piece controls.

## Layout
- `config/printer.cfg` – aggregation point that includes the other config
  fragments in a predictable order.
- `config/hardware/` – motion system, drivers, heaters, and auxiliary hardware.
- `config/macros/` – printing, homing, maintenance, and system macros split by
  purpose.
- `config/tests/` – stress and validation routines.
- `config/features/` – optional Klipper feature toggles (e.g. arcs).
- `config/crowsnest.conf` / `config/moonraker.conf` – service configurations.
- `config/fluidd.cfg`, `config/mainsail.cfg`, `config/V0Display.cfg` – UI
  related configs mirrored from the printer; edit these via the respective web
  UIs and sync back if needed.

## Usage
1. Copy the contents of `config/` to the printer’s `printer_data/config/`
   directory (replace sympatric symlinks where necessary).
2. Restart Klipper/Moonraker so the includes are reloaded.
3. Adjust values in `config/variables.cfg` for bed size, pause locations, and
   other shared constants.
4. Slice prints using `PRINT_START` / `PRINT_END` macros during start/end G-code.

Keep `_old_config` (if present) for known-good snapshots while testing new
changes locally. Once validated on the printer, update this repository to stay
aligned with the working configuration.
