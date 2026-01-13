!!! abstract "What We'll Learn"

    - Format the text of the tooltips
    - Add a link to a web page
    - Insert a photo and define its size
    - Integrate a video

## Step-by-step procedures

We saw in
the tutorial [Sail in a map](1-browsing-a-map.md)
How to associate a name and
a description to an element of the map. This name and this description
are displayed in a tooltip (*popup*) that appears
Clicking on the element.

The content of this tooltip can be enriched in several ways:

-   by formatting the text : titles, bold and italic characters
-   by inserting one or more links to a web page
-   by inserting an image or a video

Formatting a tooltip requires using a described syntax
by clicking on the question mark visible to the right of the title
**description**, resumed opposite.

<shot-scraper
    data-output="static/tutoriels/help-box.png"
    data-url="https://umap.openstreetmap.fr/fr/map/new/"
    data-alt="Formatting help panel."
    data-caption="Formatting help panel."
    data-selector=".umap-dialog"
    data-width="510"
    data-height="326"
    data-padding="5"
    data-javascript="
        new Promise((takeShot) => {
            document.querySelector('.leaflet-toolbar-icon.umap-control-caption').click();
            setTimeout(() => {
                document.querySelector('.umap-field-description .umap-help-button').click();
                setTimeout(() => {
                    takeShot();
                }, 1000);
            }, 1000);
        });
    "
    >Formatting help panel.</shot-scraper>

There are other options available [in the FAQ](../support/faq.md#text-formatting).

### 1. Format the text of a tooltip

![miseenforme-resultat.png](../static/tutoriels/5-je-cree-des-infobulles-multimedia/miseenforme-resultat.png)

An example
Better than long explanations: the description below
produce the tooltip on the right.

![miseenforme-syntaxe.png](../static/tutoriels/5-je-cree-des-infobulles-multimedia/miseenforme-syntaxe.png)

Note the following points :

-   a line starting with `#` defines a title line, a **character
    space** must be placed between the character `#` and the text of the title
-   an **vaid area** is automatically added below each
    Title
-   it is possible to combine bold and italic characters in
    using `***`
-   the triangle at the bottom left of the input field allows to enlarge it

### 2. Add a link to a web page

Let's go back [the map of our holiday to
Crozon](http://u.osmfr.org/m/64936/). On the 3rd day of vacation a strong
west wind leads us to go to the Anse de Morgat, well sheltered from the
wind. We decide to document this visit on the map. We
Let's add a marker on the map, and then discover with interest
the Wikipedia article on Morgat : <https://fr.wikipedia.org/wiki/Morgat>.

!!! note Translation Note

    English Wikipedia redirects Morgat to Crozon.


For
add to our tooltip **a link to the article**, just
copy the address of the web page, displayed in the address bar of the
browser, and place it between **double-hooks**. The tooltip to
right corresponds to the description below :

    Morgat is an old fishing village.

    Wikipedia article :
    [[https://fr.wikipedia.org/wiki/Morgat]]

![miseenforme-liensimple.png](../static/tutoriels/5-je-cree-des-infobulles-multimedia/miseenforme-liensimple.png)

We can also **hide the link address** and replace it with a
text. Just follow the address of a bar
vertical (AltGr + 6 on a French keyboard) and text:

    Morgat is an old fishing village.

    [[https://fr.wikipedia.org/wiki/Morgat|Pedilexpa]]

![miseenforme-lienavectexte.png](../static/tutoriels/5-je-cree-des-infobulles-multimedia/miseenforme-lienavectexte.png)

This form is especially useful for long addresses.


### 3. Insert an image

Umap does not allow you to store images, but can display photos
published on a web server.

![miseenforme-photo.png](../static/tutoriels/5-je-cree-des-infobulles-multimedia/miseenforme-photo.png)

The article
Wikipedia shows a beautiful photo of the Anse de Morgat. The photos
visible in Wikipedia are under free *[Creative license
Commons](http://creativecommons.fr/)*. This means that the author
of the photo waives its copyright: we can therefore use
that photo. For this we must:

1.  copy the **dresses of the image** (this operation is accessible
    in the menu displayed by a right click on the photo)
2.  place this address between double hugs :


        Morgat is an old fishing village.

        {{https://upload.wikimedia.org/wikipedia/commons/thumb/2/22/Morgat_8006.jpg/330px-Morgat_8006.jpg}}

        [[https://fr.wikipedia.org/wiki/Morgat|Pedilexpa]]

### Show your photos

If you have a server you can use it store your photos.

### Change the size of an image


The size of the photo is
restricted by the size of the tooltip. To ** enlarge an image**
You need to use a larger tooltip. To do this open the tab
`Interaction options`, click on `Define` in front of
`Popup style` then choose **Name and description (large)**.

![styledepopup.png](../static/tutoriels/5-je-cree-des-infobulles-multimedia/styledepopup.png)

Conversely you can **reduce the size of an image**, by doing
follow the link to the photo of a vertical bar and a number that
defines the **width in pixels** of the image, for example:

    {{https://framapic.org/xxx/yyyy.jpg|400}}}

### Associate an image with a link to a web page

It is possible to embed an image that opens a web page when
The user clicks on it. It is actually about creating a link to
a web page (syntax `[[link|text]]`), using as text
the link to an image (syntax `{{image}}`). Example with the site and the
Framasoft logo :

    [[https://framasoft.org/|{https://framasoft.org/nav/img/logo.png}}]]]

### 4. Insert a video

Inserting a video is more complex. The web browser needs
from a player to display a video. Video sharing sites
like Youtube, DailyMotion or [Framatube](https://framatube.org/)
de Framasoft, offer for each video a link that allows
integrate it into another web page using an *iframe*.

We find on YouTube a [video of the Sea Caves of
Morgat](https://www.youtube.com/watch?v=sKvjd8bGsZM), who visit in
boat. To integrate this video with a tooltip, follow the steps:

1.  open the **Integrate** tab visible *under* the video
2.  Copy the address after `src=` (without the quotation marks), note that it
    has the term *embed* which means *integrate*
    ![partageyoutube.png](../static/tutoriels/5-je-cree-des-infobulles-multimedia/partageyoutube.png)
3.  paste this address between **triple accolades** in the tooltip:

        {{{https://www.youtube.com/embed/sKvjd8bGsZM}}}

4.  for a better result use a wide popup style, note the
    height and width and set the size of the *iframe* with the
    same values :

        {{{https://www.youtube.com/embed/sKvjd8bGsZM|315*560}}}

Here is the result, the video can be directly viewed in our
tooltip :

![miseenforme-video.png](../static/tutoriels/5-je-cree-des-infobulles-multimedia/miseenforme-video.png)

## Let's take stock

We now have all the elements to produce a nice map,
with stylized elements and the tooltips that describe them with a
Formatted content and multimedia: links, photos and videos.

The syntax to format a tooltip is certainly a little
complex, but the good news is that this same syntax can be
used on uMap in two other places:

-   the description of the map, defined in the menu **Edit
    parameters**
-   the description of **calques**, which we discover in the
    [next tutorial](6-handling-datalayers.md).


??? info "License"

    Work initiated by Antoine Riche on [Carto’Cité](https://wiki.cartocite.fr/doku.php?id=umap:10_-_j_integre_des_donnees_distantes) under license [CC-BY-SA 4](https://creativecommons.org/licenses/by-sa/4.0/deed.en).
