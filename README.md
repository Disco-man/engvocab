# English Vocabulary

A small vocabulary trainer in a single HTML file. You add words with translations and synonyms, then take a round and type your answers.

The interface itself is in Russian.

domain: satvocab.gt.tc

## Features

- Word list with English words, Russian translations, and optional synonyms on both sides.
- Two quiz modes: **Russian → English** and **English → Russian**.
- Synonym support: a word appears once per valid answer, and each time you need to give a different one.
- Typo tolerance: one wrong, missing, or extra letter is accepted.
- Per-word toggle to leave a word out of a round without deleting it.
- Import and export of the word list as `words.json`.
- Round summary with the final score.

## Getting started

Open `index.html` in a browser.

By default, words and the selected mode are stored in the browser's `localStorage`, so clearing site data erases them. For permanent storage, download .json file with the word list.

## Usage

### Adding words

The **Новое слово** (new word) block has four fields:

| Field | Required | Example |
|---|---|---|
| English | yes | `quick` |
| синонимы (English synonyms, comma separated) | no | `fast, rapid` |
| перевод на русский (Russian translation) | yes | `быстрый` |
| русские синонимы (Russian synonyms, comma separated) | no | `скорый, шустрый` |

Enter moves to the next field, and in the last field it adds the word. The English and Russian fields can also contain several variants separated by a comma (`,`), semicolon (`;`), or slash (`/`): the first becomes the main word and the rest become synonyms.

### Word list

- The checkbox on the left controls whether the word is included in a round. An unticked word stays in the list but is not asked.
- The × button deletes the word permanently.

### Modes

The switch above the **Начать раунд** (start round) button chooses the direction. The choice is remembered in the browser.

- **русский → английский**: you see the Russian word and type the English one.
- **английский → русский**: you see the English word and type the Russian translation.

### Synonyms in a round

A word is asked once per valid answer in the current mode. For example, `quick` has two English synonyms, so in Russian → English mode the word «быстрый» comes up three times, and each time you must give a different variant (`quick`, `fast`, or `rapid`). Repeating an answer you already gave shows a message that the variant was already used.

The same applies in the other direction for Russian synonyms.

### How answers are checked

- Case and extra spaces are ignored.
- **One mistake in a letter is accepted**: a replaced, missing, or extra letter (`recive` is accepted for `receive`). The correct spelling is shown in the feedback.
- Variants shorter than 3 letters must match exactly.
- Swapping two adjacent letters counts as two mistakes.

### Backup and restore

- **Скачать слова** (download words) saves the list as `words.json`.
- **Загрузить слова** (upload words) replaces the current list with the selected file.

File format:

```json
[
  {
    "english": "quick",
    "synonyms": ["fast", "rapid"],
    "russian": "быстрый",
    "russianSynonyms": ["скорый"],
    "enabled": true
  }
]
```

