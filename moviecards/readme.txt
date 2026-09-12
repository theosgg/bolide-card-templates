Here you can find a list of supported shortcuts in HTML templates for the movie details area.

Modifiers (place them at the beginning of the template for some tweaks):
----------
<!--#orig_names_only -->
<!--#alt_names_only -->
<!--#forceplainactors -->  - do not use <table> for actors, use plain comma-delimited string instead

Labels (value depends on selected user interface language):
-----------------------------------------------------------------
<!--#title_lbl -->                                         
<!--#originaltitle_lbl -->
<!--#date_lbl -->
<!--#year_lbl -->
<!--#genre_lbl -->
<!--#duration_lbl -->
<!--#resolution_lbl -->
<!--#filesize_lbl -->
<!--#actors_lbl -->
<!--#mediatype_lbl -->
<!--#description_lbl -->
<!--#comments_lbl -->
<!--#director_lbl -->
<!--#subtitles_lbl -->
<!--#aspectratio_lbl -->
<!--#country_lbl -->
<!--#rating_lbl -->
<!--#myrating_lbl -->
<!--#mediacount_lbl -->
<!--#audcodec_lbl -->
<!--#vidcodec_lbl -->
<!--#personalmarks_lbl -->
<!--#studio_lbl -->
<!--#loan_lbl -->
<!--#medialocation_lbl -->
<!--#medialabel_lbl -->
<!--#wishlist_lbl -->
<!--#seen_lbl -->
<!--#audinfo_lbl -->
<!--#vidinfo_lbl -->
<!--#barcode_lbl -->
<!--#movienum_lbl -->
<!--#scenario_lbl -->
<!--#bitrate_lbl -->
<!--#episodes_lbl -->
<!--#price_lbl -->
<!--#trailer_lbl -->
<!--#localpath_lbl -->
<!--#quality_lbl -->
<!--#filetype_lbl -->

Field values from the database:
-------------------------------
<!--#title -->                                         
<!--#originaltitle -->
<!--#date -->
<!--#year -->
<!--#genre -->
<!--#duration -->
<!--#resolution -->
<!--#filesize -->
<!--#actors -->
<!--#mediatype -->
<!--#description -->
<!--#comments -->
<!--#director -->
<!--#subtitles -->
<!--#aspectratio -->
<!--#country -->
<!--#rating -->
<!--#myrating -->
<!--#mediacount -->
<!--#audcodec -->
<!--#vidcodec -->
<!--#personalmarks -->
<!--#studio -->
<!--#loan -->
<!--#medialocation -->
<!--#medialabel -->
<!--#wishlist -->
<!--#seen -->
<!--#movieid -->
<!--#url -->
<!--#mpaa -->
<!--#audinfo -->
<!--#vidinfo -->
<!--#barcode -->
<!--#movienum -->
<!--#scenario -->
<!--#audbitrate -->
<!--#vidbitrate -->
<!--#price --> - displayed if non-zero
<!--#trailer --> - link to the local file or remote http
<!--#localpath -->
<!--#quality -->
<!--#filetype --> - file name extension from the LocalPath field
<!--#similar --> - Displays the link for getting a list of similar movies if supported by the database from the current movie URL.


<!--#playbutton --> - inserts Play button if the movie file is available. You can define your own button by placing playbutn.gif file to the template's folder.

Cover
-----
The cover of the movie is inserted this way:
<IMG SRC="_cover_" ID="cover">

Write "_cover_" exactly as it is shown: the program replaces this very text
with the one carrying the record id, so that the viewer's image cache never
shows the cover of the previously opened movie. The image is scaled to the box
your template gives to it, so set the size on the tag or with CSS.
If the movie has no cover, a placeholder is drawn instead, and a click on the
placeholder starts looking for the cover online.

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
written by hand is the same for every movie, and the viewer's image cache can
show a screenshot of the previously opened one.

<!--#userfield -->  The all user fields will be inserted, one per line.
You can also specify what user field to display using "name" attribute.
For example <!--#userfield name="image quality" --> will be replaced by the value 
of user field named "image quality" (without quotes).
<!--#userfield name="image quality" nolink="yes" --> - non-clickable field value

<!--#episodes -->  Entire available details about episodes will be inserted. You can define style "episode"

The <!--#url --> shortcut can be given your own caption for the link:
<!--#url text="Open the movie page" -->

The rating and the personal rating are shown either with the star/heart images
or as a number, depending on the program settings. Most of the fields - the
actors, the genre, the studio, the year, the personal marks and so on - are
inserted as links: a click on such a link filters the collection by that value.

Empty fields
------------
If the field is empty, the entire line with its shortcut is removed from the
template. Note that the WHOLE line is removed, so do not put two shortcuts on
the same line unless they should always appear or disappear together. Only the
lines below the <body> tag are processed this way.

Icons
-----
Besides the Play button, the template folder can hold its own stars, hearts and
checkmark: star.gif, star_half.gif, star_empty.gif, heart.png, heart_half.png,
heart_empty.png, check.png, smallplay.gif, seen.gif, unseen.gif. The files from
the moviecards folder are used for the missing ones.

Styles
------
You can define style named "screenshot". It will be used in IMG tag for the 
screenshots.
Style "episode" is used for the episodes details. All episode details are displayed inside the <div class="episode"></div>
Style "audiostreams" is used for audio streams UL list. For example, to remove extra space and the bullets from the list use the following CSS:
.audiostreams {padding: 0; margin:0; list-style-type: none;}
Style "actors_table" (<table> tag), "actor_name" for actors <td>, "role" for character <td>