# Änderungen / Changelog

Blue-64 Keyboard für iOS und Android. Neueste Version zuerst.

## Neu (noch ohne Release) / Unreleased

### Deutsch

- **iPad** (TestFlight): Tastatur unten, Textfeld mit Bausteinen immer sichtbar, Ziffernblock und Pos1/Ende/Bild im PC-Modus.
- **iPhone/iPad: Tasten reagieren sofort**, auch an der Seite des Ladeanschlusses (iOS hatte dort Berührungen bis zu 0,75 s zurückgehalten) und beim Festhalten von SHIFT mit einem zweiten Finger.
- **Rechte SHIFT-Taste** wird als rechte SHIFT gesendet (Pico64 ab 0.11.1, Pico USB Keyboard ab 0.4.1). Beim Blue-64 (Firmware ab v1.12-ble2) nur, wenn keine andere Taste gehalten wird.
- **Mehrere Tasten gleichzeitig halten** (Pico64, Pico USB Keyboard): die App sendet die ganze Tastaturmatrix, eine zweite Taste lässt die erste nicht mehr los – wie bei der echten Tastatur. Das Blue-64 kann technisch nur eine Taste, dort bleibt es wie bisher.

### English

- **iPad** (TestFlight): keyboard at the bottom, text field with snippets always visible, number pad and Home/End/PgUp/PgDn in PC mode.
- **iPhone/iPad: keys react at once**, also on the side of the charging port (iOS held touches back there for up to 0.75 s) and while SHIFT is held with another finger.
- **Right SHIFT key** is sent as right SHIFT (Pico64 0.11.1 and newer, Pico USB Keyboard 0.4.1 and newer). With the Blue-64 (firmware v1.12-ble2 and newer) only while no other key is held.
- **Hold several keys at once** (Pico64, Pico USB Keyboard): the app sends the complete keyboard matrix, a second key no longer releases the first one – like the real keyboard. The Blue-64 can only handle one key, no change there.

## v1.1.0 – 2026-10-07

### Deutsch

- **PC-Modus** für das neue [Pico USB Keyboard](https://github.com/do2mad/pico-usb-keyboard): das Handy als USB-Tastatur für MiSTer, PC, Mac und Raspberry Pi. Oben die Knöpfe **C64** / **PC**, der gewählte ist orange.
- PC-Tastatur mit den Layouts US, Deutsch (PC), Deutsch (Mac) und US (Mac); Mac-Layouts mit ⌘ neben der Leertaste, Pfeiltasten als umgedrehtes T.
- Bei Shift, Option bzw. AltGr zeigen die Tasten das Zeichen, das getippt wird.
- Sondertasten zweimal antippen = eingerastet; Caps Lock wird angezeigt.
- Text und Textbausteine im gewählten PC-Layout; getrennte Bausteine für C64 und PC.
- Unterstützt auch den [Pico64 Keyboard](https://github.com/do2mad/pico64-keyboard)-Adapter.

### English

- **PC mode** for the new [Pico USB Keyboard](https://github.com/do2mad/pico-usb-keyboard): the phone as USB keyboard for MiSTer, PC, Mac and Raspberry Pi. Buttons **C64** / **PC** at the top, the selected one is orange.
- PC keyboard with the layouts US, German (PC), German (Mac) and US (Mac); Mac layouts with ⌘ next to the space bar, cursor keys as inverted T.
- With Shift, Option or AltGr the keys show the character that will be typed.
- Double tap a modifier = locked; Caps Lock is shown.
- Text and snippets with the chosen PC layout; separate snippets for C64 and PC.
- Also supports the [Pico64 Keyboard](https://github.com/do2mad/pico64-keyboard) adapter.

## v1.0.0 – 2026-09-24

### Deutsch

Erste Version.

- Vollständige C64-Tastatur im Brotkasten-Look, mehrere Finger gleichzeitig
- SHIFT / C= / CTRL halten oder antippen (gilt dann für die nächste Taste), SHIFT LOCK, RESTORE
- Tastenbeschriftung wie am Original: C=- und SHIFT-Grafikzeichen auf der Vorderseite, Farben auf den Ziffern
- Bei gedrücktem SHIFT, C= oder CTRL zeigen die Tasten, was der C64 schreibt
- Zeichensatz-Umschaltung (SHIFT + C=) wird mitverfolgt
- Text und kurze BASIC-Listings eintippen lassen, eigene Textbausteine
- Oberfläche Deutsch und Englisch
- Benötigt die BT-64-Firmware mit BLE-Tastaturdienst
- Android-App (ab Android 8.0) mit denselben Funktionen, als APK im Release

### English

First release.

- Full C64 keyboard in breadbin look, multi-touch
- SHIFT / C= / CTRL can be held or tapped (applies to the next key), SHIFT LOCK, RESTORE
- Keycap legends like the original: C= and SHIFT graphics on the front, colours on the digits
- While SHIFT, C= or CTRL is active, the keys show what the C64 will print
- Follows the character set switch (SHIFT + C=)
- Type text and short BASIC listings, custom snippets
- English and German user interface
- Requires the BT-64 firmware with the BLE keyboard service
- Android app (Android 8.0+) with the same features, as APK in the release
