# Street English Chicago

A spoken-English course for a new Chicago delivery driver who will later become a truck driver.
It has 50 dialogues with American voices, road signs, tests, grammar, verb forms, slang, a translator, teacher notes and a Russian / Tajik dictionary.

The whole site is **one file: `index.html`**. It has no build step, no framework and no server code.

---

## Deploy

### Vercel (recommended)
1. Push this folder to GitHub.
2. On vercel.com: **Add New → Project → Import** the repository.
3. Framework preset: **Other**. Leave the build command and output directory empty.
4. **Deploy.** Every `git push` redeploys automatically.

Or from this folder, without GitHub:
```bash
npx vercel          # first time: log in and accept the defaults
npx vercel --prod
```

Vercel serves the site over HTTPS. The microphone check and sync both need HTTPS.

### Any other static host
Upload `index.html`. Netlify, GitHub Pages and Cloudflare Pages all work.

---

## What is inside

| Menu item | What it does |
|---|---|
| **The book** | 50 lessons in 6 units. Click “The book” to open or close the list, and click a unit to see its lessons. Each lesson has 5 steps: Listen (dialogue + role-play), Key phrases, Check your ears, Read it, Your turn. |
| **Tests** | Unit tests, a road-sign test, a roadside English check and a quick mix, plus links to every grammar, verb and slang test. The questions change on every try. |
| **Grammar** | 15 topics: to be, to do, modal verbs, Present Simple, Past Simple, will / going to, Present Continuous, this / that / these / those, there is / are, questions, pronouns, in / on / at, commands, a / an / the / plurals, Present Perfect. Each topic has an explanation in Russian or Tajik, tables, examples with audio, common mistakes and an 8-question test. |
| **Verb forms** | 213 verbs (103 irregular, 110 regular) with V1 / V2 / V3, the he / she form, Russian / Tajik, the sound of -ed, search, a “hide V2 and V3” self-test mode, stars and a 10-question test. |
| **Slang** | What slang is, how many there are, how it works and when to use it, then 100 items in 6 groups (short forms, everyday, texting, Chicago, delivery, trucker / CB radio), with audio, examples and a test. |
| **Dictionary** | 214 words and phrases with Russian and Tajik, flashcards and a test mode. |
| **Videos and audio** | Street-level YouTube searches for each unit, plus the official Illinois / FMCSA papers. |
| **Teacher's guide** | 6-week plan, checkpoints, session plan, pronunciation and grammar notes, roadside-check facts, homework and sync setup. |

**Top bar:** translations on / off (RU / TJ), **Translate** (the translator), teacher notes on / off, settings and voices, light / dark theme.

### Translator (the Translate button at the top)
- Type or paste an English word or phrase to get the meaning in Russian or Tajik.
- Listen to it at normal speed or slowly. For many single words you also get the phonetic spelling and a **real recorded voice**.
- The microphone checks how he says it.
- Type in Russian or Tajik to get the English.
- Select a word anywhere on the page, then press Translate: the box opens already filled in.
- Words and phrases from the book (dictionary, verbs, slang, lesson phrases) work **offline**. Online results need internet and come from:
  - Google Translate's public web endpoint (`translate.googleapis.com`). If it fails, MyMemory (`api.mymemory.translated.net`) is used instead.
  - Free Dictionary API (`api.dictionaryapi.dev`) for the phonetic spelling, the recorded voice and English definitions.

  These are free public services with no key. If one of them is down, the translator still shows the book's results and can always speak the word with the browser voice.

---

## Progress and sync between devices

Ticks, checkpoints, starred words and verbs, test scores and the student's name are saved in the browser (`localStorage`, keys start with `sec:`).

To get **the same progress on every device**, turn on sync once:
1. Open console.firebase.google.com and create a project (free plan).
2. Open **Realtime Database → Create Database** (choose a United States location, locked mode).
3. Open the **Rules** tab, paste the rules from *Teacher's guide → Sync setup* (it has a Copy button), then **Publish**.
4. Copy the database URL, for example `https://your-project-default-rtdb.firebaseio.com`.
5. On the site: click the sync button at the bottom of the menu, paste the URL, keep the class code, then **Turn on sync**.
6. Copy the invite link and open it on the student's phone.

Optional: put the database URL into the file so new devices only need the invite link. Search `index.html` for `SYNC_URL_DEFAULT = ''` and write the URL between the quotes.

Without a database you can still move progress by hand (sync window → “No database? Move progress by hand”).

---

## Voices and microphone

- **Voices** are the ones built into the browser or phone. Microsoft Edge on a computer has the most natural American voices. On an iPhone, go to *Settings → Accessibility → Spoken Content → Voices → English (US)* and download an “Enhanced” or “Premium” voice. Then choose voices and speed in the site's Settings.
- **Microphone check** works in Chrome, Edge and Safari.

---

## Editing content

Everything is inside `index.html`: styles, data and code. The content is plain JavaScript data, so small text fixes are simple: search the file for the sentence and change it.

| Content | Search for |
|---|---|
| Lessons | `L({` (one block per lesson, `id: "pickup"` etc.) |
| Book order / units | `const units = [` |
| Grammar | `window.GRAMMAR = [` |
| Verb forms | `const IRR = [` (irregular) and `const REG = [` (regular) |
| Slang | `window.SLANG = {` |
| Dictionary | `window.DICT` |
| Teacher's guide / videos | `window.TEACHER = {` / `window.RESOURCES = [` |

`{N}` in any text is replaced with the student's name from Settings. Keep quotes and commas intact. After editing, open the page and check the browser console for errors.

---

## Changes in this version

- New **Grammar** page with 15 topics: explanations in Russian / Tajik, examples, common mistakes and tests.
- New **Verb forms** page: 213 verbs, with search, filters, a hide-forms mode and a test.
- New **Slang** page: 100 items in 6 groups, with audio and a test.
- New **Translate** button: meaning in RU / TJ, normal and slow voice, real recorded voice, phonetic spelling, microphone check, works offline for words from the book.
- The Tests page now links every grammar, verb and slang test. All scores sync.
- Fixed: the check mark in the “Covered together / Practiced alone” boxes was not centered.
