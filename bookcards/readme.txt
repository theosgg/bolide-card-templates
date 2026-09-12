Usable shortcuts are:

Modifiers (place them to the beginning of the template for some tweaks):
----------
<!--#orig_names_only -->
<!--#alt_names_only -->

Just labels (value depends on selected user interface language):
-----------------------------------------------------------------
<!--#title_lbl -->                                         
<!--#originaltitle_lbl -->
<!--#date_lbl -->
<!--#year_lbl -->
<!--#subject_lbl -->
<!--#pages_lbl -->
<!--#dimensions_lbl -->
<!--#circulation_lbl -->
<!--#bindingtype_lbl -->
<!--#synopsis_lbl -->
<!--#comments_lbl -->
<!--#authors_lbl -->
<!--#translators_lbl -->
<!--#illustrators_lbl -->
<!--#editors_lbl -->
<!--#volume_lbl -->
<!--#filesize_lbl -->
<!--#language_lbl -->
<!--#rating_lbl -->
<!--#myrating_lbl -->
<!--#personalmarks_lbl -->
<!--#publisher_lbl -->
<!--#loan_lbl -->
<!--#location_lbl -->
<!--#wishlist_lbl -->
<!--#unread_lbl -->
<!--#booknum_lbl -->
<!--#price_lbl -->
<!--#serie_lbl -->
<!--#contents_lbl -->	
<!--#dateread_lbl -->
<!--#playtime_lbl -->
<!--#localpath_lbl -->
<!--#filetype_lbl -->
<!--#loc_lbl -->
<!--#dewey_lbl -->

Field values from the database:
-------------------------------
<!--#title -->                                         
<!--#originaltitle -->
<!--#date -->
<!--#year -->
<!--#subject -->
<!--#pages -->
<!--#dimensions -->
<!--#circulation -->
<!--#bindingtype -->
<!--#synopsis -->
<!--#comments -->
<!--#authors -->
<!--#translators -->
<!--#illustrators -->
<!--#editors -->
<!--#volume -->
<!--#filesize --> - displayed if non-zero
<!--#language -->
<!--#rating -->
<!--#myrating -->
<!--#personalmarks -->
<!--#publisher -->
<!--#publisheryear --> for Publisher and Year
<!--#loan -->
<!--#location -->
<!--#wishlist -->
<!--#unread -->
<!--#bookid -->
<!--#url -->
<!--#ISBN -->
<!--#loc -->
<!--#dewey -->
<!--#booknum -->
<!--#price --> - displayed if non-zero
<!--#serie -->
<!--#contents -->
<!--#dateread -->
<!--#playtime -->
<!--#localpath -->
<!--#filetype -->


<!--#playbutton --> - inserts Play button if the book "Local path" is filled in and file is available. 

The <!--#url --> shortcut can be given your own caption for the link:
<!--#url text="Open the book page" -->

The rating and the personal rating are shown either with the star/heart
images or as a number, depending on the program settings. Some of the
fields - the authors, the subject, the publisher, the year, the series, the
personal marks and so on - are inserted as links: a click on such a link
filters the collection by that value.

Cover
-----
The cover of the book is inserted this way:
<IMG SRC="_cover_" ID="cover">

Write "_cover_" exactly as it is shown: the program replaces this very text
with the one carrying the record id, so that the viewer's image cache never
shows the cover of the previously opened book. The image is scaled to the box
your template gives to it, so set the size on the tag or with CSS.
If the book has no cover, a placeholder is drawn instead (with the title on it,
if the corresponding option is on in the program settings), and a click on the
placeholder starts the cover download.

Screenshots
-----------
<!--#screenshots -->
To limit the screenshot's width you can use "width" attribute this way:
<!--#screenshots width="320" -->

<!--#screennumX --> - screenshot number X. Parameter "width" is also applicable.
For example, <!--#screennum1 --> inserts the first screenshot, and
<!--#screennum2 width="320" --> the second one, limited to 320 pixels.

Both shortcuts expand into <IMG> tags with CLASS="screenshot".

Screenshots can also be accessed by their number (0,1,2, and so on) this way:
<IMG SRC="_screenshot0_" ID="screenshot0">
This form still works, but it is better to use <!--#screennumX -->: the SRC
written by hand is the same for every book, and the viewer's image cache can
show a screenshot of the previously opened one.

<!--#userfield -->  The all user fields will be inserted, one per line.
You can also specify what user field to display using "name" attribute.
For example <!--#userfield name="book font" --> will be replaced by the value 
of user field named "book font" (without quotes).

Empty fields
------------
If the field is empty, the entire line with its shortcut is removed from the
template. Note that the WHOLE line is removed, so do not put two shortcuts on
the same line unless they should always appear or disappear together. Only the
lines below the <body> tag are processed this way.

Styles
------
You can define style named "screenshot". It will be used in IMG tag for the 
screenshots.

Icons
-----
The stars, the hearts, the checkmark and the Play button are taken from the
files named star.png, star_half.png, star_empty.png, heart.png, heart_half.png,
heart_empty.png, check.png and playbutn.png. They are looked for in the folder
of your template first, so a template can be shipped with its own set of the
icons; the files from the bookcards folder are used for the missing ones.
