# 1170 Site Repo

ENGL 1170 — First-Year Writing Co-Req, paired with ENGL 1181.

## Read these first, before doing any work in this repo

The rules governing this work are deliberately not kept in this repo, because this repo is public. Nothing here repeats them, so skipping these files means working without them. **Read each one in full — do not skim for the sections that look relevant.**

1. `~/MEGA/work-with-claude-code/CLAUDE.md` — how Sarah wants the work done.
2. `~/MEGA/work-with-claude-code/classes/CLAUDE.md` — rules shared across every class.
3. `~/MEGA/work-with-claude-code/classes/ENGL-1170/CLAUDE.md` — this course: term, sections, readings, assignments, calendars.

Everything below this point is about this repo's own files, and belongs here.

## Log every change to this repo

Changes here get written up at:

`~/MEGA/work-with-claude-code/classes/ENGL-1170/changelog/`

**One HTML file per date, named `YYYY-MM-DD.html`**, plus an `index.html` listing them all with a short summary each. Add both in the same session as the change — the reasoning is what the log is for, and it evaporates fast. Full spec in `classes/CLAUDE.md` under "Class Website Change Logs."

**Textbook links:** 1170 is the co-req for ENGL 1181 and shares its textbook, the departmental OER at <https://macomb.pressbooks.pub/engl1181/>. Chapter numbers have moved between editions and will move again. Current verified links are in `classes/ENGL-1181/1181-oer-chapter-links.md`. Anything pointing at `sites.google.com/view/1181a/` is dead.

**Domain:** this site serves from `1170.skarlis.org` and the 1181 site from `1181.skarlis.org`. `karlismcc.com` is retired — nothing should point at it.

## The calendar is shared code — edit all three repos

`calendar/calendar.js` and `calendar/calendar.css` are **byte-identical** in `1170`, `1181` and `1190`. Not similar; identical. Check before and after any change:

```
md5sum ~/Websites_work/{1170,1181,1190}/calendar/calendar.{js,css}
```

**A fix made in one repo and not the others silently forks them.** That is not hypothetical: this file drifted before, and on 15 Aug 2026 1170 was found still carrying urgency colours at 2.8:1 and 3.3:1 that 1181 had fixed months earlier. Nobody noticed because nothing compares them.

**The sharing is also what catches bugs.** The same day, porting the calendar to a third site forced its colours to be recalculated against a different palette, which exposed a card border sitting at 1.18:1 against the page in dark mode — invisible, and live on a site that had just been through a contrast pass. One palette hid it; three did not.

### The stylesheet is token-driven, so it must stay colour-agnostic

`calendar.css` reads `--accent`, `--bright`, `--muted`, `--text`, `--bg` and `--border` from each site's own `style.css`. That is how one file renders purple here, teal on 1181 and navy on 1190. **Never hard-code a site's colour into it.** The event-type colours (due amber, reading blue, online green) are deliberately the same everywhere and are the only fixed values in the file.

**Contrast has to be re-checked per site, because the palettes differ.** A ratio that clears 7:1 against one accent can fail against another. The dark card-edge mix is 48% rather than 46% for exactly this reason: 46% cleared 3:1 on the teal site and landed at 2.88 and 2.93 on the purple and navy ones. The measured ratios are recorded in comments beside the tokens — read them rather than re-deriving, and re-run the maths for **all three** sites if you change a colour.

### What is *not* shared

The page shells are per-site and always differ: filenames, `data-calendar-id`, headings, tab titles and nav labels. Only the two files above are common.
