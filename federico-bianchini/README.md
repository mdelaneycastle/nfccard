# NFC Digital Business Card — Federico Bianchini / Castle Fine Art Manchester

Same page as the parent card, with Federico's details. Self-contained: `index.html`,
`contact.vcf`, `assets/photo.jpg`, `fonts/`. Includes the QR fallback (the QR carries
the whole vCard, so it works with no signal).

## Details on the card

| Field | Value |
|-------|-------|
| Name | Federico Bianchini |
| Title | Art Consultant, Castle Fine Art · Manchester |
| Mobile | 07448 340536 (`tel:+447448340536`) |
| Email | fbianchini@castlefineart.com |
| Website | castlefineart.com |
| Address | 12-14 King Street, Manchester M2 6AG |
| Instagram | [@castlegalleries](https://www.instagram.com/castlegalleries/) |
| LinkedIn | none |

No gallery landline on the card — the mobile stands alone, as on Lewis's. To add one,
duplicate the phone `<li>` in `index.html` and add a second
`TEL;TYPE=WORK,VOICE:+44…` line to `contact.vcf`, then regenerate the QR.

## Test locally

```bash
cd nfc-business-card/federico-bianchini
python3 -m http.server 8000
```

## Deploy

Copy this folder into the GitHub Pages site repo as `card/federico-bianchini/` — it
goes live at `https://marcdelaney.co.uk/card/federico-bianchini`. Then write that URL
to the NFC tag with **NFC Tools → Write → URL/URI**, and only lock the tag once you've
tapped it and confirmed the page loads.

## Regenerate the QR after any detail change

```bash
python3 tools/make-qr.py contact.vcf   # segno required: pip install segno
```

Paste the output over the existing `<svg class="qr">` inside `<div class="qr-tile">`.
