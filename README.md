# Razan Saylami — portfolio site

A plain HTML site (no build step, no dependencies) with free hosting (Cloudflare Pages) and a free visual
editor (Pages CMS). Everything needed to run it is in this folder.

## What's in here
- `index.html` — the whole site: layout, styles and behaviour.
- `content/projects.json` — every project (Direction and Production Design). Edited through Pages CMS.
- `content/settings.json` — name, email, social links, About text, colours, list names.
- `images/` — all photos. `images/laurels/` holds the festival laurels, `images/nav/` the top-bar lettering.
- `fonts/` — Monigue (project titles). See "Font licence" below.
- `.pages.yml` — tells Pages CMS which fields to show. **Hidden file** — on a Mac press Cmd+Shift+. in
  Finder to see it, and make sure it gets uploaded. Without it the editor won't work.

## 1. Put it on GitHub
Make a free GitHub account and a new repository (e.g. `razan-site`), then get this folder's contents into it.

**Easiest: GitHub Desktop** (desktop.github.com). Create a new repository, copy everything from this folder
into the repository folder, then Commit and Publish. It handles hidden files and any number of files.

**Browser upload** works too, but GitHub only accepts about 100 files per upload and this site has 200+.
Upload in batches (root files first, then `images/` in a few chunks), committing after each.

## 2. Host it on Cloudflare Pages (free)
1. Cloudflare dashboard → create a Pages project → connect the GitHub repo.
2. Framework preset: None. Build command: empty. Output directory: `/`.
3. Deploy. You get a `*.pages.dev` address straight away.
4. For a real domain, add it under the project's Custom domains tab.

Every change pushed to GitHub — including every save in the editor — redeploys the site in about a minute.
(Cloudflare renames things in its dashboard now and then; their Pages docs are the reference if a button has moved.)

## 3. Editing content
1. Go to https://app.pagescms.org, sign in with GitHub, open the repo.
2. **Projects**: add, delete or drag to reorder. The "List" field puts a project under Direction or Production Design.
3. **Cover** is the full-screen image that appears when hovering a title on the home page. Use a wide still,
   around 2400px across, JPG under 600 KB.
4. **Stills** are the gallery on the project page (tiled two across, click to enlarge with arrows/swipe).
5. **Video link**: paste a YouTube or Vimeo link and it embeds at the top of the project's media.
   (Instagram links can't be embedded.)
6. **Show cover among the stills**: on by default. Turn it off when the cover is only for the hover preview and
   shouldn't also appear on the project page — Alchemy in Venice is set up this way (video only).
7. **Festival laurels**: upload white-on-transparent PNGs; they show as a row under the credits.
8. **Keep in view on phones**: picks which side of the cover stays visible when a phone crops it.
9. To let Razan edit on her own, add her GitHub account as a collaborator (repo Settings → Collaborators).

## Font licence — do this before launch
Project titles use Monigue. The file supplied is the **demo**, licensed for personal use only, and covers
letters only (numbers and symbols fall back to another font, so a title like "312 Days" mixes two faces).
A portfolio counts as commercial use. Buy the full licence at https://zarmatype.com/font/monigue/ and replace
`fonts/monigue.woff` (and `monigue.ttf`) with the licensed files, keeping the same filenames.

## Previewing locally
Double-clicking `index.html` shows a built-in snapshot of the content as it was when the site was packaged
(browsers block reading the JSON files from disk, and the YouTube embed won't play from a file). To see live
content and video, run `python3 -m http.server` in this folder and open http://localhost:8000.

## Notes
- **Top-bar lettering** (`images/nav/`): two files per button, `<name>-en.png` and `<name>-ar.png`, both white
  on transparent. The site tints them with the colours in Settings. To replace one, export both layers at the
  same size so they stay lined up, and keep the filenames.
- **Colours** are set in Settings: background `#5B6A46`, text `#FCF9F4`, supporting text `#B2B6A4`.
- **Opening screen**: the home page opens on the name alone and scrolls up into the header. It's tied to scroll
  position, and is skipped for anyone who has reduced motion turned on, or who opens a project link directly.
- **Image naming**: project images follow `<project-slug>-hero.jpg` for the cover, then `-a.jpg`, `-b.jpg`, and so on.
