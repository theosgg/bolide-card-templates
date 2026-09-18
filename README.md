# Card templates for All My Movies and All My Books

The details pane of [All My Movies](https://www.bolidesoft.com/allmymovies.html)
and [All My Books](https://www.bolidesoft.com/allmybooks.html) is an HTML
template: a folder with `template.html`, a few images and placeholders like
`<!--#title -->`. This repository holds the templates that ship with the
programs, the documentation needed to write your own, and a gallery so you
can pick one without trying them all.

* [docs/renderer.md](docs/renderer.md) - what the built-in HTML renderer
  can and cannot do (it is not a browser), units and zoom, images
* [docs/empty-fields.md](docs/empty-fields.md) - the rule that removes a whole
  line when a field is empty, and the layout mistakes it causes
* [docs/placeholders-movies.md](docs/placeholders-movies.md),
  [docs/placeholders-books.md](docs/placeholders-books.md) - every placeholder,
  modifier, icon and style hook

## Installing a template

1. Download the repository (Code → Download ZIP) or just the folder you want.
2. Copy the theme folder into the program's template folder:
   `moviecards\` for All My Movies, `bookcards\` for All My Books. They are
   next to the program's exe, usually
   `C:\Program Files (x86)\AllMyMovies\moviecards\` and
   `C:\Program Files (x86)\AllMyBooks\bookcards\` (writing there needs
   administrator rights).
3. In the program: menu **View → HTML template** and pick the folder name.

The program looks for `template.html` in every subfolder; folders without
it (and `_old`) are ignored. No restart is needed after copying.

## Movie card gallery (All My Movies)

| | | |
|---|---|---|
| **Standard**<br>![Standard](screenshots/movies/Standard.webp) | **Standard Dark**<br>![Standard Dark](screenshots/movies/Standard%20Dark.webp) | **Dark**<br>![Dark](screenshots/movies/Dark.webp) |
| **Black Page**<br>![Black Page](screenshots/movies/Black%20Page.webp) | **Blue 3D**<br>![Blue 3D](screenshots/movies/Blue%203D.webp) | **Dune**<br>![Dune](screenshots/movies/Dune.webp) |
| **Golden**<br>![Golden](screenshots/movies/Golden.webp) | **High Contrast**<br>![High Contrast](screenshots/movies/High%20Contrast.webp) | **Indian**<br>![Indian](screenshots/movies/Indian.webp) |
| **Indian Dark**<br>![Indian Dark](screenshots/movies/Indian%20Dark.webp) | **KinopoiskOld**<br>![KinopoiskOld](screenshots/movies/KinopoiskOld.webp) | **LikelMDb**<br>![LikelMDb](screenshots/movies/LikelMDb.webp) |
| **Lite Gray**<br>![Lite Gray](screenshots/movies/Lite%20Gray.webp) | **Popcorn**<br>![Popcorn](screenshots/movies/Popcorn.webp) | **Premiere**<br>![Premiere](screenshots/movies/Premiere.webp) |
| **Redline**<br>![Redline](screenshots/movies/Redline.webp) | **Rusty Art**<br>![Rusty Art](screenshots/movies/Rusty%20Art.webp) | **Screenplay**<br>![Screenplay](screenshots/movies/Screenplay.webp) |
| **Short**<br>![Short](screenshots/movies/Short.webp) | **Sidelined Gray**<br>![Sidelined Gray](screenshots/movies/Sidelined%20Gray.webp) | **Storefront**<br>![Storefront](screenshots/movies/Storefront.webp) |

## Book card gallery (All My Books)

| | | |
|---|---|---|
| **Standard**<br>![Standard](screenshots/books/Standard.webp) | **Standard Dark**<br>![Standard Dark](screenshots/books/Standard%20Dark.webp) | **Dark**<br>![Dark](screenshots/books/Dark.webp) |
| **Bookshelf**<br>![Bookshelf](screenshots/books/Bookshelf.webp) | **Golden**<br>![Golden](screenshots/books/Golden.webp) | **High Contrast**<br>![High Contrast](screenshots/books/High%20Contrast.webp) |
| **Indian**<br>![Indian](screenshots/books/Indian.webp) | **Ozon**<br>![Ozon](screenshots/books/Ozon.webp) | **Redline**<br>![Redline](screenshots/books/Redline.webp) |
| **Rusty Art**<br>![Rusty Art](screenshots/books/Rusty%20Art.webp) | **Short**<br>![Short](screenshots/books/Short.webp) | **Sidelined Gray**<br>![Sidelined Gray](screenshots/books/Sidelined%20Gray.webp) |
| **Storefront**<br>![Storefront](screenshots/books/Storefront.webp) | | |

Screenshots were taken at 150% display scaling with the demo collection, card pane about 1780x1980 px, reduced to 1000 px wide.

## Writing your own

Start from `Standard` (or `Standard Dark` for dark themes): copy the folder
under a new name and edit `template.html`. Then read the three documents
above - the renderer is picky in ways a browser is not. The short version:

* **Layout with tables**, not floats or flex. Give tables the HTML
  `width="100%"` attribute, size fixed columns in `em`.
* **Sizes in `pt` and `em`, not `px`**, so the card follows the zoom and the
  monitor DPI. `font-size` without a unit means pixels here.
* **One optional field per source line.** If a field is empty for a record,
  the whole line with its placeholder is removed - label included if it is
  on the same line, other placeholders included too.
* **`<IMG SRC="_cover_" ID="cover">`** for the cover, exactly like that.
* **UTF-8 with BOM** if the file contains anything beyond plain ASCII.
* No `border-radius`, shadows, gradients, `background-size`, web fonts,
  JavaScript.

Test with records that lack fields (no rating, no screenshots, a wish-list
item without a file) and with the card zoom at 50% and 200%.

## Contributing

Pull requests with new themes are welcome. Please include a screenshot,
keep the folder self-contained (images in a subfolder, no absolute paths),
use only images you have the right to publish under this repository's
license, and check the theme against the empty-field checklist above.
Fixes to the documentation are just as useful: if something rendered
differently from what a document says, that is a bug in the document.

## License

MIT. The templates are the ones shipped with the programs; use, modify and
redistribute them freely.
