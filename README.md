# Terminal "Good" Image Protocol

This repository aims to formalize the `"Good" Image Protocol` that
was posted on terminal-wg issue [#26](https://gitlab.freedesktop.org/terminal-wg/specifications/-/issues/26).

## Goal of this repository

I want to finally formalize what other people have been already put great work in (see references),
and ideally also come up with a reference implementation (as technical preview).

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
- [ ] hopefully get enough terminal and TUI app devs attracted to collaborate in a positive, friendly, and productive manner.

## FAQ

- **Why LaTeX and not Markdown?** Expressivity and the fact that you can convert to Markdown: https://pandoc.org/demos.html
- **Why GitHub and not GitLab on freedesktop?** Better reachability.

