# freePEMF
A single Arduino .ino file for beginners. Fully functional firmware for the freePEMF device.

Home: biotronics.eu (archived) / biotronika.pl

Supports frequencies up to 16 kHz (0.01–60.99 Hz standard, 61 Hz–16 kHz experimental).

Related documents:
- bioZAP 2018-10-21 EN.pdf (originally hosted on biotronika.pl; use the documentation folder or a web archive if the link is offline)
- Polish manual (2018-04-09) — slightly out of date

### How to compile and upload with Arduino IDE
1. Download freePEMF.ino and place it in a folder named exactly freePEMF.
2. Open freePEMF.ino in Arduino IDE.
3. Ensure EEPROM and Wire libraries are available (Sketch -> Include Library -> verify EEPROM and Wire).
4. Install LiquidCrystal_I2C (Sketch -> Include Library -> Manage Libraries...; search for LiquidCrystal_I2C by Frank de Brabander, select version 1.1.2 and Install).
5. Select board: Tools -> Board -> Arduino Nano; Processor: ATmega328P (Old Bootloader).
6. Install the CH341 USB-Serial driver if needed (CH341SER.ZIP). If the original biotronika.pl link is down, use a trusted mirror or archived copy.
7. Select serial port: plug USB to PC and device; then Tools -> Port -> choose the correct COM port.
8. Define or comment compile-time options as needed (e.g., #define FREEPEMF_DUO). For freePEMF duo, the defaults are fine.
9. Upload: Sketch -> Upload. Wait for "Done uploading" in the status bar.

#### TODO in freePEMF user manual
1. Support for Bluetooth interface and communication with PC & mobile phones
2. freePEMF duo functions description in bioZAP doc
3. pbar in bioZAP doc

#### TODO
* hrm
* chrm
* jump ... min max
* njump ... min max
* jump3
* auto-calculation of pbar
* pause working in xfreq mode (above 61 Hz)

#### DONE
2019-05-31
* blight [0|1] — turn backlight of LCD on/off
* pin3 [0|1|~] — pin3 as output: 0=low, 1=high (5V), ~=toggle

2019-05-28 — added RTC (DS3231) support. New time-control commands:
* settime [hh] [mm] [ |ss] — set specific time
* waitfor [hh] [mm] [ |ss] — wait for specific time
* gettime — returns hh mm ss

2019-03 — freePEMF duo support
* During therapy loading, add beep after committing each part of the script
* Support for Bluetooth interface
* out mode: B M A — Both, Main or Auxiliary coil
* Automatic change of out to M above 61 Hz
* disp 0|1 — use or do not use display (freePEMF duo only) 1=use, 0=don't use
* pbar <left_time_sec> < |percent> — setup program progress bar on LCD. Percent optional; none means 100%
* pbar — manual refresh LCD if display is off
* print
