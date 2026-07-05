# Anders' website — read me first 👋

Hi Anders! This folder is a complete, ready-to-go personal website. It's already
filled in with your details, your CountsDiff paper, your photo, and your logo.

**You do not need to know how to code.** You will not run any programs on your
computer. Everything happens on the GitHub *website*, in your browser. The plan:

1. **[Put it on GitHub and switch it on](#part-1--put-it-online)** — about 10 minutes, one time only.
2. **[Change the bits that are still placeholders](#part-3--change-things-later)** — whenever you like, by editing files in the browser.

### How this works (the one idea to understand)

Your website is just a folder of text files. You put that folder on GitHub.
GitHub has a robot that reads those files and builds the actual website for you,
automatically, for free. **Every time you save a change on GitHub, the robot
rebuilds the site within about a minute.** You never build anything yourself.

That's it. Now let's get it online.

---

## Part 1 — Put it online

Everywhere below, wherever you see `USERNAME`, replace it with the GitHub
username you choose. Write it down — you'll use it a few times.

### Step 1 — Make a GitHub account

Go to <https://github.com/signup> and sign up (free). Your username becomes part
of your web address, so pick something you're happy with — e.g. if you pick
`andershoel`, your site will live at `https://andershoel.github.io`.

### Step 2 — Create the project ("repository")

1. Go to <https://github.com/new>.
2. In **Repository name**, type exactly: **`USERNAME.github.io`**
   (all lowercase, with your real username). This exact name is what makes the
   free web address work — don't name it anything else.
3. Choose **Public**.
4. Leave every checkbox **unticked** (don't add a README or anything — this
   folder already has one).
5. Click **Create repository**.

### Step 3 — Upload this folder

On the page that appears after creating the repo, find the link that says
**"uploading an existing file"** and click it. Then:

1. Open **this folder** on your computer.
2. Select **everything inside it** and drag it onto the GitHub page.
3. Scroll down and click the green **Commit changes** button.

> ### ⚠️ Important: don't miss the hidden `.github` folder
> There's a folder here named `.github` (with a dot at the front). It's the part
> that tells GitHub's robot how to build your site — **without it, nothing will
> work.** Your computer may hide it because of the dot.
>
> - **On a Mac:** in Finder, press **⌘ + Shift + .** (period) to show hidden
>   files, then do the drag-and-drop.
> - **Easiest, most reliable option:** instead of dragging, on the upload page
>   click **"choose your files"** and select everything — or use GitHub Desktop
>   (see the note at the very bottom), which never misses hidden files.
>
> If after Step 5 your site looks broken/unstyled, a missing `.github` folder is
> the most likely reason.

### Step 4 — Turn the site on

1. In your repository, click **Settings** (top menu).
2. In the left sidebar, click **Pages**.
3. Under **Build and deployment → Source**, open the dropdown and choose
   **GitHub Actions**. (Not "Deploy from a branch".)

You don't type or configure anything else. That's the whole setup.

### Step 5 — Watch it go live

1. Click the **Actions** tab (top menu). You'll see a job running with a yellow
   dot; when it turns into a green tick (about a minute), your site is live.
2. Open **`https://USERNAME.github.io`** in your browser. 🎉

From now on, **any change you save on GitHub automatically rebuilds the site.**
You never touch the Actions or Settings tabs again.

---

## Part 2 — Where you may and may not touch

Think of it like a house: you can redecorate the rooms, but leave the plumbing
and wiring alone.

### ✅ Safe to edit — these hold *your* content

| File / folder | What's in it |
|---|---|
| `config.yml` | **Your main file.** Name, bio, email, links, sidebar text. 90% of your edits are here. |
| `content/projects/` | Your projects/papers (one folder each). |
| `static/` | Your images: `profile.jpg` (photo), `logo.png` (logo + browser-tab icon), and `cv.pdf` if you add one. |
| `assets/css/core/theme-vars.css` | Optional: the colours and fonts. |

### ⛔ Do NOT touch — this is the machinery

Leave these completely alone. Editing them can break the site:

- `.github/` — the build robot's instructions
- `themes/` — the website's engine
- `layouts/` — the page templates
- `archetypes/`, the other files in `assets/`, `LICENSE.md`, `.gitignore`,
  `CLAUDE.md`, and this `README.md`
- Anything named `public/` or `resources/` if they ever appear (auto-generated)

If you're ever unsure whether something is safe to change — it's in `config.yml`
or it's one of your own images/projects, you're fine. Anything else: don't.

---

## Part 3 — Change things later

**How to edit any file (no downloads, all in the browser):**

1. On your repository page, click into the file you want to change.
2. Click the **pencil icon** (✏️, top-right of the file) to edit.
3. Make your change, then click **Commit changes** at the top-right.
4. Wait ~1 minute and refresh your live site. Done.

Below is exactly where each thing lives.

### Your bio, name, and links → `config.yml`

Open `config.yml`. It has comments (lines starting with `#`) explaining each
part. The things you'll likely change:

- **The bio paragraphs** — `params.profileMode.subtitle`. The first paragraph
  is already written; the second (Norway / PwC / running / Tolkien) is too.
  Edit freely. `<br><br>` makes a blank line; `[text](https://link)` makes a link.
- **The three sidebar boxes** — under `params.sidebar`:
  - `work:` — the "Current Work" bullets. **These are still placeholders** —
    replace the three "Current project or focus" lines with what you're actually
    working on.
  - `interests:` and `using:` — topic tags (already filled with sensible ones).
- **Your links** — under `params.socialIcons`. Your LinkedIn and email are on.
  Four others (CV, Google Scholar, GitHub, ORCID) are **hidden** because they
  still have fake addresses. To switch one on: put in your real web address,
  then **delete the line that says `hidden: true`** under it. To hide any link,
  add `hidden: true` back. **Add your GitHub link** once you're set up.

### Your photo and logo → `static/`

Replace the file, keep the **same filename**:

- Photo: replace `static/profile.jpg` (a square photo looks best).
- Logo + browser-tab icon: replace `static/logo.png`. This one image is used
  both next to your name *and* as the little icon in the browser tab (the
  "favicon") — change the file and both update automatically on the next build.
  (Browsers cache tab icons aggressively, so if the tab icon looks unchanged,
  force-refresh or peek in a private window.)
- CV: add a file named `static/cv.pdf`, then switch on the CV link in
  `config.yml` (see above).

### Add another project

Each project is a folder inside `content/projects/`. Your CountsDiff paper is in
`content/projects/countsdiff/`. To add another:

1. In `content/projects/`, make a new folder (any short name).
2. Copy the text from `content/projects/countsdiff/index.md` into a new
   `index.md` inside your new folder, and edit the title, authors, description,
   date, and the link.
3. (Optional) drop an image in that folder and set `image:` to its filename for
   a thumbnail — or delete the `cover:` block for a plain text card.

Newest `date:` shows first. To temporarily hide a project, add a line
`hiddenInHomeList: true` near the top of its `index.md`.

### Change the colour or fonts (optional)

In `assets/css/core/theme-vars.css`:

- `--darkcolor` is the blue accent (`#1e6dde`). Change that one value to re-skin
  the whole site.
- `--font-name` is the font of your name (currently **Jost**).

---

## If something goes wrong

- **Site is blank or looks unstyled.** Usually the hidden `.github` folder
  didn't upload (see the warning in Step 3), or Pages isn't set to **GitHub
  Actions** (Step 4). Re-check both.
- **A change didn't show up.** Give it a minute, then hard-refresh
  (**⌘ + Shift + R**). Check the **Actions** tab shows a green tick, not a red X.
- **Red X in the Actions tab.** Click it to see the error. The usual cause is a
  typo in `config.yml` — this file is picky about spacing: use spaces, never the
  Tab key, and keep the same indentation as the lines around it. If in doubt,
  undo your last edit (open the file → **History** → revert) and try again.
- **The tab icon (favicon) won't change.** It's just browser caching — force
  refresh or open the site in a private/incognito window.

---

<details>
<summary>Optional: editing on your computer with GitHub Desktop (nicer for frequent edits)</summary>

If you'd rather not edit in the browser every time, install
[GitHub Desktop](https://desktop.github.com/) (free, no command line). It lets
you edit files in this folder on your Mac and click one **"Push"** button to
publish. It also uploads the hidden `.github` folder correctly. Totally optional
— the browser method above works perfectly on its own.

</details>

---

Built with [Hugo](https://gohugo.io/), [PaperMod](https://github.com/adityatelange/hugo-PaperMod),
and [hugo-website](https://github.com/pmichaillat/hugo-website).
