!!! abstract "What We'll Learn"

    - Create a polygon and modify it
    - Stylize a polygon : filling and contour(s)
    - Associate a URL with a polygon
    - Extract from the administrative boundaries of OpenStreetMap
    Import data into a map

!!! question

    Why treat polygons separately, it’s just a line
    Closed? A polygon is actually much more than a closed line. This
    line separates the **inside of the polygon** from its exterior, this is
    important because uMap can react to a click inside the polygon. of
    plus a polygon being holed, it is then defined by several lines.

## Step-by-step procedures

### 1. Creating a Polygon

Let's go back to the map of our holiday in Crozon. A day of good weather we
Let's rent a dinghy and naviguons in the area defined by the club
nautical. Let's add this area to the map.

<shot-scraper
    data-output="static/tutoriels/draw-polygon.png"
    data-url="https://umap.openstreetmap.fr/fr/map/new/"
    data-alt="Polygon drawing button."
    data-width="46"
    data-height="47"
    data-selector=".leaflet-toolbar-icon.umap-draw-polygon"
    data-padding="5"
    > Polygon drawing button.</shot-scraper>

The button
**Drawing a polygon** allows you to trace the perimeter of a polygon
point by point, and to finish it by clicking again on the last
point as for the drawing of a line. A difference however : from the
third point the inside of the polygon is colored.

### Properties of a Polygon

![proprietes_polygones.png](../../static/tutoriels/8-le-cas-des-polygones/proprietes_polygones.png)

The list of
properties of a polygon is quite long. Properties of half
upper menu apply to the perimeter of the polygon, and are
identical to the properties applicable to the lines. The lower half
concerning the filling of the polygon. Note :

-   options **trait** and **filling** allow you not to
    display the perimeter or interior of the polygon: if none of these
    Two elements is displayed the polygon is invisible.
-   the **color of the filling** is by default that of the line, but
    can be modified.
-   a low **opacity of the filling** allows to see the bottom of
    card *under* the polygon.

### Find a polygon

It is sometimes useful to create one or more holes in a polygon,
for example to draw a clearing in a forest or an island in
middle of a pond.

![polygone_trou.jpg](../../static/tutoriels/8-le-cas-des-polygones/polygone_trou.jpg)

You can create a
polygon with one or more holes by clicking on the option **Add
an inner path** when you select a polygon in mode
Edition.

The first point of the *inner perimeter* is created directly where
you clicked before choosing **Add an inner track**.

Note that the perimeter properties of a polygon apply to everyone
perimeters - exterior and interior.

### 2. Define interactions with a polygon

The **Interaction Options** tab offers two options specific to
polygons.

![interaction-desactivee.png](../../static/tutoriels/8-le-cas-des-polygones/interaction-desactivee.png)

Any interaction can be disabled by selecting **OFF** for
the **Allow interactions** option. No tooltip is then
displayed when you click on the polygon. This option is interesting
to give importance to an area of the map without
The user cannot interact with.

![ile-de-nantes.jpg](../../static/tutoriels/8-le-cas-des-polygones/ile-de-nantes.jpg)

Here is an example showing
The Island of Nantes surrounded by a wide red line and without filling. He
is not possible to click on the outline or inside the
polygon.

!!! note
    Interaction with the polygon remains disabled in mode
    Edition. To be able to edit the polygon it is then necessary to
    go through the panel **View data** (always accessible
    by the Legend panel itself accessible from the link **A
    propos** bottom right of the map).


![interaction-url.png](../../static/tutoriels/8-le-cas-des-polygones/interaction-url.png)

Conversely, it is
possible to associate a URL with a polygon: a click on the polygon
then open the corresponding web page directly, without going through a
Toothboil. Just define the **Link to...** then
enter the URL. there are three options to define ***where***
will be open the web page :

-   **new window** : the page opens in a new tab of the
    Navigator
-   **parent window** : the page opens in the same tab as the one
    of the map
-   **iframe** : if the map is integrated in an iframe, the web page
    is then open inside the iframe


### 3. Create a map menu

Combining a URL with a polygon allows you to create a *map menu*,
that is to say, a card allowing access to several web pages according to
the area on which the user clicks. Here is an example showing the
different neighborhoods of Nantes: a click on a neighborhood opens the page
corresponding to the website <http://www.nantes.fr>.

<iframe width="500px" height="550px" frameBorder="0" src="https://umap.openstreetmap.fr/fr/map/quartiers-de-nantes_126581?scaleControl=false&miniMap=false&scrollWheelZoom=false&zoomControl=false&allowEdit=false&moreControl=false&searchControl=null&tilelayersControl=null&embedControl=null&datalayersControl=false&onLoadPanel=undefined&captionBar=false&fullscreenControl=false&datalayers=311326#12/47.24/-1.5"></iframe>


Here are the steps to make this card.

### a. Recovering the contours of the neighborhoods

The outline of the districts of Nantes comes the administrative boundaries
from OpenStreetMap (for more information, see this [page of
Wiki](http://wiki.openstreetmap.org/wiki/WikiProject_France/List_limites_administratives)).
The site [OSM Boundaries](https://osm-boundaries.com/) allows
select the administrative boundaries one by one, and then export them
in different formats.

![osm-boundaries.png](../../static/tutoriels/8-le-cas-des-polygones/osm-boundaries.png)

Follow these steps :

1.  Log in to your OpenStreetMap account (this one is required to
    being able to export the administrative limits)
2.  select the administrative limits one by one, opening
    successively the different levels : country - region - department
    etc.
3.  select the JSON export format: the format
    [GeoJSON](https://fr.wikipedia.org/wiki/GeoJSON) was then used
4.  click Export

You retrieve a file from the downloads folder, including
The extension is `.geojson`.

![import-contours.png](../../static/tutoriels/8-le-cas-des-polygones/import-contours.png)

### b. Import neighborhood contours into a map

<shot-scraper
    data-output="static/tutoriels/upload-data.png"
    data-url="https://umap.openstreetmap.fr/fr/map/new/"
    data-alt="Data import button."
    data-width="46"
    data-height="47"
    data-selector=".leaflet-toolbar-icon.upload-data"
    data-padding="5"
    >Data import button.</shot-scraper>

In a new
map, click **Import data**. In the panel that appears
Then select the file produced in the previous step.

The format selector is automatically positioned on **geojson**,
Select it if it is not, for example because
the file extension is not `.geojson`. Click on **Import** :
The outlines appear on the map.

### c. Configure the uMap card

Configure the layer to display a label - on the flyover or not
according to your choice. Then edit each polygon to associate it
the URL to the corresponding web page, as we saw above.

Finally you can, in the **Settings of the map**, set the
**Geographic limits** of the map. This prevents
the user to move the card beyond these limits.
![limites-geographiques.png](../../static/tutoriels/8-le-cas-des-polygones/limites-geographiques.png)

### d. Integrate the map into an iframe

Recover the code from the iframe, as we saw in the
[previous tutorial](7-publishing-and-permissions.md),
Taking care to disable all interaction options:
zoom buttons, zoom with the knob, “More” button, etc.

Copy this **code iframe** to your web page, and you're done!

!!! note
    When you modify the card, you must reload
    the entire page containing the iframe to clear the cache of the
    browser, for example using <kbd>Ctrl</kbd>+<kbd>F5</kbd>
    on Firefox.


## Let's take stock

This tutorial marks the end of the intermediate level. You know how to structure
the content of a card with layers and use styles by
Defect. You know how to format the tooltips and integrate multimedia.
You know how to embed your map into a web page and control who can
See and modify it.

We have just seen how to import data into a map, the
advanced level will allow us to go much further in this
approach.


??? info "License"

    Work initiated by Antoine Riche on [Carto’Cité](https://wiki.cartocite.fr/doku.php?id=umap:10_-_j_integre_des_donnees_distantes) under license [CC-BY-SA 4](https://creativecommons.org/licenses/by-sa/4.0/deed.en).

