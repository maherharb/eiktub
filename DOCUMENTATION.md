# eiktub Documentation

Full reference for the BATR (Bikdash Arabic Transliteration Rules) system used by eiktub.

For a quick overview, see the [README](README.md). For a guided walkthrough, visit the [Tutorial](https://www.eiktub.com/tutorial.html).

---

## Table of Contents

1. [Consonants](#1-consonants)
2. [Diacritization](#2-diacritization)
3. [Vowelization](#3-vowelization)
4. [Shadda (شدة)](#4-shadda-شدة)
5. [Tanwin (تنوين)](#5-tanwin-تنوين)
6. [Hamza (همزة)](#6-hamza-همزة)
7. [Special Characters — Al-ta'rif (ال التعريف)](#7-special-characters--al-tarif-ال-التعريف)

---

## 1. Consonants

Most Arabic consonants are represented by their English phonetic equivalents. Capital letters represent "heavy" (emphatic) Arabic letters.

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

- With the exception of ذ (*z'aal*) and ة (*taa marbuta*), every consonant is one key (upper or lower case).
- Use a **dash** to prevent two letters from being read as a digraph: `s-h` → سه (not ش), `t-h` → ته (not ث).

---

## 2. Diacritization (شكل كما تسمع)

Full diacritization involves short vowels (حركات), long vowels (أحرف العلة), tanwin (تنوين), shadda (شدة), and madda (مدة).

Short vowels are often omitted in Modern Standard Arabic (newspapers, magazines) but are essential for correct pronunciation. eiktub encourages full vowelization — **type the word the way you hear it** (شكل كما تسمع).

---

## 3. Vowelization

| Sound | Short | Long | Tanwin |
|-------|-------|------|--------|
| فتحة (a) | `a` | `aa` | `aN` |
| ضمة (u) | `u` | `uu` | `uN` |
| كسرة (i) | `i` | `ii` | `iN` |
| الف مقصورة | — | `aaa` | `aaaN` |

Long vowels automatically include the corresponding short vowel. For example, `aa` in *samaae* = سَمَاء produces both a *fatHa* and an *alif*.

Vowelization can be suppressed via the `eiktub_litepad.vowels = 0` option.

---

## 4. Shadda (شدة)

Type the same consonant twice to produce shadda (doubled consonant stress).

| Input | Output |
|-------|--------|
| `muHmmd` | محمّد |
| `quwwat'` | قوّة |

Note: inserting a vowel between two identical consonants prevents shadda — `mamduuH` → ممدوح (no shadda).

---

## 5. Tanwin (تنوين)

| Tanwin | Type | Notes |
|--------|------|-------|
| فتحتين | `aN` | eiktub adds alif where required |
| ضمتين | `uN` | |
| كسرتين | `iN` | |

eiktub recognises when an alif is needed in *tanwin al-fath*:

| Input | Output | Word |
|-------|--------|------|
| `baytaN` | بيتاً | house |
| `baqarataN` | بقرةً | cow |
| `samaaeaN` | سماءً | sky |

---

## 6. Hamza (همزة)

The hamza in all its shapes is represented by `e`, `2`, or `'` (apostrophe). The correct form is determined by the surrounding vowels you type — **proper vowelization is required** for the engine to produce the right shape.

### Hamza forms by context

| Input | Output | Notes |
|-------|--------|-------|
| `maaeaN` | ماءً | hamza on satar, fathatan |
| `maaeuN` | ماءٌ | hamza on satar, dammatan |
| `maaeiN` | ماءٍ | hamza on satar, kasratan |
| `maaeahu` | ماءهُ | hamza on satar |
| `maaeuhu` | ماؤهُ | hamza on waw |
| `maaeihi` | مائهِ | hamza on kursi |
| `maae` | ماء | hamza on satar |
| `maaeo` | مَاءْ | hamza with sukun |
| `laein` | لئن | hamza on kursi |
| `laeiim` | لئيم | hamza on kursi |
| `biTeuN` | بطءٌ | hamza on satar |
| `sueaal` | سؤال | hamza on waw |
| `Al-ealam` | العالم | hamza after Al- |
| `einsaan` | إنسان | hamza below alif |
| `Al-einsaan` | الإنسان | hamza below alif after Al- |

### Using a dash with hamza

A dash suspends parsing rules where needed — particularly for hamza following a prefix:

| Correct | Wrong |
|---------|-------|
| `bi-eannanii` → بِأَنَّنِي | `bieannanii` → بِئَنَّنِي |
| `la-ein` → لَأَنْ | `laein` → لَئِنْ |
| `li-eanna` → لِأَنَّ | `lieanna` → لِئَنَّ |

If the hamza is mid-word only, no dash is needed.

---

## 7. Special Characters — Al-ta'rif (ال التعريف)

The definite article "the" is written as `Al-`. Solar/lunar letter assimilation is handled automatically.

| Input | Output |
|-------|--------|
| `Al-naas` | الناس |
| `bAlnaas` | بالناس |
| `Al-einsaan` | الإنسان |
| `bAl-einsaan` | بالإنسان |
| `lileinsaan` | للإنسان |

Use `Al-` with hyphens on both sides when a hamza follows, to ensure correct parsing.

---

## Arabizi (Arabic chat alphabet)

Numbers can be used as alternative representations for letters without English equivalents:

| ح = 7 | خ = 5 | ص = 9 | ض = '9 | ط = 6 | ظ = '6 | ع = 3 | همزة = 2 |
|-------|-------|-------|--------|-------|--------|-------|---------|

---

*Copyright © 2008–2026 LinguArabica, LLC*
