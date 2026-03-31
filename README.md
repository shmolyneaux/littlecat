# littlecat

A Python command-line tool that slowly prints a file to stdout, character by character, as if someone were typing it. It uses regex-based pattern matching to vary the typing speed depending on the kind of character being "typed," producing a more natural, human-like effect.

## Usage

```
python3 littlecat.py <file>
```

For example, to "type out" a source file:

```
python3 littlecat.py littlecat.py
```

## How It Works

`littlecat` reads a file one character at a time and prints each character with a delay. The delay is determined by matching the text printed so far against a set of regex patterns:

- **Repeated letters/numbers** — fast (0.1 s), simulating fluent typing
- **Indentation start** — moderate pause (0.25 s), simulating thinking at the start of a new indent level
- **Mid-indentation** — no pause, for the middle of whitespace runs
- **Symbols** (e.g. `>`, `<`, `:`, `;`, `-`, `=`, `+`, `(`, `)`) — longer pause (0.8 s), simulating hesitation
- **Default** — 0.25 s per character

## Requirements

- Python 3 (no external dependencies)

## Features

- Human-like variable-speed typing simulation
- Configurable pattern-based delay system using regex
- Works with any text file

## Limitations

- Reads the entire file into memory incrementally; not suitable for very large files as the regex matching runs against the accumulated text
- The regex patterns and delay timings are hardcoded and noted by the author as needing adjustment
- No support for reading from stdin
- No option to adjust overall typing speed from the command line

## History

Development on littlecat took place on 2016-12-04:

- 2016-12-04 — Initial commit with README, LICENSE (Unlicense), and `.gitignore`
- 2016-12-04 — Added `littlecat.py` with character-by-character file printing, regex-based variable typing delays for indentation, repeated characters, and symbols (noted that regexes and timings still need adjustment)
