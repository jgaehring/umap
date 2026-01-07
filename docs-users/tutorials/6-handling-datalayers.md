!!! abstract "What We'll Learn"

    - Create layers and organize the content of the map
    - Define the properties of a layer
    - Manage the layers of a card

## Step-by-step procedures

### 1. Creating a layer

Let's take the [map of the Festival of 3 continents](http://u.osmfr.org/m/26381/)
seen in the tutorial [Sail in a map](1-browsing-a-map.md). The
data of this card are organized in several layers:

-   cinemas : yellow markers
-   the other venues of the festival : brown markers
-   public transport lines
-   Bicloo bike-sharing stations

![umap_calques_gauche_droite.jpg](../../static/tutoriels/6-je-structure-ma-carte-avec-des-calques/umap_calques_gauche_droite.jpg)

The layer selector allows the user to zoom in on the set
elements of a layer, to hide it or display it at leisure. Every
layer can be described in the side panel of the card. Organize
the elements of a map is therefore convenient to consult the map, we
See also that it facilitates its creation.

<shot-scraper
    data-output="static/tutoriels/control-browse.png"
    data-url="https://umap.openstreetmap.fr/en/map/new/"
    data-alt="Layer(s) selector icon."
    data-selector=".umap-control-browse"
    data-width="48"
    data-height="48"
    data-padding="5"
    >Layer(s) selector icon.</shot-scraper>

The **Manage layers** menu, available in edit mode, displays the list of layers
existing and allows to create a new layer. Then click on
**Add a layer**, then appears the panel **Layer Properties**
of the new layer.

![](../../static/tutoriels/6-je-structure-ma-carte-avec-des-calques/umap_layer_props_top.png)

Enter the layer name and a description of the item category
to which you intend this layer: they will be displayed in the panel
**About**. Below is the result corresponding to the properties
seized on the right.

![umap_layer_description.png](../../static/tutoriels/6-je-structure-ma-carte-avec-des-calques/umap_layer_description.png)

!!! note
    Skip a line at the beginning of the description
    for this one appears **under** the name of the layer and not next to it in the
    panel About.

### 2. Organize the content of the map


When you
add an item to the map, at the top of the properties panel of
the element is a **drop-down menu** that allows you to choose the
layer where to place the element.

![umap_layer_select.png](../../static/tutoriels/6-je-structure-ma-carte-avec-des-calques/umap_layer_select.png)

It is of course possible to change the layer of an element already created.
So do not hesitate, when your card is enriched, to *restructure* sound
content in several layers.

### How to define the layers of a card?

There is no established method to define layers: it depends
really data placed on the map and experience of
Cartographer. Here, for some map themes and for example
of examples, a proposal of lists of layers:

-   tourism: accommodation, catering, transport, museums, points of
    View...
-   logistics of a festival: access, stages, catering, sanitary,
    waste, emergency stations, power grid...
-   event with an international scope: one or more layers by
    language
-   structures of a network: supporting structures, members of the network,
    Partners
-   development project: the different scenarios or variants of the
    Project

We’ll see later than when a map is embedded on a web page,
it is possible to create several presentations of the same card, and
Select for each one which layers are visible. You can
therefore, from the same uMap card, broadcast several cards including the
content is suitable for the target audience of each card.

So for a multi-lingual card you can broadcast the card in
different languages by selecting the layer(s) of each language.
For the example of a map of the logistics of a festival, you can
thus broadcast a map to the public (access, scenes, restoration,
sanitary), another to the technical teams (sanitary, waste,
electricity network), a third towards civil security (access, stations
emergency, electrical network, etc.

### 3. Define the properties of a layer

A major interest in the use of layers is the possibility of
set, for each layer, the **style by default** of the elements that
will be added to the layer. This will prevent the tedious task of
define one by one the style of each element and the map will be clearly
more *readable* because homogeneous. Especially if you decide that cinemas
must be displayed also in yellow but in red, you will not do the
modification only once for the whole layer and not for
Each of the elements.

![](../../static/tutoriels/6-je-structure-ma-carte-avec-des-calques/umap_layer_edit.png)

In the
Layer management panel click on the pencil to edit the
properties of the layer. Tabs **Properties of the form** and
**Advanced properties** allow you to set default styles
of the layer. You find the same properties used in
the tutorial [Create an account](3-create-account.md).

![umap_legende.png](../../static/tutoriels/6-je-structure-ma-carte-avec-des-calques/umap_legende.png)

All properties, which
apply to markers, lines and polygons, are here
Available. A layer may contain the three indifferently
Types of items, so you can set the default properties
for each category.

One remark though: you can define **one and only one
color**, which applies to all elements regardless of their type.
This constraint aims to create a readable map, by associating a
color to each layer. This color appears in **legend of the panel
About**, as in the example below.

### 4. Managing the layers


Let's go back to **layer management panel**. We have seen how
Create a new layer and define its properties.

![](../../static/tutoriels/6-je-structure-ma-carte-avec-des-calques/umap_gestion_calques.png)

The square on the right allows to modify the **order of the layers** by a
Drag and drop. The order thus defined is that which is found in
the layer selector and in the list of layers in the To panel
About.

The eye allows you to hide/display a layer and the magnifying glass to zoom in on sound
content, as for the layer selector. We will see later
the usefulness of **Edit in a table** the content of the layer. **Delete
the layer** will ask you to confirm the operation, this operation
removing the content of the layer.

![](../../static/tutoriels/6-je-structure-ma-carte-avec-des-calques/umap_layer_advanced.png)

Finally, the **Advanced Actions** tab allows you to empty a layer: this
deletes its data but retains the layer. You can also
**cloning a layer** : this operation copies the content and the
properties of the layer.


!!! note
    To quickly create a new layer including
    the properties are close to an existing layer, you can clone the
    initial layer then rename the clone and empty its contents.

## Let's take stock

If it is a little abstract, the concept of layers is one of the strengths of
uMap. When creating a map, take the time to define the
main layers by anticipating the uses and updates of the
map. Familiarize yourself with the use of layers, we will make one
great use in advanced level.

We now have all the elements to make cards
structured, useful, whose content is rich and beautiful. It's time
to learn how to publish a map on a website, this is the purpose of
[next tutorial](7-publishing-and-permissions.md).


??? info "License"

    Work initiated by Antoine Riche on [Carto’Cité](https://wiki.cartocite.fr/doku.php?id=umap:10_-_j_integre_des_donnees_distantes) under license [CC-BY-SA 4](https://creativecommons.org/licenses/by-sa/4.0/deed.en).
