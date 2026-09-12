# How empty fields are handled

Before a record is rendered, the program walks the template **line by line**
and deletes every line that contains a placeholder whose value is empty for
this record. The check is a plain substring match on the source line, so:

* **The whole source line goes**, not just the placeholder. Labels, table
  cells, `<tr>` tags - anything on that line disappears with it.
* **Only lines after the line containing `<body`** are processed. The
  `<style>` block and anything in `<head>` are never touched.
* **The match is on the exact spelling** `<!--#name -->` with one space
  before `-->`. A placeholder written as `<!--#name-->` still renders, but is
  never removed when empty.
* A line with **two placeholders** is removed when **either** is empty.

## What that means for a layout

Put each optional field with its label on one line:

```html
<tr><td class="lbl"><!--#country_lbl --></td><td><!--#country --></td></tr>
```

If country is empty the whole row vanishes and nothing dangling is left.
Split it over two lines and you get an orphaned label:

```html
<tr><td class="lbl"><!--#country_lbl --></td>      <!-- stays -->
    <td><!--#country --></td></tr>                 <!-- removed -->
```

Things that always appear (title, cover) and lines without placeholders can be
formatted freely.

## Traps seen in real templates

* `<!--#mediatype --> (<!--#mediacount -->)` on one line: `mediacount` counts
  as empty when it is 1 (the usual case), so the media type disappears for
  almost every movie. Keep them on separate lines.
* `<!--#rating --> <!--#myrating -->` on one line: records without a personal
  rating lose the online rating stars too.
* A section heading on its own line above an optional field leaves a heading
  with nothing under it. Keep `<h2><!--#description_lbl --></h2>` and
  `<!--#description -->` together, or drop the heading.
* `originaltitle` counts as empty when it **equals** the title
  (case-insensitive), not only when the field is blank.
* A decorative box (`<div class="panel">` ... `</div>`) with several optional
  lines inside stays as an empty frame when all of them are gone. Either put
  the whole box on one source line, or place something nearly always present
  in it (the rating).
* `vidbitrate` and `audbitrate` are **not** in the list below and never get
  removed; keep them on the same line as `vidcodec` / `audcodec`, which are.
* `date`, `movieid`, `bookid` and all `*_lbl` labels are never removed on
  their own; they only disappear when they share a line with a removable
  placeholder.

## When a placeholder counts as empty

### Movies (All My Movies)

| placeholder | removed when |
|---|---|
| `title` | title empty |
| `originaltitle` | empty, or equal to the title ignoring case |
| `description`, `comments` | empty |
| `genre`, `country`, `director`, `scenario`, `actors`, `studio` | empty |
| `year`, `duration`, `resolution`, `filesize`, `aspectratio`, `subtitles`, `mpaa` | empty |
| `vidcodec`, `vidinfo` | video info shorter than 6 characters |
| `audcodec`, `audinfo` | audio info shorter than 9 characters |
| `rating`, `myrating` | rating is 0 |
| `mediatype`, `medialocation`, `medialabel`, `quality` | empty |
| `mediacount` | **count is 1** |
| `movienum` | number is 0 |
| `barcode`, `loan`, `personalmarks` | empty |
| `url` | empty (kept for wish-list items even when empty) |
| `similar` | URL is not a Kinopoisk or TMDb link |
| `wishlist` | not on the wish list |
| `seen` | not marked as seen |
| `screenshots`, `screennumX`, `_screenshotN_` | no screenshots |
| `episodes` | no episodes |
| `userfield` | no custom fields at all |
| `price` | 0 |
| `trailer` | empty |
| `localpath`, `filetype` | file path empty |
| `playbutton` | file not available (missing file, or drive not present) |

### Books (All My Books)

| placeholder | removed when |
|---|---|
| `title` | empty |
| `originaltitle` | empty, or equal to the title ignoring case |
| `synopsis`, `comments`, `contents` | empty |
| `subject`, `serie`, `volume`, `language`, `location`, `bindingtype` | empty |
| `authors`, `translators`, `illustrators`, `editors` | empty |
| `year`, `pages`, `circulation` | 0 |
| `dimensions` | empty |
| `filesize` | empty or "0" |
| `rating`, `myrating` | 0 |
| `loan`, `personalmarks`, `ISBN`, `loc`, `dewey`, `url`, `playtime` | empty |
| `publisher` | empty |
| `publisheryear` | publisher empty **and** year 0 |
| `wishlist` | not on the wish list |
| `unread` | already read |
| `dateread` | no date, or the book is unread |
| `price` | 0 |
| `screenshots`, `screennumX` | no extra pictures |
| `userfield` | no custom fields at all |
| `localpath`, `filetype` | file path empty |
| `playbutton` | file not available |
