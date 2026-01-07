!!! abstract "What We'll Learn"

    - Insert a map into an HTML page
    - Publish a map on Wordpress
    - Adapt the functionality of the card
    - Define who can see or edit the map

## Step-by-step procedures

### 1. Insert a map into an HTML page

We saw in the tutorial
[Sail in a map](1-browsing-a-map.md) that
the sharing menu allows you to *board an iframe* card, without giving
More detail. Let's see how it goes.

<shot-scraper
    data-output="static/tutoriels/control-embed.png"
    data-url="https://umap.openstreetmap.fr/en/map/new/"
    data-alt="Icon of sharing and integration."
    data-selector=".leaflet-control-embed"
    data-width="48"
    data-height="48"
    data-padding="5"
    >Allows you to share the map or export the data.</shot-scraper>

A **iframe** is a HTML computer language tag that allows
integrate (embed) the content of a web page into another page
Web. It’s actually very simple and we’ve already used this mechanism
to embed a video in the tutorial
[Infobulles multimedia](5-multimedia-tooltips.md).

![export-iframe.png](../static/tutoriels/7-je-publie-ma-carte-et-en-controle-lacces/export-iframe.png)

Here are the steps to follow:

1.  open the panel **Export and share the card**
2.  copy the entire text under **Integrate the card into a
    iframe** (tip: place the cursor over the text and then use the
    keyboard shortcuts <kbd>Ctrl</kbd>+<kbd>a</kbd> to select everything
    then <kbd>Ctrl</kbd>+<kbd>c</kbd> to copy the selection)
3.  paste the copied text into the source code of the HTML file in
    which you want to integrate the card (keyboard shortcut: <kbd>Ctrl</kbd>+<kbd>v</kbd>)

Here is a minimalist example of an HTML file in which the iframe of a
uMap map was integrated :

    <! DOCTYPE html>
    <html>
        <head>
            <title>Example of uMap map integrated into a web page</title>
            <meta charset="UTF-8">
        </head>
        <body>
            <div>
                <h1>The festival map</h1>
                <iframe width="100%" height="300px" frameBorder="0" src="https://umap.openstreetmap.fr/fr/map/festival-des-3-continents_26381? scaleControl=false&miniMap=false&scrollWheelZoom=false&zoomControl=true&allowEdit=false&moreControl=true&searchControl=null&tilelayersControl=null&embedControl=null&datalayers=controltrue&onLoadPanel=caption&caption=Barfalse"></iframe>
                <p><a href="http://umap.openstreetmap.fr/fr/map/festival-des-3-continents_26381">See full screen</a></p>
                <p>This card is offered by Carto’Cité:-)</p>
            </div>
        </body>
    </html>

Here is the map built into this page, using the options
of export by default :

<div style="border: solid 1px;">
    <h1>The festival map</h1>
    <iframe width="100%" height="300px" frameBorder="0" src="https://umap.openstreetmap.fr/fr/map/festival-des-3-continents_26381? scaleControl=false&miniMap=false&scrollWheelZoom=false&zoomControl=true&allowEdit=false&moreControl=true&searchControl=null&tilelayersControl=null&embedControl=null&datalayers=controltrue&onLoadPanel=caption&caption=Barfalse"></iframe>
    <p><a href="http://umap.openstreetmap.fr/fr/map/festival-des-3-continents_26381">See full screen</a></p>
    <p>This card is offered by Carto’Cité:-)</p>
</div>

Of course, it means knowing a little HTML and having a
server on which to publish such a file. But the principle is laid and
Not so complicated. Now let’s look at a more common case.

### 2. Publish a map on WordPress

Publishing a map to a WordPress site happens the same way as
above, by copying the *HTML code of the iframe* in the editor
WordPress. It is necessary to **use the text editor**
(Text tab) and not the visual editor.

![import-iframe-wordpress.png](../static/tutoriels/7-je-publie-ma-carte-et-en-controle-lacces/import-iframe-wordpress.png)

Publish the page and it’s done!

!!! note
    For security reasons, shared sites
    as <https://fr.wordpress.com/> do not allow the inclusion of iframe.
    It will therefore be impossible for you to publish an uMap map on such
    sites.

### 3. Adapt the functionality of the map

The map integrated above is not very practical: its height is
insufficient and the side panel is partially visible. The
buttons available on the left are not necessarily suitable, for example
We do not want to integrate the layer selector.

The **Export Options tab of the iframe** allows you to control all this.
Some of these options correspond to the **Interface Options** seen
in the tutorial
[Customize your map](4-customize-map.md). It's enough
enable these options so that the *iframe import code* is
modified. Once the options are chosen, copy this code and then embed it
in the one your web page.

![options-export-iframe.png](../static/tutoriels/7-je-publie-ma-carte-et-en-controle-lacces/options-export-iframe.png)

The first options are specific to export by iframe and deserve
to be commented :

-   the **width of 100% allows to use all the available width
    of the page. You can set a fixed width by replacing the
    text by a width in pixels, for example `800px`
-   the **link "full screen"** means the link `See full screen`
    placed under the card. This allows the user to display the
    uMap map as we have seen it so far.
-   the **Current view option rather than default view** allows
    to apply the current position and zoom level of the map to
    the export. This option is interesting to produce
    multiple zooms of the same map.
-   the **Keep layers visible currently** allows you to
    choose the layers included in the exported card. This option is
    useful for producing multiple cards for multiple profiles
    of users.
-   **Allow zoom with the dial** is not very suitable if the map is
    integrated into a long page, which users will do
    scroll with the wheel : arrived at the map the page will no longer scroll
    and the map will zoom out. Nothing serious but this
    behavior can be surprising.

!!! note
    When the options **Current view rather than seen by
    defect** and **Keep currently visible layers** are active,
    changing the current view or visible layers does not change the code
    of export. You must disable and then re-enable the option to take in
    Count these changes.

Here is the same map as above, with a view and a choice
different layer, and most options disabled. He is
possible to move the map but not zoom or modify the
layers.

<iframe width="600px" height="400px" frameBorder="0"
    src="https://umap.openstreetmap.fr/fr/map/festival-des-3-continents_26381?scaleControl=false&miniMap=false&scrollWheelZoom=false&zoomControl=null&allowEdit=false&moreControl=false&searchControl=null&tilelayersControl=null&embedControl=null&datalayersControl=false&onLoadPanel=none&captionBar=false&datalayers=53329%2C53328&locateControl=null&fullscreenControl=false#15/47.2132/-1.5503"
    ></iframe>


### 4. Define who can see or edit the map

<shot-scraper
    data-output="static/tutoriels/map-permissions.png"
    data-url="https://umap.openstreetmap.fr/fr/map/new/"
    data-alt="Permissions Management Button."
    data-width="46"
    data-height="47"
    data-selector=".leaflet-toolbar-icon.update-map-permissions"
    data-padding="5"
    >Permissions management button.</shot-scraper>


The button **Change
permissions and editors** gives access to the **Permissions panel
of the card**. This allows you to control, for each card, who
can see it and who can change it.

<shot-scraper
    data-output="static/tutoriels/map-permissions-panel.png"
    data-url="https://umap.openstreetmap.fr/fr/map/new/"
    data-alt="Permissions panel."
    data-caption="Permissions panel."
    data-width="410"
    data-height="414"
    data-selector=".panel.right"
    data-padding="5"
    data-wait-for="document.querySelector('.panel.right')"
    data-javascript="
        new Promise((takeShot) => {
            document.querySelector('.leaflet-control-edit-save').click();
            document.querySelector('#umap-alert-container').style.display='none';
            setTimeout(() => {
                document.querySelector('.leaflet-toolbar-icon.update-map-permissions').click();
                setTimeout(() => {
                    takeShot();
                }, 1000);
            }, 1000);
        });
    "
    >Permissions panel.</shot-scraper>

When you create a card, it is visible in your *catalogue*
of cards, whose address is
`http://umap.openstreetmap.fr/fr/user/<your-account>/` : option **All
the (public) world** of the **Who has access** drop-down menu is selected.
The other options in this menu are:

-   **anyone has the link** : the card no longer appears in your
    catalogue but people who know its link can
    consult.
-   **only publishers** : only people with the right
    to edit the map, and identified as such, can consult the
    map. Anyone else will be denied access. Do not use
    This option if you are integrating the card into an iframe.

When you create a card, you are the only one who can edit it.
You can invite other users to edit it by selecting
the **Only editors can edit** in the **Status menu
of edition**, then by entering one by one the account name of
invited users in the **Editors** field.

Each user's name is added to the following field.

The **Everyone option can edit** from the **Editing status** menu is
Useful to create a map collectively.

!!! note
    uMap does not allow multiple publishers to modify the
    card simultaneously. The software alerts you when the operation
    **Save** may overwrite changes from another
    user, you must then choose between its changes (in
    validating Save) or yours (by canceling).

    If you are several publishers of the same card, consult before
    to modify the card.

Finally you can **transfer property** from one card to another
user : delete the current owner (you) by clicking on the
small cross to the right of the **Owner** field, then enter the name of
account of the user to whom you give the card.

## Let's take stock

At this point we know how to create a structured map with content
multimedia, we know how to publish it and integrate it into a web page, we
Even know how to change it collectively. We will soon be able to
move to the advanced level, in which we will learn to **importe
data** in a map and explore the opening capabilities of
uMap.

But before that, we will finish the intermediate level by
treating [the case of polygons](8-polygons.md).


??? info "License"

    Work initiated by Antoine Riche on [Carto’Cité](https://wiki.cartocite.fr/doku.php?id=umap:10_-_j_integre_des_donnees_distantes) under license [CC-BY-SA 4](https://creativecommons.org/licenses/by-sa/4.0/deed.en).

