# SMUNOPOLY — RA Training board

A digital Monopoly board for Resident Assistant training, played by a
facilitator on a projector.

Games save the way a Word document does: **Save Game** downloads a `.json` file,
**Continue Game** opens one back up. That file is the save, and it travels — put
it on a flash drive and the game resumes on any other computer.

```
index.html          the entire thing — board, pieces, money, rules, saving
READ ME FIRST.txt   instructions for whoever runs the training
inspo/              the original board photo and rules document
```

One file. No database, no accounts, no npm packages, no build step. That is on
purpose: there is nothing to configure and nothing to expire.

---

## Putting it online (about 5 minutes, one time)

You need a GitHub account and a Vercel account. You have both.

### 1. Put the code on GitHub

Go to <https://github.com/new>, name the repository `smunopoly`, and click
**Create repository**. Ignore the commands GitHub then shows you. Run these
instead, from this folder:

```bash
git init
git add .
git commit -m "Smunopoly RA training board"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/smunopoly.git
git push -u origin main
```

Replace `YOUR-USERNAME` with your GitHub username.

### 2. Deploy it on Vercel

1. Go to <https://vercel.com/new>
2. Find `smunopoly` and click **Import**
3. Change nothing. Framework Preset should say **Other**.
4. Click **Deploy**

A minute later you have an address like `https://smunopoly.vercel.app`. Send it
to whoever is running training. That's the whole setup — there is no step 3.

---

## What it costs

Nothing, and there is no usage to keep an eye on.

The site is a single static page. Once a browser has loaded it, the page does
not talk to any server again — moving pieces, changing money and saving games
all happen on the facilitator's own computer. Vercel's free Hobby plan gives
100 GB of bandwidth a month; this page is roughly 55 KB, so a month of training
uses a rounding error of it.

**One caveat.** Vercel's fair use guidelines restrict the free Hobby plan to
*non-commercial, personal use*, and a university department running staff
training is a grey area. Nobody is likely to mind a page that four people load
once a year, but if the school wants it strictly above board, Vercel Pro is
$20/month and can be switched on for the training month and off again after.

If that ever became a hassle, `index.html` also works with no web host at all —
see below.

---

## It also works with no internet

`index.html` is completely self-contained. Double-click it and the game runs in
the browser, saving and loading files exactly the same way. Copy it to a flash
drive and it runs on any computer.

Worth knowing the night before training: if the Wi-Fi is down or the site is
unreachable, nothing is lost. Keep a copy of `index.html` alongside your saved
game files.

---

## Changing the board later

Square names and rents are in `index.html`, in the list under the comment
`2. Board data`. Team names, colours and the $1,500 starting cash are just
below under `3. Teams`.

Edit, then:

```bash
git add .
git commit -m "Updated square names"
git push
```

Vercel redeploys itself within a minute. Saved game files still open fine
afterwards — they hold the game, not the board layout.

---

## If something goes wrong

**"It forgot my game"** — the browser keeps its own copy as a safety net, but
that copy is per-computer and a school laptop wiping browser data will clear
it. The downloaded `.json` file is the real save. Save one at the end of every
day.

**"That does not look like a saved Smunopoly game"** — wrong file was picked.
The right one starts with `smunopoly-` and ends in `.json`, and lives in the
Downloads folder.

**Badge says "● Unsaved changes"** — there have been moves since the last
Save Game. Click **💾 Save Game**. The badge is also why closing the tab warns
you.

**You want to wipe the board and start clean** — click **Start Over**. It asks
twice, and it does not touch any file you already downloaded.
