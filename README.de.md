# Blue-64 Keyboard für iOS und Android

*English version: [README.md](README.md)*

Macht das iPhone oder Android-Handy zur kabellosen Tastatur für einen Commodore 64 mit
[BT-64 / Blue-64](https://github.com/sideprojectslab/BT-64) Bluetooth-Adapter – ohne Zusatzhardware.

![Tastatur](docs/screenshots/keyboard.png)

▶ **Video am echten C64:** https://youtube.com/shorts/MC3hHcny5D0

Die App zeigt eine vollständige C64-Tastatur im Brotkasten-Look mit den originalen
PETSCII-Beschriftungen und schickt jeden Tastendruck per Bluetooth Low Energy an den BT-64,
der die Tastaturleitungen des C64 direkt ansteuert.

> **Benötigt die BT-64-Firmware mit BLE-Tastaturdienst.**
> iOS-Apps dürfen sich nicht als Bluetooth-Tastatur (HID) ausgeben. Deshalb stellt die Firmware
> einen kleinen eigenen BLE-Dienst bereit – siehe [docs/FIRMWARE.md](docs/FIRMWARE.md).

## App bekommen

- **iPhone – TestFlight (Beta):** App „TestFlight“ installieren, dann https://testflight.apple.com/join/jEn4tsP7 öffnen
- **iPhone – App Store:** geplant
- **Android:** `Blue64-Keyboard-Android-x.y.z.apk` aus dem
  [neuesten Release](https://github.com/do2mad/blue64-keyboard-ios/releases/latest) auf dem Handy herunterladen und öffnen.
  Android fragt einmal, ob Apps aus dieser Quelle (Browser / Dateien) installiert werden dürfen.

Dieses Repository enthält Dokumentation, BLE-Protokoll und Releases.
Der Quellcode der App wird nicht veröffentlicht.

## Funktionen

- Vollständiges C64-Layout mit RUN/STOP, RESTORE, C=, CTRL, SHIFT LOCK, CLR/HOME, INST/DEL und F1–F8
- Mehrere Finger gleichzeitig; SHIFT / C= / CTRL halten oder kurz antippen (gilt für die nächste Taste)
- Beschriftung wie am Original: C=- und SHIFT-Grafikzeichen vorne auf den Tasten, Farben auf den Ziffern
- Bei gedrücktem SHIFT, C= oder CTRL zeigt jede Taste, was der C64 schreibt
  (PETSCII-Grafik, Farbcodes, Steuerfunktionen)
- Folgt der Zeichensatz-Umschaltung (SHIFT + C=): GROSS/Grafik ↔ klein/GROSS
- **Text tippen lassen:** beliebiger Text oder kurzes BASIC-Listing (bis 1024 Zeichen)
- **Textbausteine:** eigene Knöpfe (z. B. `LOAD"$",8`), in der App anlegen, ändern, sortieren
- Cursor-Schnelltasten, automatisches Wiederverbinden
- Oberfläche Deutsch und Englisch
- **PC-Modus** mit einem [Pico USB Keyboard](https://github.com/do2mad/pico-usb-keyboard): das Handy wird zur
  USB-Tastatur für MiSTer, PC, Mac oder Raspberry Pi (siehe unten)

![Text tippen lassen und Textbausteine](docs/screenshots/type-text.png)

## PC-Modus (Pico USB Keyboard)

Mit einem [Pico USB Keyboard](https://github.com/do2mad/pico-usb-keyboard) – ein einfacher Raspberry Pi
Pico 2 W, der sich als USB-Tastatur meldet – zeigt die App oben zwei Knöpfe **C64** und **PC**:

- **C64** – die C64-Tastatur, gesendet als die Tasten, die der C64-Core des MiSTer erwartet
- **PC** – eine normale PC- oder Mac-Tastatur: Layouts US, Deutsch (PC), Deutsch (Mac), US (Mac); Strg, Alt,
  Win/Cmd, AltGr/Option, Esc, F1–F12, Pfeiltasten, Caps Lock
- Sondertasten: antippen = für die nächste Taste, **zweimal antippen = eingerastet**, nochmal = aus
- Bei aktivem Shift / Option / AltGr zeigen die Tasten das Zeichen, das getippt wird
- Text und Textbausteine werden im gewählten Layout getippt; getrennte Bausteine für C64 und PC,
  im Textfenster umschaltbar

## Voraussetzungen

- iPhone ab iOS 17 oder Android-Handy ab Android 8.0
  (bis Android 11 muss für die Bluetooth-Suche der Standort eingeschaltet sein – Vorgabe von Android, die App nutzt den Standort nicht)
- **Eins** davon:
  - C64 mit BT-64 / Blue-64 und der Firmware mit BLE-Tastaturdienst ([docs/FIRMWARE.md](docs/FIRMWARE.md))
  - C64 mit einem [Pico64-Keyboard](https://github.com/do2mad/pico64-keyboard)-Adapter – Selbstbau-Alternative mit Raspberry Pi Pico 2 W, 17 Widerständen und einer Diode
  - ein [Pico USB Keyboard](https://github.com/do2mad/pico-usb-keyboard) – Raspberry Pi Pico 2 W an einem beliebigen USB-Anschluss (MiSTer, PC, Mac, Raspberry Pi), ohne Verkabelung

## Bedienung

- Die App sucht den BT-64 selbst und merkt ihn sich. Die LED oben zeigt den Zustand:
  grün = verbunden, gelb = Suche, rot = aus/getrennt.
- **ABC / Abc** zeigt den Zeichensatz der Tastenanzeige; folgt SHIFT + C= automatisch,
  antippen, falls es nicht mehr stimmt (z. B. nach einem Reset des C64).
- **Text** öffnet das Eingabefenster. Zeilenumbruch = RETURN, Sonderzeichen:
  `{clr} {home} {f1}…{f8} {up} {down} {left} {right} {stop} {run} {pi}`.
- Die **Textbausteine** oben im Textfenster tippen ihren Text sofort ein; verwalten über **Bausteine**.
  Mit einem Pico USB Keyboard gibt es zwei Sätze, **C64** und **PC** – das Fenster öffnet mit dem
  Satz der gerade angezeigten Tastatur.

## Protokoll

Das BLE-Protokoll ist offen und in [docs/PROTOCOL.md](docs/PROTOCOL.md) beschrieben (englisch) –
eigene Apps für andere Plattformen sind ausdrücklich willkommen.

## Datenschutz

Die App erhebt keine Daten, siehe [PRIVACY.md](PRIVACY.md).

## Dank und Lizenz

- BT-64 / Blue-64 Hardware und Firmware: [SideProjectsLab](https://github.com/sideprojectslab/BT-64) (Apache-2.0)
- App: Martin Oswald (do2mad) – [1mhz.de](https://1mhz.de)

Die App ist © 2026 Martin Oswald, alle Rechte vorbehalten.
Die Dokumentation in diesem Repository einschließlich der Protokollbeschreibung steht unter
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.de).
Änderungen: [CHANGELOG.md](CHANGELOG.md).

Commodore und Commodore 64 sind Marken ihrer jeweiligen Inhaber.
Dieses Projekt steht in keiner Verbindung zu ihnen oder zu SideProjectsLab.
