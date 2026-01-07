!!! abstract "What We'll Learn"

    - Create a layer that uses remote data
    - Produce a heat map (heatmap)
    - Display layers according to the zoom level
    - Display data that evolves in real time
    - Use a portal *open data*
    - Credit the data source to comply with the license


## Step-by-step procedures

So far all the maps we have created show data
managed by uMap. Even when we used the data of a
spreadsheet in the previous tutorial, this data was *imported* on
the uMap server, where they are *stocked*. If these data are
modified, we have to import them again to update the
map.

In this tutorial we will learn how to create a map that
use **remote data**, i.e. stored on another
server that the uMap server.

### 1. I use remote data

We take for this tutorial the theme of bike-sharing stations to
Paris, the famous Vélib’, whose data is available in open
Data.

#### Use an open data portal

Let’s start by observing the dataset “Vélib’ - Location and
characteristic of the stations”, available on the open data portal of
the city of Paris :
<https://opendata.paris.fr/explore/dataset/velib-location-des-stations/>.

The **Information** tab explains that the data “are updated
every minute according to GBFS 1.0.” This standard describes several
files, accessible with the API described in the **API** tab, including the
format is not included by uMap.

The **Table** tab shows the data: each station has a name and a
capacity (number of locations), as well as a geographical position.

The **Export** tab offers several formats, including formats
**GeoJSON**, **KML** and **GPX**, all three included by uMap. We
Let's choose the [GeoJSON format](https://fr.wikipedia.org/wiki/GeoJSON),
which allows to exploit all the attributes present in the data.

One option would be to download the file and then import it into
uMap, as we did in the previous tutorial with a file at
CSV format. Besides manipulations, this would involve updating
these data regularly. Instead, we will configure our map
to access directly the data made available by the portal
open data. For this we copy the link to the file: a click
right opens a context menu that allows to **copy the link** to the
file :

    https://opendata.paris.fr/api/explore/v2.1/catalog/datasets/velib-emplacement-des-stations/exports/geojson?lang=fr&timezone=Europe%2FBerlin

![umap-donnees-distantes.png](../../static/tutoriels/10-jintegre-des-donnees-distantes/umap-donnees-distantes.png)

#### Configure remote data

Now let’s see how to use this link in uMap. For this we
Let us create a new layer and open, in the Properties of the layer,
the **Remote data** tab. The information to be provided is the
following :

-   **URL** : we paste here the link to the copied file
    previously.
-   **Format** : we have to select the format, here **geojson**
-   **License** : ODbL as indicated on the export page of the portal
    open data

The **Check URL** button allows you to test the file access from
uMap, and to check that the chosen format corresponds to the data.
The data is then displayed on the map.

#### Proxy or not proxy?

If it doesn’t work (uMap displays a banner that says “
Problem in the server response”), it is likely that the server
on which the file is stored does not allow access to the file
from a third party service.

!!! note

    This is the CORS mechanism, described in the article
    Wikipedia [Cross-origin resource
    sharing](https://fr.wikipedia.org/wiki/Cross-origin_resource_sharing).

uMap allows you to bypass this constraint by transiting the
file by the uMap server, thanks to the **With proxy** option it
Then agree to activate. This option is associated with the drop-down menu
**Hide the request with proxy**, which allows the uMap server to
keep the file so as not to recover it with each display of
The map. The longest duration (1 day) would be adapted here.

### About the license

The Vélib’ station locations file is published under the
[ODbL license](https://opendatacommons.org/licenses/odbl/). This one
requires the producer of the data to be credited with the
Use. The information on the open data portal indicates that this
Producer is “Autolib Velib Métropole”. It should therefore be cited
in the **Credits** of the map, a tab of the *Properties menu of the
map*.

![umap-geojson-properties.png](../../static/tutoriels/10-jintegre-des-donnees-distantes/umap-geojson-properties.png)

#### Show the name and capacity of the stations

To display the name and capacity of each station in one
tooltip, we need to determine the keys to access these
information. For this we need to observe the GeoJSON file.

We download this file from the Export tab of the open portal
data, or paste the previously copied link into the navigation bar
of the browser. Either the file is directly displayed in the
browser, or it is downloaded: a possibility is then to
open it in a text editor, or drop it in the window of the
Navigator.

In the `properties` block of each element, we observe several
key-value associations : the **name** property contains the name of the
station, **capacity** contains the number of locations. These properties
correspond to our column headers of a CSV file (see tutorial
previous).

We can then configure the **Popup Template** to display
this information in the tooltip of each station, as we have
seen in the [previous tutorial](9-map-from-spreadsheet.md).

For example :

    # {name}
    {capacity} locations

### 2. I combine two layers for the same data

There are many stations Vélib’ and the map is a little dense to
The Paris Ladder. At this scale it would be more interesting to have
an overview of the distribution of the Vélib’ offer on the capital
and the neighbouring municipalities.

![umap-heatmap.png](../../static/tutoriels/10-jintegre-des-donnees-distantes/umap-heatmap.png)

#### Produce a heat map or “Heatmap”

uMap allows to present the data of a layer in several forms,
with the **Layer Type** drop-down menu in the *Properties menu of the
layer*. The different types of layers are:

-   **By default** : each data is displayed individually.
-   **With cluster** : the nearby points are grouped into one
    Circle.
-   **Heatmap** : the data are represented in the form of *card of
    heat*.
-   **Choropleth** : this display is suitable for polygons, and allows
    to graduate their color.
-   **Proportional circles** : this representation is suitable for
    absolute quantitative values (which can be added).
    The surface area of the circles is proportional to the quantity.

The types *With cluster* and *Heatmap* are rather suitable for layers
containing only points. When you choose one of these modes, a
Configuration tab appears. For the *Heatmap* type, the tab
**Heatmap: parameters** allows to adjust the intensity – or *heat* – of
the card (from the icy blue to the burning red), and select a
property to rate this *heat*. This must correspond to a
ownership of our data containing numerical values. If none
property is not defined, each point has the same value and only the
Geographical density of points affects the *heatmap*.

Our station file contains precisely the `capacity` property,
which corresponds to the number of locations of each station – a good one
criteria to represent the offer of self-service bicycles. As for the
**Sheet radius**, a slider allows you to adjust it with immediate effect
on the map. It is a good idea to test this ray at different levels
zoom the map, so that the map reveals the data.

### Duplicate the layer

The type of display of a layer applies regardless of the level of
Zoom. But at high zoom levels, at the neighborhood scale, it is
more interesting to show individual stations than the map of
heat. We will combine the 2 representations by creating 2 layers
which use the same data, one displaying the stations
Individual, the other in the form of Heatmap. The trick is then
to activate or disable each layer according to the zoom level.

Proceedings in stages :

1.  Let’s duplicate our layer with the operation **Cloner** available in
    the **Advanced Operations** tab of the Layer Properties panel.
2.  The Properties panel of the new layer is then displayed:
    Let’s rename this layer, for example “Heatmap stations Vélib’”.
3.  Let's change the layer type for **Heatmap**, the **Heatmap tab:
    parameters** appears.
4.  In this tab, let's enter the property name - `capacity` - and
    Let's adjust the **ray of heatmap** (a value around 30 works
    good for this dataset)
5.  In the **Remote data** tab, let's configure the layer to
    that it is displayed **until zoom** 15.
6.  In the same way, let’s configure the initial layer so that it
    is displayed **from zoom** 15.

Here we choose to overlay, at zoom 15, the heatmap to
individual stations. This produces a transition between the 2 modes of
representation, and allows to identify the stations with a large number
of locations.

Please note that we did not need to specify the URL of the data
remote and their format: these parameters were kept during the
Duplication of the layer.

### 3. I use dynamic data

Another dataset from the open data portal is entitled “Vélib - Vélos
and terminals - Real-time availability » :
<https://opendata.paris.fr/explore/dataset/velib-disponibilite-en-temps-reel/>.

We may use this data *in real time* – in reality with a
lightly delayed – to power our uMap card, and display the number
of seats and bicycles available. The procedure is the same as
above, at a nuance close: the **Dynamic** option of the tab
**Remote data** must be enabled. It tells uMap of
recover data at each display of the card, i.e.
each time the map is moved, zoomed in, or zoomed in. However,
this data will not be automatically updated by uMap to a
Regular time interval: it is up to the user to refresh the
web page or move the map.

![umap-api-properties.png](../../static/tutoriels/10-jintegre-des-donnees-distantes/umap-api-properties.png)

He's still at
change our popup template to display availability in
Real time. To identify the name of the properties, we can use
the **API** tab on the open data portal: the **Results** panel
shows an extract of the data with all their properties. These
properties are the same as for the GeoJSON export. Here is an example
possible popup template :

    # {name}
    {capacity} locations including {numdocksavailable} free
    {numbikesavailable} available bicycles including {ebike} VAE

![umap-api-parameters.png](../../static/tutoriels/10-jintegre-des-donnees-distantes/umap-api-parameters.png)

### Filter data at the source

The Results panel in the **API** tab shows us the existence of the
property `is_installed`. This makes it possible to detect stations that
are not in service, which we do not wish to display on our
map.

The **Request panel for the API** call allows you to generate a request,
displayed under this panel (**URL of the API** call), and view the
data produced by this query in the **Results** panel. He
also allows you to add parameters to the request, to filter the
data produced. The **refine** parameter allows you to filter the data
based on the value of one or more properties. If we
let's indicate `is_installed` for the property name and `NON` for the
value, we can see the number of stations that are not in
service, and that we do not want to integrate into our map.

The data produced using this **API** tab is in GBFS format,
which is not known to uMap. Export requests in GeoJSON format
accept the same parameters. To produce the filtered data at
GeoJSON format, so we have to edit the request *by hand*.
Process in stages *a little geek* :

1.  Enter `is_installed` and `OUI` in the field **refine**
2.  Remove the value from the `limit` field, because we do not want
    *limit* the response of the request to 20 stations.
3.  Let’s look at the generated query:
    `/api/explore/v2.1/catalog/datasets/velib-disponibilite-en-temps-reel/records?refine=is_installed%3AOUI`,
    It consists of 3 sections:
    -   the basic URL, up to the last character **`/`**
    -   the **endpoint** `records` followed by character **`? `**
    -   the parameter `refine=is_installed%3AOUI` (`%3A` is the *encoding*
        character **`:`**)
4.  Let’s take the request generated for the GeoJSON export:
    `https://opendata.paris.fr/api/explore/v2.1/catalog/datasets/velib-disponibilite-en-temps-reel/exports/geojson?lang=fr&timezone=Europe%2FBerlin`,
    It consists of the same sections:
    -   the basic URL :
        `https://opendata.paris.fr/api/explore/v2.1/catalog/datasets/velib-disponibilite-en-temps-reel/exports/`
    -   le endpoint `geojson?`
    -   the list of parameters `lang=fr&timezone=Europe%2FBerlin` (`%2F`
        is the character **`&`** encoding that allows to separate
        several parameters)
5.  We can combine the URL and endpoint of the GeoJSON request,
    followed by the parameter `refine=is_installed%3AOUI` (the parameters
    `lang` and `timezone` are not useful here) :


    `https://opendata.paris.fr/api/explore/v2.1/catalog/datasets/velib-disponibilite-en-temps-reel/exports/geojson?refine=is_installed%3AOUI`

Use this query as a URL of the remote data of our layer
**Stations Vélib’** allows only stations to be displayed in service.

Note that the `exclude` parameter can also be used to exclude
stations whose `is_installed` property has the value `NON`. We
can use the same mechanism to exclude stations that do not
No bike available :

    https://opendata.paris.fr/api/explore/v2.1/catalog/datasets/velib-disponibilite-en-temps-reel/exports/geojson?exclude=is_installed%3ANON&exclude=numbikesavailable%3A0

### 4. I inject parameters into the request

uMap allows you to inject parameters into a request, with syntax
`{paramX}`. These parameters depend on the status of the map at the time of
the sending of the request:

-   the coordinates of the center of the map : {lat} and {lng}
-   the *bounding_box* of the card : {bbox} or {west}, {south}, {east} and
    {north}
-   zoom level : {zoom}

The open data portal can take into account some of these parameters
to refine the request. Our goal here is to recover the
availability of stations **in the visible part of the
card**, that is, in the *bounding_box*. This helps to reduce the
volume of data transferred, and display it faster.

### I use the API console of the open data platform

The API tab of the dataset allows you to access the **API console
complete**. In the Dataset section, we choose the *endpoint*
**Export a dataset**.
![umap-api-console.png](../../static/tutoriels/10-jintegre-des-donnees-distantes/umap-api-console.png)

Then appears a form where we can fill in the different
parameters :

-   **dataset_id** is the identifier of the dataset:
    `velib-disponitite-in-time-reel`
-   for **format** we select `geojson`
-   we can filter the stations in service again with the
    **refine** parameter : `is_installed:OUI`

![umap-api-console-dataset.png](../../static/tutoriels/10-jintegre-des-donnees-distantes/umap-api-console-dataset.png)

Set the **where** parameter with the `in_bbox()` function (see the
[documentation
OpenDataSoft](https://help.opendatasoft.com/apis/ods-explore-v2/#section/ODSQL-predicates/in_bbox()))
and – for the moment – fixed latitudes and longitudes (somewhere to
Paris) :

![umap-api-console-bbox.png](../../static/tutoriels/10-jintegre-des-donnees-distantes/umap-api-console-bbox.png)

**coordinates_geo** is the name of the field containing the geometry in the
original data, which can be found by exporting them in a format
Other than GeoJSON.

Let's test now that the query works by clicking **Execute**
: the response code 200 indicates that the request worked, and it is
possible to download the resulting file.

![umap-api-console-execute.png](../../static/tutoriels/10-jintegre-des-donnees-distantes/umap-api-console-execute.png)

### I boost the request

Now let's change our *static* request (all parameters are
fixed) to make it *dynamic*, replacing the coordinates of the
bounding_box by the parameters that will be injected by uMap. We
do not use the `{bbox}` parameter here, because the order of the values does not
not the one expected by the open data API. The function is written
then :

    in_bbox(coordonnees_geo,{south},{west},{north},{east})

Which gives with encoding:

    in_bbox%28coordonnees_geo%2C{south}%2C{west}%2C{north}9%2C{east}%29

The complete encoded request is therefore:

    https://opendata.paris.fr/api/explore/v2.1/catalog/datasets/velib-disponibilite-en-temps-reel/exports/geojson?where=in_bbox%28coordonnees_geo%2C{south}%2C{west}%2C{north}9%2C{east}%29&limit=-1&refine=is_installed%3AOUI

All that remains is to use this query as a URL for our data
distant.

Note that it is not necessary to use the encoded shape, because uMap
proceed to encoding. The URL can therefore be more readable:

    https://opendata.paris.fr/api/explore/v2.1/catalog/datasets/velib-disponibilite-en-temps-reel/exports/geojson?where=in_bbox(coordonnees_geo,{south},{west},{north},{east})&limit=-1&refine=is_installed:OUI

## Let's take stock

The card produced for this tutorial can be seen here:
<http://u.osmfr.org/m/1051915/>

We have seen how **to exploit open data** without the
download, which allows our map to stay up to date (provided
of course the data are updated by their producer). We
have also seen how **optimize the request** by injecting the
*bounding box* of the visible part of the card.

Other sites make data available through an API, the stakes
is then to appropriate the syntax of the requests by reading the
documentation and testing the requests.


??? info "License"

    Work initiated by Antoine Riche on [Carto’Cité](https://wiki.cartocite.fr/doku.php?id=umap:10_-_j_integre_des_donnees_distantes) under license [CC-BY-SA 4](https://creativecommons.org/licenses/by-sa/4.0/deed.en).
