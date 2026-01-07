!!! abstract "What We'll Learn"

    - Change the shape, color and pictogram of a marker
    - Create and modify a line
    - Control the display of labels

Here's how to make a card with nice markers and lines
with for example the map of our holiday at the
[Goulien Beach Camp](https://www.openstreetmap.org/way/119055693)
on the peninsula of Crozon in Brittany.

### 1. Create a nice marker

Let’s start by creating a map: let’s give it a name, let’s define a
right-of-way and add a marker at [the location of the
camping](http://www.openstreetmap.org/?mlat=48.2387&mlon=-4.5434#map=16/48.2387/-4.5434).
We saw in [the previous tutorial](2-first-map.md) how to perform these operations.

![umap_marqueur_props.png](../static/tutoriels/3-jutilise-un-compte-et-cree-une-belle-carte/umap_marqueur_props.png)

This big blue marker is not very explicit to feature a campsite.
Let's remedy that. In the visible side panel when a marker is
selected, the **Properties menu of the shape** allows to modify
The appearance of the marker:

-   **Color** : click on `set` allows you to choose a color.
    Note that you can set a color by [its name
    CSS](http://www.w3schools.com/cssref/css_colors.asp) or by its code
    hexadecimal, which you can choose for example with this [selector
    colors](http://htmlcolorcodes.com/fr/selecteur-de-coleur/).
-   **Icon shape** : the choice `By default` corresponds to the marker
    Currently, the other choices are Circle, Drop and Pin.
-   **Image of icon** : click on `set` to choose from one
    Hundreds of pictograms. Note that the picto is only displayed for
    the `By default` and `Drop` icon shapes.

Here is the marker obtained with the properties opposite:

![umap_camping.png](../static/tutoriels/3-jutilise-un-compte-et-cree-une-belle-carte/umap_camping.png)

### Edit a marker

![umap_modifier_marqueur.png](../static/tutoriels/3-jutilise-un-compte-et-cree-une-belle-carte/umap_modifier_marqueur.png)

To modify a marker of the card, several possibilities are available to you:

-   a **right click** on the marker allows you to view the options
    possible editing with your rights and other actions relating to this point
-   **shift-click** is a shortcut that directly displays the panel
    of edition
-   a drag and drop allows you to move the marker on the map

### 2. Creating a line

On the first day of vacation we go by sea kayak to the
Pointe de Dinan to the west of the Goulien beach. Trace the route
followed.

<shot-scraper
    data-output="static/tutoriels/draw-polyline.png"
    data-url="https://umap.openstreetmap.fr/fr/map/new/"
    data-alt="A line drawing button."
    data-width="46"
    data-height="47"
    data-selector=".leaflet-toolbar-icon.umap-draw-polyline"
    data-padding="5"
    > Drawing button of a line.</shot-scraper>

The button **Draw a line** allows to trace, point by point,
a line consisting of several segments.
Click again on the last plot point to
finish the line : then appears on the right a panel allowing to
give a name and description to the line, as for the markers.

#### Edit a line

At any time you can select a line by double-clicking
on it. You can then edit its properties in the side panel,
or modify his layout on the map:

-   **remove a point** of the line, materialized by a white square,
    by clicking on it
-   **move a dot** by a drag and drop
-   **insert a dot** by clicking on a grey square located at
    middle of each segment
-   ** extend the line** with a Ctrl-Clic when the cursor is placed
    On the first or last point
-   **cut the line** in two : Right click on a point then choose
    the `Scinder the line` option

![umap_ligne.jpg](../static/tutoriels/3-jutilise-un-compte-et-cree-une-belle-carte/umap_ligne.jpg)

#### Properties of a line

![umap_ligne_props.png](../static/tutoriels/3-jutilise-un-compte-et-cree-une-belle-carte/umap_ligne_props.png)

The properties of a
line allows you to define your color and other parameters
defining his *style* :

-   the **opacity** ranges from transparent to left to totally opaque to
    right. The thicker the stroke, the more transparent it can be.
-   the **thickness** is defined in pixels, its default value is 3:
    slide the cursor to the right for a thicker line (which will be
    easier to select).

**Advanced properties** allow to:

-   **simplify** the plot can reduce the number of points to
    Adapt it to the zoom level. There is generally no need to simplify
    a path made *by hand*.
-   define a **traited**, by a series of digits separated by
    commas : visible length (in pixels), invisible length,
    visible length, etc. The thickness of the line should be taken in
    account : the thicker the strokes the more the intervals must
    be great.

Here is the style of line obtained with the properties opposite:

![umap_ligne_tirets.png](../static/tutoriels/3-jutilise-un-compte-et-cree-une-belle-carte/umap_ligne_tirets.png)

### 3. Add labels

![etiquettes.png](../static/tutoriels/3-jutilise-un-compte-et-cree-une-belle-carte/etiquettes.png)

To help identify the
different elements of our map, we can associate them with a
Label. The **Interaction Options** tab allows you to control
the display of a label associated with each element:

-   **Show a label** activates its display, it is then
    automatically placed
-   **Direction of the label** allows you to fix the position, to
    right or left of the element, or above or below
-   **Show only overflight** of the mouse is an option
    interesting if the map is dense: display all the labels
    over-lick the map
-   **Clickable label** allows you to display the corresponding tooltip
    if the user clicks on the label, and not only in the event of
    Click on the *geometry* of the element.


## Let's take stock

Our second card is already more interesting than the first, and we
Know how to find it easily. We have seen how to create, *styl*
and modify points and lines. We did not treat polygons here,
which represent surfaces. Some features specific to
polygons deserve to be detailed, what we will do in the
tutorial [The case of polygons](8-polygons.md).

For now, let’s see how we can more
[customize our map](4-customize-map.md).

??? info "License"

    Work initiated by Antoine Riche on [Carto’Cité](https://wiki.cartocite.fr/doku.php?id=umap:10_-_j_integre_des_donnees_distantes) under license [CC-BY-SA 4](https://creativecommons.org/licenses/by-sa/4.0/deed.en).

