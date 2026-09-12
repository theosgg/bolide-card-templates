# Placeholders: book card (All My Books)

Syntax: `<!--#name -->` or `<!--#name attr="value" -->`. See
[renderer.md](renderer.md) for how they are expanded and
[empty-fields.md](empty-fields.md) for when a line is removed.

## Modifiers

Put at the very beginning of the template, before `<html>`.

| modifier | effect |
|---|---|
| `<!--#orig_names_only -->` | persons shown by original name only |
| `<!--#alt_names_only -->` | persons shown by alternative (localized) name only |

## Labels

`<!--#xxx_lbl -->` inserts the field caption in the current interface
language. One exists for:
`title, originaltitle, date, year, subject, pages, dimensions, circulation,
bindingtype, synopsis, comments, authors, translators, illustrators, editors,
volume, filesize, language, rating, myrating, personalmarks, publisher, loan,
location, wishlist, unread, booknum, price, serie, contents, dateread,
playtime, localpath, filetype, loc, dewey`.

## Values

| placeholder | inserts |
|---|---|
| `title`, `originaltitle` | titles |
| `date` | date added |
| `year` | year of publication (link) |
| `authors`, `translators`, `illustrators`, `editors` | persons, links |
| `subject` | subjects / genres, links |
| `publisher` | publisher (link) |
| `publisheryear` | publisher and year in one string |
| `serie`, `volume` | series and volume |
| `pages`, `dimensions`, `circulation`, `bindingtype`, `language` | edition data |
| `ISBN` | ISBN (upper case in the name) |
| `loc`, `dewey` | Library of Congress / Dewey classification |
| `synopsis`, `comments`, `contents` | memo fields |
| `rating`, `myrating` | stars / hearts or a number, per program settings |
| `personalmarks` | personal marks as links |
| `unread`, `wishlist` | marks, only when set |
| `dateread` | date finished |
| `loan` | who has the book and since when |
| `location` | shelf / location |
| `booknum` | number in the list |
| `bookid` | internal record id |
| `price` | price, only when non-zero |
| `filesize` | e-book file size, only when non-zero |
| `playtime` | audiobook length |
| `url` | link to the book page; `<!--#url text="Open the book page" -->` sets the caption |
| `localpath` | path of the e-book / audiobook file |
| `filetype` | extension of that file |
| `playbutton` | Open/Play button when the file exists |
| `userfield` | all custom fields, one per line; `name="Field name"` picks one |
| `screenshots` | all extra pictures as `<img class="screenshot">`; `width="320"` limits each |
| `screennum1`, `screennum2`, ... | one picture by number, same `width` attribute |

## Cover and pictures

```html
<IMG SRC="_cover_" ID="cover">
```

Write `_cover_` literally. Without a cover a placeholder is drawn (with the
title on it if that option is on) and a click on it starts the cover download.

## Icons a template may override

`star.png`, `star_half.png`, `star_empty.png`, `heart.png`, `heart_half.png`,
`heart_empty.png`, `check.png`, `playbutn.png` next to `template.html`;
missing ones come from the shared `bookcards` folder.

## Style hooks

| class | applied to |
|---|---|
| `screenshot` | every extra picture `<img>` |
| `#cover` | the cover image |
