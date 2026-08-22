# 🥅 Jack's Match

**Tell real words from decodable nonsense words, then spell by ear**

[![Play it](https://img.shields.io/badge/▶_play-jacks--games.github.io/match-brightgreen?style=for-the-badge)](https://jacks-games.github.io/match/)

![One HTML file, no build step](https://img.shields.io/badge/one_HTML_file-no_build_step-blue)
![No dependencies](https://img.shields.io/badge/dependencies-none-blue)
![Ages 5 to 7](https://img.shields.io/badge/ages-5--7-orange)
![No accounts, no tracking](https://img.shields.io/badge/no_accounts-no_tracking-lightgrey)

![Jack's Match: the nonsense word "fod" with two large buttons, GOAL for a real word and ALIEN for a silly word](screenshot.png)

## What this is

A two-half football match that trains the two halves of literacy: **decoding in the first half,
spelling in the second.**

The first half is a playable version of the **Year 1 Phonics Screening Check**, the statutory
assessment in English primary schools. In it, children read 40 words, half of them *pseudo-words*
— made-up but phonically regular strings like `fod` or `shob`, presented as alien names. The
point of the nonsense words is that they cannot be recognised by shape or guessed from the first
letter, so they show whether a child is genuinely decoding rather than remembering. This game
puts the same idea on a pitch: real word → shoot at goal, alien word → give it to the alien.

Crucially the app **does not read the word out first**. Hearing it would turn decoding into
listening. It speaks the word *after* a correct answer as confirmation, and after a wrong one it
sounds the word out and brings it back later in the half.

The second half is dictation: the app says a word and the child types it on an on-screen
keyboard with **no letters supplied** — the sequence has to come from memory.

## ⏱️ First half — real word or alien word?

| | |
|---|---|
| 🥅 | A **real** word → tap **GOAL** |
| 👽 | A **made-up** word → tap **ALIEN** |

Alien words in the pool: **fod · zat · bep · vum · shob · chid · thog · keeb · narp · quog · sprot · dree**

Stuck? **🔊 Sound it out** reads the graphemes — `sh-i-p`, not `s-h-i-p` — but never the whole
word. That part stays with the reader.

## ⏱️ Second half — write the word

![The writing half: a voice says a word and it is tapped out on an ABC keyboard](screenshot-writing.png)

| | |
|---|---|
| 🔊 | Listen to the word |
| ⌨️ | Tap the letters — no tiles, no clues |
| ✅ | Correct letters stay put, the rest clears, try again |
| 👻 | After two attempts a faint ghost word appears |
| ⚽ | Spell it and the crowd goes up |

## 🏆 Full time

The whistle blows, the goals are counted, and the best score so far is remembered.

## 🎯 What it practises

- 🔍 &nbsp; Blending sounds through a whole word instead of guessing from the start
- 🧩 &nbsp; Recognising digraphs (`sh`, `ch`, `th`, `oa`, `igh`) as single sounds
- ✍️ &nbsp; Producing a spelling from memory, not from a choice of tiles

## ⚙️ Notable details

- The keyboard is in **ABC order by default** — a five-year-old hunts through the alphabet, not
  a QWERTY layout. A setting switches it.
- A missed word is pushed back into the queue so it comes round again, but the queue is capped
  so the half always ends.
- Grapheme splitting is greedy and digraph-first, which is what makes the sounding-out correct.

## 🎈 The other games

| Game | What it is | |
|---|---|---|
| 📖 [**Jack's Words**](https://github.com/jacks-games/words) | Hear a word, build it from letter tiles, then read it in a sentence | [▶ play](https://jacks-games.github.io/words/) |
| 🥅 [**Jack's Match**](https://github.com/jacks-games/match) | Tell real words from decodable nonsense words, then spell by ear | [▶ play](https://jacks-games.github.io/match/)  👈 **this one** |
| ✏️ [**Jack's Letters**](https://github.com/jacks-games/letters) | Finger-trace all 26 lowercase letters in the correct stroke order | [▶ play](https://jacks-games.github.io/letters/) |
| 🔢 [**Jack's Numbers**](https://github.com/jacks-games/numbers) | Count, add and subtract with footballs — to 10, then to 20 | [▶ play](https://jacks-games.github.io/numbers/) |
| ♟️ [**Jackies Schach**](https://github.com/jacks-games/chess) | Full FIDE rules with a coach that marks the safe squares (German) | [▶ play](https://jacks-games.github.io/chess/) |

All five on one start page: **[jackbenn.ing](https://jackbenn.ing)**

## 🛠 Built like this

Every game in this organisation is **one self-contained `index.html`** — no build step, no
framework, no package manager, no analytics, and no network calls once the page has loaded.
That is a deliberate constraint: a game a child depends on should still work in five years,
and a parent should be able to read the whole thing in one sitting.

- **Speech** — the browser's Web Speech API, preferring a British English voice. It always
  waits for a tap first, because Chrome and iOS block audio without user activation.
- **Progress** — kept in `localStorage` on the device. Nothing is collected, sent or stored
  anywhere else.
- **Made for** an iPad mini in either orientation: finger-sized targets, no hover-only
  interactions, `prefers-reduced-motion` respected.

Run it locally:

```bash
python3 -m http.server 8000
```

The start page at [jackbenn.ing](https://jackbenn.ing) is built from
[google814/Jack](https://github.com/google814/Jack), which is the source of truth. The repos
in this organisation are copies kept in step by `tools/sync-game-repos.sh` in that repo, so
each game also has its own page and its own link.
