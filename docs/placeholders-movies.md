# Placeholders: movie card (All My Movies)

Syntax: `<!--#name -->` or `<!--#name attr="value" -->`. See
[renderer.md](renderer.md) for how they are expanded and
[empty-fields.md](empty-fields.md) for when a line is removed.

## Modifiers

Put at the very beginning of the template, before `<html>`.

| modifier | effect |
|---|---|
| `<!--#orig_names_only -->` | persons shown by original name only |
| `<!--#alt_names_only -->` | persons shown by alternative (localized) name only |
| `<!--#forceplainactors -->` | actors as a comma-separated string instead of `<table class="actors_table">` |

## Labels

`<!--#xxx_lbl -->` inserts the field caption in the current interface
language. One exists for every value below that has a caption:
`title, originaltitle, date, year, genre, duration, resolution, filesize,
actors, mediatype, description, comments, director, subtitles, aspectratio,
country, rating, myrating, mediacount, audcodec, vidcodec, personalmarks,
studio, loan, medialocation, medialabel, wishlist, seen, audinfo, vidinfo,
barcode, movienum, scenario, bitrate, episodes, price, trailer, localpath,
quality, filetype`.

## Values

| placeholder | inserts |
|---|---|
| `title`, `originaltitle` | titles |
| `date` | date added |
| `year` | year (link: filter by year) |
| `genre`, `country`, `studio` | comma-separated links |
| `director`, `scenario` | persons, links |
| `actors` | table of actor / role (`class="actors_table"`, cells `actor_name` and `role`), or plain text with the modifier |
| `duration` | minutes |
| `resolution`, `aspectratio`, `filesize`, `subtitles` | technical strings |
| `vidcodec`, `vidbitrate`, `vidinfo` | video codec, bitrate, full video line |
| `audcodec`, `audbitrate`, `audinfo` | audio codec(s), bitrate(s), `<ul class="audiostreams">` with one `<li>` per track |
| `mediatype`, `mediacount`, `medialabel`, `medialocation`, `quality` | media fields (links where it makes sense) |
| `description`, `comments` | memo fields, line breaks converted |
| `rating`, `myrating` | stars / hearts images or a number, per program settings |
| `mpaa` | age rating |
| `personalmarks` | personal marks (flags) as links |
| `seen`, `wishlist` | check mark / wish-list mark, only when set |
| `loan` | who has the movie and since when |
| `movienum` | number in the list |
| `movieid` | internal record id (for anchors) |
| `barcode` | barcode |
| `price` | price, only when non-zero |
| `url` | link to the movie page; `<!--#url text="Open the movie page" -->` sets the caption |
| `similar` | link "similar movies" when the URL is a Kinopoisk or TMDb page |
| `trailer` | link to the trailer (local file or http) |
| `localpath` | path of the movie file |
| `filetype` | extension of that file |
| `playbutton` | Play button when the file is available; `playbutn.png` in the template folder replaces the image |
| `episodes` | all episodes, each in `<div class="episode">` |
| `userfield` | all custom fields, one per line; `name="Field name"` picks one; `nolink="yes"` makes it plain text |
| `screenshots` | all screenshots as `<img class="screenshot">`; `width="320"` limits each |
| `screennum1`, `screennum2`, ... | one screenshot by number, same `width` attribute |

## Cover and pictures

```html
<IMG SRC="_cover_" ID="cover">
```

Write `_cover_` literally; the program substitutes a per-record source and
delivers the image resized to the box. If there is no cover a placeholder is
drawn and a click on it starts the online cover search.

Old form for screenshots, still working: `<IMG SRC="_screenshot0_" ID="screenshot0">`
(numbered from 0). Prefer `<!--#screennum1 -->`.

## Icons a template may override

Put files with these names next to `template.html`; missing ones are taken
from the shared `moviecards` folder:
`star.png`, `star_half.png`, `star_empty.png`, `heart.png`, `heart_half.png`,
`heart_empty.png`, `check.png`, `playbutn.png`, `smallplay.gif`, `seen.gif`,
`unseen.gif`.

## Style hooks

| class | applied to |
|---|---|
| `screenshot` | every screenshot `<img>` |
| `episode` | the `<div>` around each episode |
| `audiostreams` | the `<ul>` of audio tracks (`.audiostreams { padding:0; margin:0; list-style-type:none }` removes bullets) |
| `actors_table`, `actor_name`, `role` | actors table and its cells |
| `#cover` | the cover image |
