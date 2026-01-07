!!! abstract "What We'll Learn"

    - distinguish the editing mode of the consultation mode
    - identify the steps needed to create a map
    - produce a first card and broadcast it!

## Step-by-step procedures

The object of our first card is simple: position one or more
places (home, holiday, work, etc.). Proceedings in stages.

### 1. The editing mode

!!! osm-instance "For the general public, associations..."

    Go to the uMap instance of OSM <https://umap.openstreetmap.fr/>

!!! french-instance "For public officials"

    Visit the uMap public officials website <https://umap.incubateur.anct.gouv.fr/>
    and connect to the top left. The connection uses ProConnect.

<shot-scraper
    data-output="static/tutoriels/create-map.png"
    data-url="https://umap.openstreetmap.fr/fr/"
    data-alt="Card creation button from the reception."
    data-width="176"
    data-height="119"
    data-selector=".button.button-primary"
    data-padding="5"
    >Card creation button from the reception.</shot-scraper>


Then appears on your browser a card that appears as follows:

![A blank card annotated with the main editing actions](../../static/tutoriels/2-je-cree-ma-premiere-carte-umap/umap_edition.png)

We find on the left the buttons available during the
[map viewing](1-browsing-a-map.md).

Several elements visible above and to the right of the map are
visible only when creating or modifying a card, that is,
in the *edit mode* :

-   the **name of the card** at the top left as well as the access rights
-   the possibility of **⃔ cancel** / **reproduce⃕** actions with arrows
-   the **Preview** and **Save** buttons at the top right
-   on the right a series of 4 buttons to add elements to
    the map : markers, lines, polygons and roads
-   below a series of buttons to configure the card

### 2. Name the map

A card must have a name that provides information on what the card represents.
To set the card name, click the button
**Edit name or caption** or more simply on `No name card` in
the headband :

<shot-scraper
    data-output="static/tutoriels/modify-name.png"
    data-url="https://umap.openstreetmap.fr/fr/map/new/"
    data-alt="Edit button of the card name."
    data-width="46"
    data-height="47"
    data-selector=".leaflet-toolbar-icon.umap-control-caption"
    data-padding="5"
    >Edit button of the card name.</shot-scraper>

A panel appears on the right of the map, it contains at the top one
input field for the **name** of the card, which contains the text
`No name card` : place the cursor in this field, delete the text
existing and enter the name of your card, for example `My home`.

<shot-scraper
    data-output="static/tutoriels/modify-name-panel.png"
    data-url="https://umap.openstreetmap.fr/fr/map/new/"
    data-alt="Panel of the card name editing panel."
    data-width="410"
    data-height="382"
    data-selector=".panel.right"
    data-padding="5"
    data-javascript="document.querySelector('button.map-name').click()"
    >Card name editing panel.</shot-scraper>

Note that the name at the top left of the card is immediately changed.
You can also enter longer text in the field
**description**, which will appear in the legend panel - we y
Let's come back.

Now save the card with the **Save** button: a
text is displayed at the top of the map, like the one below:

#### For the general public on the OSM instance

<shot-scraper
    data-output="static/tutoriels/create-map-alert.png"
    data-url="https://umap.openstreetmap.fr/fr/map/new/"
    data-alt="Alert message containing the edit link."
    data-width="790"
    data-height="226"
    data-selector='umap-alert-creation [role="dialog"]'
    >Alert message containing the edit link.</shot-scraper>

This text explains that you have just created a **anonymous** card and you
gives a link (a URL) to be able to modify the card. Indeed the
card you created is not associated with any account, and **uMap**
Considers that only people with this *secret link* can
modify. You must keep this link if you wish to be able
change the card or enter your email address to receive it.

We will see in [the next tutorial](3-create-account.md)
how to create your catalog of cards using an account, it is not
necessary to keep a secret link.

### For public officials on the instance dedicated to them

If they did not log in before creating their map, the message is different:

![The link to the MyAccountPro](../../static/tutoriels/proconnect-connexion.png)

It is not possible to save changes to an anonymous map on this instance.

### 3. Add a marker

Start by moving and zooming the map to view the place
specific of your home, place of vacation or work.

Then click the **Add Marker** button.

<shot-scraper
    data-output="static/tutoriels/draw-marker.png"
    data-url="https://umap.openstreetmap.fr/fr/map/new/"
    data-alt="Add marker button."
    data-width="46"
    data-height="47"
    data-selector=".leaflet-toolbar-icon.umap-draw-marker"
    data-padding="5"
    >Add marker button.</shot-scraper>

The cursor takes the form of a sign
`+` : move the place you want to *mark* and click with
the left mouse button: a *blue* and square marker is created at
This place and a sign appears on the right.

![A marker uMap.](../../static/tutoriels/2-je-cree-ma-premiere-carte-umap/umap_marqueur.jpg)

This panel allows you
to associate a name and a description with the marker:

-   the name will be displayed on the flyby of the marker by the mouse
-   the name and description will be visible in a so-called window
    *popup* that will appear when clicking on the marker.

We will see later the usefulness of the layers, and how to modify the
Marker properties: shape, color, pictogram, etc.

Repeat the operation to add the markers you deem useful to
your card.

### 4. Define the right-of-way of the map

It is important to define the initial right-of-way of the map, that is,
the part of the planisphere that will be posted during the consultation of the
map.

This right-of-way must include your marker and allow you to locate the
map. It is necessary to find a compromise between a zoom too far and
A zoom too close. The good compromise depends essentially on
content of the map : the majority of markers, lines and polygons
must be visible and make the best use of the scope of the card.

You can also consider the public of the card: a card shipped
to your neighbor can be very zoomed in, a map sent a correspondent
Foreigner must allow to recognize the country where your card is located.


To define
the right-of-way, move and zoom the map to display the right-of-way
want and click the **Save Zoom and Center button
current**.

<shot-scraper
    data-output="static/tutoriels/register-zoom.png"
    data-url="https://umap.openstreetmap.fr/fr/map/new/"
    data-alt="Button recording the current zoom and center."
    data-width="46"
    data-height="47"
    data-selector=".leaflet-toolbar-icon.update-map-extent"
    data-padding="5"
    >Togure recording button and current center.</shot-scraper>

!!! note
    uMap actually records the center and level of
    Zoom. Depending on the size of the window where the map is displayed, the part
    visible may vary. It is useful to provide a margin around the
    content of the map.

### 5. Register the card

Any changes to the card must be saved
by clicking on the **Save** button at the top right. This
operation records all changes since the last
backup : so you can make several changes to the
Then record them. Conversely, the **Cancel** button allows you to
Remove all changes since the last backup.

!!! note
    Registration is done on the servers of OpenStreetMap in the case
    use of uMap OSM or those of the ANCT if uMap for
    Public officials are used.


After saving the changes, the Cancel button is replaced
**Deactivate the edition**. This allows you to leave the mode
editing to see the map in consultation mode. Then you can
*test* your card : click on the marker to view popup and
Check his name and description.

**Congratulations! ** You created your first uMap card. You
can distribute it to your entourage by copying their URL in the bar
of the browser address, or by copying its **URL short** available
in the **Share** menu seen in the tutorial
[Sail in a map](1-browsing-a-map.md).

## Let's take stock

Your first card is created in a few steps. The operation is
Quite simple, but the result is quite sketchy. The
[next tutorial](3-create-account.md) goes to us
Allow to create a nice map.


??? info "License"

    Work initiated by Antoine Riche on [Carto’Cité](https://wiki.cartocite.fr/doku.php?id=umap:10_-_j_integre_des_donnees_distantes) under license [CC-BY-SA 4](https://creativecommons.org/licenses/by-sa/4.0/deed.en).

