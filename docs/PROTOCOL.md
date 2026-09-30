# BT-64 BLE keyboard protocol (v1)

The BT-64 advertises as **`Blue-64`** with the 128-bit service UUID
**`C64B0001-B1E6-4A64-9C64-6B7E3F1A2D00`**. No pairing is required.

| Characteristic | UUID | Properties |
|---|---|---|
| Key | `C64B0002-B1E6-4A64-9C64-6B7E3F1A2D00` | write, write without response |
| Text | `C64B0003-B1E6-4A64-9C64-6B7E3F1A2D00` | write |
| Info | `C64B0004-B1E6-4A64-9C64-6B7E3F1A2D00` | read |

## Key

Two bytes: `[flags, key]`

| flags bit | meaning |
|---|---|
| 0 | SHIFT |
| 1 | C= (Commodore key) |
| 2 | CTRL |
| 3 | RESTORE |

`key` is the C64 keyboard matrix position `PA * 8 + PB` (0–63), where PA is the
column line (CIA1 port A) and PB the row line (CIA1 port B). `0xFF` = no key.
Examples: RETURN = `0*8+1 = 1`, A = `1*8+2 = 10`, SPACE = `7*8+4 = 60`.

Every write describes the complete keyboard state. The BT-64 hardware can address one
matrix position at a time plus the SHIFT/C=/CTRL/RESTORE lines, so the client sends the
most recently pressed key (key rollover). Each state is held for at least 30 ms by the
firmware, so press/release sequences are never lost. `[0x00, 0xFF]` releases everything;
the firmware also releases all keys when the client disconnects.

## Text

Write in chunks of at most (ATT MTU − 3) bytes:

- byte 0: bit 0 = first chunk, bit 1 = last chunk
- bytes 1…: text in BT-64 macro syntax (lower-case letters are typed unshifted,
  `~ret~`, `~clr~`, `~home~`, `~f1~` … `~f8~`, `~up~`, `~dn~`, `~ll~`, `~rr~`, …)

Maximum total length: 1024 bytes. While the BT-64 is still typing a previous text,
the last chunk is rejected with ATT error `0x80` (busy) – retry after a short delay.
ATT error `0x81` means the text is too long.

## Info

Read returns `[protocol version, status]`, status bit 0 = text feed running.
