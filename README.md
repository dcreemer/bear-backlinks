# bear-backlinks

Automated backlinks for the excellent Bear app, in case you'd like those for a Zettelkasten-style notes library.

## TODO

- [x] Document installation & usage for this script
- [ ] Figure out scheduling for the script (launchd job)
- [ ] Figure out security/accessibility preferences required to run this script reliably, particularly with a background launchd job. (When running from iTerm, add iTerm to the list of apps allowed to use Accessibility.)
- [ ] Fork [python-xcall](https://github.com/robwalton/python-xcall) & update it with my Python 3 version (see [xcall.py](https://github.com/cdzombak/bear-backlinks/blob/master/xcall.py))
- [ ] Fork [xcall](https://github.com/martinfinke/xcall) & build fat binaries, to ensure future Apple Silicon compatibility

## What it Does

In a Bear note, write the following to opt into automatic backlinking:

```
## Backlinks

*This space intentionally left blank.*

---
```

When this script runs, it looks for notes which contain the string `## Backlinks\n`. It'll search Bear for any notes that link to this set of notes; and it replaces everything between `## Backlinks` and `---` with a list of links. For example, it produced this output for one of my notes:

```
## Backlinks
- [[Anatomy of a Zettel]]
- [[Bear as Zettelkasten]]
- [[Zettelkasten Basics]]

---
```

This is useful for certain note-taking practices such as [Evergreen Notes](https://notes.andymatuschak.org/Evergreen_notes) and [Zettelkasten](https://zettelkasten.de), though there is [debate](https://zettelkasten.de/posts/backlinks-are-bad-links/) about its effectiveness.

## Requirements / Compatibility

**Tested on macOS Mojave, on various Intel Macs.**

Should work on newer versions of macOS, except that changes to automation/privacy/Apple Events/security policies in newer macOS versions might make the automated interaction with Bear flakier, or make authorizing this program to use Accessibility more complex. (As it is, running this script via eg. iTerm requires iTerm to be allowed to use Accessibility automation).

I imagine this could run under Rosetta 2 on Apple Silicon, but this is untested. The main potential issue is that the checked-in copy of xcall is AFAIK not built for ARM.

**A working Python 3.x installation is required.**

Install it with eg. `brew install python`. See [Homebrew's docs on Python](https://docs.brew.sh/Homebrew-and-Python) for background information.

## Installation

Simply `git clone https://github.com/cdzombak/bear-backlinks.git`. You can run the program from the checked-out repo.

## Usage

1. Ensure Bear is running and is not in any weird state (eg. it is not currently displaying a modal window).
1. Run `./main.py`.

## About

- Issues: https://github.com/cdzombak/bear-backlinks/issues/new
- Author: [Chris Dzombak](https://www.dzombak.com)
