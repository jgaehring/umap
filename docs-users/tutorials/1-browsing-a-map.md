!!! abstract "What We'll Learn"

    - Handle a uMap card
    - Share a map uMap
    - Know the main features of uMap


## Step-by-step procedures

### 1. Handle the map

You have received a link to an uMap card by email. Here are the
main elements of the map, and the operations available for the
manipulate. The uMap map shown below is available
[here](http://umap.openstreetmap.fr/fr/map/festival-des-3-continents_26381).

![Description of the different elements of a map](../static/tutoriels/1-je-consulte-une-carte-umap/anatomie_carte_umap_2021.jpg)


To the right of the map and according to the choice of its author can be displayed
one of the following two panels:

-   **About** : the title of the card, a possible description, and
    the list of layers
-   **Visualize the data** : all the elements of the card,
    distributed by layers (see below)

The About panel can be displayed by clicking on the word "About",
Always visible at the bottom right of the map.

As with most interactive maps you can:

-   move the card by a drag and drop
-   zoom in and out with the + and - buttons, or with the
    Mouse wheel
-   select an element of the map by a click of the mouse:
    Then appears a window *popup* displaying a description of
    the element. This can include text, an image, a link to
    a website. In our example the description of each cinema
    contains an image that is a link on the movie website.

**Note** : the buttons at the top left of the map, as well as the
legend bar, may not be available if the author of the
card chose to hide them.

Now let’s look at some features specific to uMap.

### 2. The layer selector

The elements of an umap card can be distributed in several
layers, or layers. This allows you to structure a map, so that it
be clearer and easier to maintain. The user can choose
to display or hide each layer individually.

<shot-scraper
    data-output="static/tutoriels/control-browse.png"
    data-url="https://umap.openstreetmap.fr/en/map/new/"
    data-alt="Layer(s) selector icon."
    data-selector=".umap-control-browse"
    data-width="48"
    data-height="48"
    data-padding="5"
    >Layer selector icon(s).</shot-scraper>

The layer selector is
the icon visible at the top left of the map under the zoom buttons.
When you position the mouse over this button, the list of layers
appears, you can then display or hide each layer, or
center the map on the contents of a layer.

![A description of the different parts of a layer selector](../static/tutoriels/1-je-consulte-une-carte-umap/umap_sélecteur_calques.png)

In this example, the “Bicloo Stations” layer is hidden:
Click on the eye of this layer allows you to display it.
The list of layers, with possibly a description of each
layer, is also visible in the legend of the map.

### 3. The Plus button

<shot-scraper
    data-output="static/tutoriels/control-more.png"
    data-url="https://umap.openstreetmap.fr/en/map/new/"
    data-alt="Icon for displaying more options."
    data-width="46"
    data-height="33"
    data-selector=".umap-control-more"
    data-padding="5"
    >Icon for displaying more options.</shot-scraper>

Under the card selector is visible a button with the text "More".
A click on this button shows another series of buttons.

<shot-scraper
    data-output="static/tutoriels/control-search.png"
    data-url="https://umap.openstreetmap.fr/en/map/new/"
    data-alt="Search selector icon."
    data-selector=".leaflet-control-search"
    data-width="48"
    data-height="48"
    data-padding="5"
    >Allows to search for a locality and center the map on it:
    Type the name of a municipality and tap on `Enter`</shot-scraper>

<shot-scraper
    data-output="static/tutoriels/control-fullscreen.png"
    data-url="https://umap.openstreetmap.fr/en/map/new/"
    data-alt="Icon of full screening."
    data-selector=".leaflet-control-fullscreen"
    data-width="48"
    data-height="48"
    data-padding="5"
    >Places the browser in full screen mode, which you can leave with the same
    button or with the `Escape key of the keyboard.</shot-scraper>

<shot-scraper
    data-output="static/tutoriels/control-embed.png"
    data-url="https://umap.openstreetmap.fr/en/map/new/"
    data-alt="Icon of sharing and integration."
    data-selector=".leaflet-control-embed"
    data-width="48"
    data-height="48"
    data-padding="5"
    >Allows you to share the map or export the data.
    A panel to the right of the map is displayed, it is explained below.</shot-scraper>

<shot-scraper
    data-output="static/tutoriels/control-locate.png"
    data-url="https://umap.openstreetmap.fr/en/map/new/"
    data-alt="Icon of geolocation."
    data-selector=".leaflet-control-locate"
    data-width="48"
    data-height="48"
    data-padding="5"
    data-javascript="document.querySelector('.umap-control-more').click()"
    >
    Allows you to geolocate, i.e. center the map on your position
    current. Geolocation requires the user to be asked for permission,
    Your web browser may therefore ask you to accept or activate geolocation.
</shot-scraper>

<shot-scraper
    data-output="static/tutoriels/measure-control.png"
    data-url="https://umap.openstreetmap.fr/en/map/new/"
    data-alt="Measuring icon."
    data-selector=".leaflet-measure-control"
    data-width="48"
    data-height="48"
    data-padding="5"
    data-javascript="document.querySelector('.umap-control-more').click()"
    >
    Is a measuring tool.
    Activate this tool has two effects: on the one hand it displays the length
    linear elements of the map and the area of the elements
    surface; on the other hand it allows you to trace on the map one
    line whose length is displayed. Click the button again
    to disable this tool.
</shot-scraper>

<shot-scraper
    data-output="static/tutoriels/control-edit-in-osm.png"
    data-url="https://umap.openstreetmap.fr/en/map/new/"
    data-alt="Icon for editing OpenStreetMap data."
    data-selector=".leaflet-control-edit-in-osm"
    data-width="48"
    data-height="48"
    data-padding="5"
    data-javascript="document.querySelector('.umap-control-more').click()"
    >
    Is useful for improving the OpenStreetMap card - which is apparent from the purpose of this tutorial.
</shot-scraper>

<shot-scraper
    data-output="static/tutoriels/control-icon-layers.png"
    data-url="https://umap.openstreetmap.fr/en/map/new/"
    data-alt="Card background change icon."
    data-selector=".leaflet-iconLayers"
    data-width="48"
    data-height="48"
    data-padding="5"
    data-javascript="document.querySelector('.umap-control-more').click()"
    >
    Displays several backgrounds of map in the flyby:
    Click on one of them changes the background of the map.</shot-scraper>


#### Share the map

The card sharing panel offers three possibilities. Your choice
depends on how you want to share the card:

-   **URL short** allows you to copy an abridged URL - equivalent to
    the URL of the card - which you can for example send in a
    mail.
-   **Embark the card in iframe** allows you to include the card in a
    web page : just copy the HTML code and insert it into
    The one on your web page. This possibility is explored in detail
    in the tutorial
    [I publish my map and access control](7-publishing-and-permissions.md).
-   **Download data** allows you to obtain visible data
    on the map, in different formats. This can allow you
    use this data with another tool.


### 4. Visualize the data

![umap_donnees.jpg](../static/tutoriels/1-je-consulte-une-carte-umap/umap_donnees.jpg)

The list of items in the map can be displayed with a click on
**View data**, accessible from the layer selector,
the legendary bar, or at the top of the Legend panel.

The panel then visible on the right shows all the elements of the
map, organized by layers. The magnifying glass to the left of each element allows
to display on the map the popup describing this element. The text of
input above the list allows you to search for an item, by
showing that those whose name contains the text entered.


## Let's take stock

This first tutorial allowed us to discover the main ones
features of an uMap card. We're going now
[learn how to create such a map](2-first-map.md).


??? info "License"

    Work initiated by Antoine Riche on [Carto’Cité](https://wiki.cartocite.fr/doku.php?id=umap:10_-_j_integre_des_donnees_distantes) under license [CC-BY-SA 4](https://creativecommons.org/licenses/by-sa/4.0/deed.en).
