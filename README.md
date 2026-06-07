# eiktub — Arabic Transliteration Engine

**eiktub** converts phonetically typed Latin text into proper Arabic script in real time. Type the way you hear it — the engine figures out the correct Arabic characters, including vowels, hamza forms, and special letters.

🟢 **[Try it live at eiktub.com](https://www.eiktub.com)**

---

## How it works

The engine intercepts keystrokes and maps them to Arabic Unicode characters using a rule-based system. It handles:

- All 28 Arabic consonants
- Short and long vowels (حركات وأحرف العلة)
- Shadda / doubled consonants (شدة)
- Tanwin in all three forms (تنوين)
- Hamza in all positions and shapes (همزة) — chosen automatically based on context
- Al-ta'rif (ال التعريف) with solar/lunar letter handling
- Arabizi notation (numbers as Arabic letters: 3, 7, 2, etc.)
- Alif maqsura, taa marbuta, sukun, madda

---

## Quick Reference

### Consonants

| Arabic | Type | Arabic | Type | Arabic | Type | Arabic | Type |
|--------|------|--------|------|--------|------|--------|------|
| ا | A | ب | b | ة | t' | ت | t |
| ث | c, th | ج | j | ح | H | خ | K, kh |
| د | d | ذ | z', dh | ر | r | ز | z |
| س | s | ش | x, sh | ص | S | ض | D |
| ط | T | ظ | Z | ع | E | غ | g, gh |
| ف | f | ق | q | ك | k | ل | l |
| م | m | ن | n | ه | h | و | w |
| ي | y | ء | e, 2, ' | | | | |

> Capital letters represent "heavy" (emphatic) Arabic sounds — e.g. `d` → د, `D` → ض

### Vowels

| Type | Short | Long | Tanwin |
|------|-------|------|--------|
| فتحة / a-sound | `a` | `aa` | `aN` |
| ضمة / u-sound | `u` | `uu` | `uN` |
| كسرة / i-sound | `i` | `ii` | `iN` |
| الف مقصورة | | `aaa` | `aN` + aaa |

### Arabizi (chat alphabet)

| ح = 7 | خ = 5 | ص = 9 | ض = '9 | ط = 6 | ظ = '6 | ع = 3 | همزة = 2 |
|-------|-------|-------|--------|-------|--------|-------|---------|

### Special rules

- **Shadda**: type the same consonant twice — `muhammad` → محمّد
- **Hamza**: use `e`, `2`, or `'` — the engine picks the correct shape automatically
- **Al- (ال)**: use `Al-` — solar/lunar assimilation is handled automatically
- **Dash separator**: use `-` to prevent two letters from being parsed as a digraph — `s-h` → سه (not ش)

---

## Examples

| Latin input | Arabic output |
|-------------|---------------|
| mrhba | مرحبا |
| Al-ealam | العالم |
| muhammad | محمّد |
| samaae | سماء |
| maaeaN | ماءً |
| einsaan | إنسان |
| bAlnaas | بالناس |

---

## Usage

Include `eiktub_litepad.js` in your page and attach it to a textarea:

```html
<textarea id="pad" onkeypress="return eiktub_litepad.Transliterate(event, this)"
          onkeydown="eiktub_litepad.SpecialKeys(event, this)"></textarea>
<script src="eiktub_litepad.js"></script>
```

### Options

```js
eiktub_litepad.on = 1;       // 1 = transliteration on, 0 = off (Ctrl+Y to toggle)
eiktub_litepad.arabesh = 1;  // 1 = allow Arabizi numbers (3, 7, 2...)
eiktub_litepad.vowels = 1;   // 1 = show short vowel diacritics
```

---

## Files

| File | Description |
|------|-------------|
| `eiktub_litepad.js` | Client-side JavaScript transliteration engine |
| `BATRengine.cs` | Server-side C# port of the same engine (ASP.NET) |

---

## Background

The transliteration scheme is based on **BATR** (Bikdash Arabic Transliteration Rules), designed to be intuitive for English speakers while covering the full range of Arabic phonology including emphatic consonants, long vowels, and the notoriously tricky hamza.

The system was originally developed around 2008 and powers the online pad at [eiktub.com](https://www.eiktub.com).

---

## License

MIT License — see [LICENSE](LICENSE) for details.

Copyright © 2008–2026 LinguArabica, LLC
