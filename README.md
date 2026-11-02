# max-nathan.github.io (new design)

A plain HTML + CSS academic site. There is no build step, no Jekyll, and nothing to install.

## Preview

Double-click `index.html`. It opens in any browser straight from your disk.

PDFs are linked at their live addresses (see below), so a PDF you've just added to `downloads/`
won't open from the preview until you've pushed it to GitHub.

## Edit

Open the folder in BBEdit or VS Code. Every page is a single `.html` file, with comments
marking the parts you'll change.

| File | What it is |
|---|---|
| `index.html` | Home: bio with photo, research themes, recent work |
| `research.html` | The four research areas, each with links to recent work |
| `publications.html` | In-progress papers as figure cards; published articles and chapters as compact lists |
| `teaching.html` | Courses, office hours, PhDs and RAs |
| `assets/style.css` | All colours, fonts and layout. The colour variables are at the top |
| `images/papers/` | One figure per in-progress paper (cropped from your drafts and slides) |
| `images/mn26_3.jpg` | Your photo on the home page (also the "hi-res photo" link). To change it, update both `src` and the link in `index.html` |
| `images/mn26_2.jpg` | Alternative photo (blue shirt), not currently used |
| `tumblr/theme.html` | Matching Tumblr theme, with install steps at the top of the file |

PDFs (CV, drafts, slides) are linked at `https://max-nathan.github.io/downloads/...`, so they
keep working from your existing `downloads/` folder. To add a PDF, drop it in `downloads/` and link it the same way.

### Things repeated on every page

The header and footer are copied into all four pages. If you change either, change it in all four.

- **Header menu:** Home, Research, Publications, Teaching, Blog, Play. Blog and Play go to
  other sites and open in a new window (`target="_blank" rel="noopener"`); keep that on any new external menu link.
- **Name in the header:** shown on every page except Home, which opens with your name as its title.
- **Footer:** "© 2026 Max Nathan" plus profile links (CV, Scholar, Bluesky, ORCID, ResearchGate).
  Update the year each January.
- **Email:** written as "max.nathan at ucl.ac.uk" (Home and Teaching) rather than as a link, to deter spam bots.

### Research themes

The four themes appear in three places: the bio paragraph and the Research themes list on `index.html`,
and the sections of `research.html`. Keep them in the same order in all three:

1. The economics of cultural diversity
2. Innovation systems
3. The creative industries and cities
4. Public policy for cities

### Look and feel

- White background, one sans-serif font (Inter), no decorative graphics.
- Colours come from Paul Tol's "muted" scheme, which is colour-blind safe
  (https://personal.sron.nl/~pault/). Indigo and rose were chosen to echo the portrait.
  - `--accent` indigo `#332288`: links
  - `--accent-2` rose `#CC6677`: decoration only (menu underline, headline bars). It's too light for text
  - `--label` wine `#882255`: small coloured text (e.g. "WORKING PAPER", "Revise and resubmit") and link hover
- Dark mode is automatic when a visitor's device uses it; its colours are in the second block at the top of `style.css`.
- Text starts at the same left edge on every page; images (paper figures, your photo) sit on the right.
- Two sizes you might want to tweak, both in `style.css`:
  - `--wide` (near the top, currently `56rem`): the width of every page, header included.
    Smaller brings the menu and photo closer to the text.
  - The `170px` in the `.intro` rule: the width of the home page photo (it shrinks to 120px on phones).

## Publications page

### In progress

One `<article class="paper">` card per paper, with the figure on the right. Keep them in this order:

1. Revise and resubmit
2. Under review
3. Work in progress

To add one:

1. Save a key chart as a PNG or JPG in `images/papers/` (a screenshot of a slide is fine; roughly 3:2 looks best).
2. Copy a whole `<article class="paper">` block and edit it: status line, one-sentence headline,
   abstract (folded until clicked), and link buttons. Delete any buttons you don't need.

### Published articles, books and chapters

One `<li>` per item, newest first, with no figure. Copy a whole `<li> ... </li>` block to add one.
When a working paper is published, delete its card from In progress and add it here.

## Still to do

- **Publish**: the new design isn't live yet. Follow the switchover guide below.
- **Tumblr**: paste `tumblr/theme.html` into Tumblr when you're ready (steps at the top of that file).

## Switching the live site to the new design (one-off)

Two folders are involved, both in `Dropbox/code/claude/_website/`:

- `new-site/`: the new design (this folder).
- `maxnathan.github.io/`: your GitHub repository, i.e. the live site. Its branch is called `master`.

The plan is to move the old design out of the repository into an archive folder,
copy the new design in, check it, then commit and push. Everything you remove stays in the
repository's history on GitHub too, so nothing is lost even without the archive.

Before you start, press **Cmd+Shift+.** in Finder to show hidden files (names starting with a dot).
Press it again at the end to hide them.

### Step 1: Make an archive folder

Create `Dropbox/code/claude/_website/archive/old-site-2026/`. It must sit **outside** `maxnathan.github.io/`:
anything inside the repository gets published.

### Step 2: Move the old design into the archive

Move these out of `maxnathan.github.io/` and into `archive/old-site-2026/`:

| Item | What it is |
|---|---|
| `index.html`, `research.html`, `publications.html`, `teaching.html` | The old pages (the new ones replace them in Step 4) |
| `README.md` | The old three-line description (this README replaces it) |
| `fonts/`, `webfonts/` | The old MyFonts web fonts; the new site uses Inter from Google Fonts |
| `scripts/` | The old stylesheets (`squareglasses.css` etc.) |
| `images/png/`, `images/gif/` | The old header logo (`maxnathanlse.png`); `images/` itself stays, because the new photos go in it |
| `old/`, `old_site/`, `x/` | Earlier versions of the site and test files |

`old/` was never on GitHub (your `.gitignore` excludes it), so the archive is its only copy. The others are
also in the repository's history.

### Step 3: Keep these where they are

| Item | Why |
|---|---|
| `downloads/` | Every PDF link on the new site points here: CV, drafts, slides, and the No 10 North draft |
| `logo_blog/` | Keep for now in case your current Tumblr theme or blog loads this image. Archive it after installing the new Tumblr theme |
| `.git/` | The repository itself. Never move or delete it |
| `.gitignore`, `.gitattributes` | Git settings |

Optional tidy-up inside `downloads/`: `No._10_North_logo.png` is a spare copy (the site uses
`images/papers/no10north.png`), and `old_cvs/` holds superseded CVs. Both can go to the archive. Leave
everything else, because old links elsewhere on the web may point to those PDFs.

### Step 4: Copy the new design in

Copy these from `new-site/` into `maxnathan.github.io/`:

- `index.html`, `research.html`, `publications.html`, `teaching.html`
- `assets/` (the stylesheet)
- `images/mn26_3.jpg`, `images/mn26_2.jpg` and `images/papers/` (into the existing `images/` folder)
- `tumblr/` (the matching Tumblr theme)
- `README.md` (this guide)
- `.nojekyll` (hidden; it tells GitHub Pages to serve the files as they are)

Don't copy `.DS_Store` files; they're Finder clutter.

### Step 5: Update the CV

Save your updated CV over `downloads/webcv.pdf`, keeping that exact name, so every CV link keeps working.

### Step 6: Check it before publishing

Double-click `maxnathan.github.io/index.html` and click through all four pages, plus Blog and Play.
PDF links open the live site, so a new PDF (such as the No 10 North draft) won't open until you've pushed.

### Step 7: Commit and push in GitHub Desktop

1. Open GitHub Desktop with the `maxnathan.github.io` repository selected.
2. In the **Changes** list, expect three kinds of entry: deleted (the archived files),
   new (the new design and PDFs) and modified (the four pages, the README, `webcv.pdf`).
   If anything you meant to keep shows as deleted, move it back before going on.
3. Write a summary such as "New site design" and click **Commit to master**.
4. Click **Push origin**.

### Step 8: Check the live site

After a minute or two, open https://max-nathan.github.io/ and press **Cmd+Shift+R** to skip any cached copy.
Check each page, a couple of PDF links (including the No 10 North draft) and the CV.

If something's badly wrong, go to GitHub Desktop's **History** tab, right-click the "New site design" commit,
choose **Revert changes in commit**, then push again. That puts the old site back.

### Step 9: Afterwards

- **One copy only:** from now on, edit the files in `maxnathan.github.io/`. Move `new-site/` into the archive
  so you never edit the wrong copy.
- **Tumblr:** install the new theme, then archive `logo_blog/` (Step 3).
- **Routine updates:** edit a page, double-click it to check, then commit and push in GitHub Desktop.

## Switching the blog to Substack

Search all files for `medium.com/@maxnathan` and replace it with your Substack URL.
