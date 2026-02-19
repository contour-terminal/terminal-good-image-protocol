# Terminal \*Good\* Image Protocol

**IMPORTANT: THIS PROJECT IS IN ALPHA STAGE & ACTIVE DEVELOPMENT**

This repository aims to finish and formalize the `*Good* Image Protocol` that
was posted on terminal-wg issue [#26](https://gitlab.freedesktop.org/terminal-wg/specifications/-/issues/26).

## Goal of this repository

I want to finally formalize what other people have been already put great work in (see references),
and also come up with a reference implementation (for verifying the spec and as a technical preview).

It would be nice if this repository serves as a communication hub for improving this spec
that ideally enough terminal emulators will adopt so we could call this the future defacto image protocol
for terminals, so that developers have it easier in the future on how to get images into their
terminal applications.

## Roadmap

- [x] get the actual non-subjective content extracted out of the other sources into this one specification draft.
- [x] create CI job for auto-generating PDF/markdown of the latest draft to be downloadable
- [x] create CI job for providing prereleases of the draft specification.
- [ ] Move Changelog into .tex file and let CI's release.yml extract it from there
- [ ] Create Github pages that have an auto-generated PDF/markdown version of this specification.
- [ ] Hopefully get enough terminal and TUI app devs attracted to collaborate in a positive, friendly, and productive manner.
- [ ] CLI tool for `cat`ing images onto the screen (a shell script should be sufficient).
- [ ] CLI tool for testing the feature availability (could be integrated in the above tool with a `--test` flag)

## Protocol Synopsis

The protocol uses **DCS** (Device Control String) sequences with a single-character operation identifier:

| Operation      | Sequence                    | Description                          |
|----------------|-----------------------------|--------------------------------------|
| Upload         | `DCS u <message> ST`        | Upload an image to the storage pool  |
| Render         | `DCS r <message> ST`        | Render a previously uploaded image   |
| Upload+Render  | `DCS s <message> ST`        | Upload and render in one step        |
| Release        | `DCS d <message> ST`        | Release a named image from the pool  |

**Feature detection:** DA1 response code `11`.

**Image formats:** `1` (RGB), `2` (RGBA), `3` (PNG).

**Quick example (bash):**

```bash
# Upload a PNG image named "logo"
echo -ne "\033Pun=logo,f=3;!$(base64 logo.png)\033\\"

# Render it in a 20x10 cell grid
echo -ne "\033Prn=logo,c=20,r=10\033\\"

# Release it
echo -ne "\033Pdn=logo\033\\"
```

See the [spec document](spec/vt-good-image-protocol.tex) for the full specification.

## FAQ

- **Why LaTeX and not Markdown?** Expressivity and the fact that you can convert to Markdown: https://pandoc.org/demos.html
- **Why GitHub and not GitLab on freedesktop?** Better reachability.

