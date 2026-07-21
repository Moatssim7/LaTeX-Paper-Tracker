# LaTeX Writing Tracker

A single-file, drag-and-drop planner for **multi-author papers** — surveys, journal articles, theses, grant proposals. Lay out your section structure, assign co-authors, track drafting status, and see workload and unassigned parts at a glance. Everything runs in the browser; nothing is uploaded anywhere.

![status: static badge](https://img.shields.io/badge/dependencies-none-brightgreen) ![single file](https://img.shields.io/badge/build-single%20HTML%20file-blue) ![license](https://img.shields.io/badge/license-MIT-lightgrey)

## Why

On a paper with many co-authors, the hard part isn't writing — it's knowing **who owns what**, **what's done**, and **what has no owner yet**. This tool turns a `main.tex` (or a blank board) into a live assignment map you can edit in a meeting and share as a one-page PDF or a text summary.

## Features

- **Three-level outline** — sections → subsections → sub-subsections.
- **Assignment at the subsection level**, with per-author **workload counts**. A subsection's chips show *everyone* working anywhere inside it; a sub-subsection can carry its own owner, shown inline when it differs from the subsection.
- **Status tracking** — click a dot to cycle *not started → in progress → done*. Subsection status auto-aggregates from its sub-subsections.
- **Full structure editing** — rename (double-click), add, and delete at every level.
- **Drag-and-drop reordering** — grab the `⠿` handle to move sections, move subsections within or **across** sections (drop on a section header), and move sub-subsections within or **across** subsections (drop on a bold row).
- **Import from LaTeX** — paste your source; it builds the outline from `\section/\subsection/\subsubsection`, reads owners from `\TODO{Name}` / `\TODO{Name + Name}` tags (`??` or empty → **NEEDS OWNER**), estimates status from how much prose each part contains, grabs `\title{}`, and flags `XX` placeholder cells in tables.
- **Import / Export** a plan as a `.json` file to share or version-control it.
- **Copy summary** — a plain-text digest grouped per author plus the unassigned list, ready to paste into email/Slack.
- **Print / PDF** — collapses to a clean one-page landscape layout.
- **Auto-saves** to your browser's local storage. No accounts, no server, no tracking.

## Use it

**Option A — just open the file.** Download `index.html` and open it in any modern browser.

**Option B — host it free on GitHub Pages.** Push this repo, then in **Settings → Pages** set *Source: Deploy from a branch*, branch `main`, folder `/root`. Your tracker will be live at
`https://<your-username>.github.io/<repo-name>/`.

## Quick start

1. Click **⟳ Import from LaTeX** and paste your `main.tex`, **or** click **Load demo** to see an example, **or** **Start blank**.
2. Double-click the title to rename the paper.
3. Add authors with **＋ Author**; assign them with the **＋** on any row.
4. Reorder by dragging the `⠿` handle; set status by clicking the dots.
5. **Export** to save a shareable `.json`, or **Print** for a one-page PDF.

## LaTeX conventions it understands

- `\title{...}` → paper title.
- `\section{...}`, `\subsection{...}`, `\subsubsection{...}` → the outline.
- `\TODO{Alice}` or `\TODO{Alice + Bob}` right after a heading → owner(s) of that part. `\TODO{??}` or no tag → NEEDS OWNER.
- A `\TODO{}` on a `\subsubsection` rolls up into its subsection's chips (and stays visible inline).
- Cells containing `XX` inside a `table`/`table*` environment are counted and flagged as remaining placeholders.

> The `\TODO` command is just an example convention. If your project uses a different macro, either add `\newcommand{\TODO}[1]{}` to your preamble, or adjust the `parseOwners` regex in `index.html`.

## Privacy

100% client-side. Your plan is stored only in your browser's local storage and in any `.json` you export. Nothing is sent over the network.

## License

MIT — see [LICENSE](LICENSE).
