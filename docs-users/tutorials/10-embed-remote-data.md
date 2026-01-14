!!! abstract "What You'll Learn"

    - Create a layer that uses remote data
    - Render a heat map
    - Display layers according to the zoom level
    - Display data that evolves in real time
    - Use an *open data* portal
    - Credit the data source to comply with the license


## Step-by-step procedures

So far all the maps we've created show data
controlled by uMap. Even when you used spreadsheet data
in the previous tutorial, the data was *imported* to
the uMap server, and that's where it is *stored*. If the data is
modified, you have to import it again to update the
map.

In this tutorial you will learn how to create a map that
use **remote data**, i.e. stored on separate
server from the uMap server.

### 1. Access remote data

For this tutorial we'll use the theme of bike-sharing stations to
Paris, the famous Vélib’, whose data is available in open
Data.

#### Access an open data portal

Let’s start by inspecting the dataset “Vélib’ - Location and
characteristic of the stations”, available on the open data portal of
the city of Paris :
<https://opendata.paris.fr/explore/dataset/velib-location-des-stations/>.

The **Information** tab explains that the data "is updated
every minute according to GBFS 1.0." This standard describes several
files, accessible via the API described in the API tab, whose
format is not understood by uMap.

The **Table** tab shows the data: each station has a name and a
capacity (number of docks), as well as a geographical position.

The **Export** tab offers several formats, including formats
**GeoJSON**, **KML** and **GPX**, all three included by uMap.
Choose the [GeoJSON format](https://en.wikipedia.org/wiki/GeoJSON),
which allows you to take advantage of all the data's attributes.

One option would be to download the file and then import it into
uMap, as you did in the previous tutorial with a CSV file.
Besides the extra modifications, this would involve updating
the data regularly. Instead, configure your map
to directly access the data provided by the open data portal.
To do this, copy the link to the file; a right-click
opens a context menu that allows us to **copy the file link**:

    https://opendata.paris.fr/api/explore/v2.1/catalog/datasets/velib-emplacement-des-stations/exports/geojson?lang=fr&timezone=Europe%2FBerlin

![umap-donnees-distantes.png](../static/tutoriels/10-jintegre-des-donnees-distantes/umap-donnees-distantes.png)

#### Configure remote data

Now let’s see how to use this link in uMap. For this we'll
create a new layer and open the **Remote data** tab, in the
Layer Properties. The following information should be provided:

-   **URL** : paste the link to the file you copied previously.
-   **Format** : select the format, **geojson** in this case
-   **License** : ODbL as indicated on the export page of the
    open data portal

The **Verify URL** button allows you to test the file access from
uMap, and to check that the chosen format corresponds to the data.
The data is then displayed on the map.

#### Proxy or not proxy?

If it doesn’t work (uMap displays a banner that says "Problem
in the server response"), it is likely that the server
where the file is stored does not allow access to the file
from a third party service.

!!! note

    This is the CORS mechanism, described in the
    Wikipedia article [Cross-origin resource
    sharing](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing).

uMap allows you to bypass this constraint by routing the
file via the uMap server, thanks to the **With proxy** option that
must be activated. This option is associated with the drop-down menu
**Hide the request with proxy**, which allows the uMap server to
keep the file so it doesn't need to be retrieved each time the map
is displayed. The longest duration (1 day) would be appropriate here.

#### About the license

The Vélib’ station locations file is published under the
[ODbL license](https://opendatacommons.org/licenses/odbl/). This
requires the producer of the data to be credited wherever it is
used. The information on the open data portal indicates that the
producer is "Autolib Velib Métropole". It should therefore be cited
in the map **Credits**, a tab under the *Properties* menu.

![umap-geojson-properties.png](../static/tutoriels/10-jintegre-des-donnees-distantes/umap-geojson-properties.png)

#### Show the name and capacity of the stations

To display the name and capacity of each station in one
tooltip, you need to determine the keys to access that
information. To do this, inspect the GeoJSON file.

You can download this file from the Export tab of the open data portal,
or paste the previously copied link into the navigation bar
of the browser. Whether the file is directly displayed in the
browser or it was downloaded, it can be opened
in a text editor or drag-and-dropped into the browser window.

In the `properties` block of each element, you'll see several
key-value relationships: the **name** property contains the name of the
station, **capacity** contains the number of docks. These properties
correspond to the column headers in your CSV file (see previous tutorial).

You can then format the **Popup Content Template** to display
this information in the tooltip for each station, as you've
seen in the [previous tutorial](9-map-from-spreadsheet.md).

For example :

    # {name}
    {capacity} docks

### 2. Combine two layers for the same data

There are many stations Vélib’ and the map is a little dense for
the Paris scale. At this scale it would be more interesting to have
an overview of the distribution of Vélib’ services across the capital
and the surrounding municipalities.

![umap-heatmap.png](../static/tutoriels/10-jintegre-des-donnees-distantes/umap-heatmap.png)

#### Produce a heat map

uMap allows to present the data of a layer in several forms,
with the **Layer Type** drop-down menu in the *Properties* menu for the
layer. The different types of layers are:

-   **Use default** : each row is displayed individually.
-   **With cluster** : the nearby points are grouped in a circle. 
-   **Heatmap** : the data is represented in the form of *heatmap*.
-   **Choropleth** : this display is intended for shapes rather than points,
    allowing for color gradation.
-   **Proportional circles** : this representation is intended for
    absolute quantitative values that can be tallied.
    The surface area of the circles is proportional to the quantity.

The types *With cluster* and *Heatmap* are most suitable for layers
containing only points. When you choose one of these modes, a
configuration tab appears. For the *Heatmap* type, the tab
**Heatmap: parameters** lets you adjust the intensity – or *heat* – of
the map (from icy blue to the red hot), and select a
property as the *heat* level. This must correspond to a
data property containing numerical values. If no
property is not defined, each point has the same value and the heatmap
will merely correspond to the geographical density of the points.

Our station file appropriately contains a `capacity` property,
which corresponds to the number of docks at each station – a good
match for representing the availability of shared bicycles. As for the
**Sheet radius**, a slider allows you to adjust it with instant feedback
from the map. It is a good idea to test this radius at different
zoom levels on the map, so the data remains visible on the map.

#### Duplicate the layer

The display type of a layer applies regardless of the zoom level.
But at high zoom levels, at the neighborhood scale, it is
more interesting to show individual stations than the heatmap.
Let's combine the 2 representations by creating 2 layers
which use the same data, one displaying the individual stations,
the other in the form of heatmap. The trick is then
to activate or disable each layer according to the zoom level.

Step by step:

1.  Let’s duplicate our layer with the **Clone** operation available in
    the **Advanced Operations** tab of the Layer Properties panel.
2.  The Properties panel of the new layer is then displayed;
    let’s rename this layer, for example "Vélib’ stations heatmap".
3.  Change the layer type to **Heatmap** so the **Heatmap:
    parameters** tab appears.
4.  In this tab, enter the property name - `capacity` - and
    adjust the **heatmap radius** (a value around 30 works
    well for this dataset)
5.  In the **Remote data** tab, configure the layer so
    that it is displayed **to** zoom 15.
6.  In the same way, configure the initial layer so that it
    is displayed **from** zoom 15.

Here we've chosen, at zoom 15, to override the heatmap with
individual stations. This produces a transition between the 2 modes of
representation, and allows the stations to be identified with a large number
of docks.

Please note that we did not need to specify the remote data's URL
or its format. These parameters were retained when the layer was cloned.

<!-- TODO: The remaining sections still need to be adapted to idiomatic English. -->

### 3. Use dynamic data

Another dataset from the open data portal is entitled "Vélib - Bikes
and docks - Real-time availability":
<https://opendata.paris.fr/explore/dataset/velib-disponibilite-en-temps-reel/>.

We may use this data *in real time* – in actuality, with a
slight delay – to feed our uMap, and display the number
of docks and bicycles available. The procedure is the same as
above, with a subtle change: the **Dynamic** option of the
**Remote data** tab must be enabled. This tells uMap to
retrieve the data each time the map is rendered, i.e.
each time the map is moved, zoomed in, or zoomed in. However,
this data will not be automatically updated by uMap at
regular intervals: it is up to the user to refresh the
web page or move the map.

![umap-api-properties.png](../static/tutoriels/10-jintegre-des-donnees-distantes/umap-api-properties.png)

We still need to change our popup template to display availability in
real-time. To find the property names, we can use
the **API** tab on the open data portal: the **Results** panel
shows some sample data with all its properties. These
properties are the same as for the GeoJSON export. Here is an example
of one potential popup template :

    # {name}
    {capacity} docks available, including {numdocksavailable} open spaces
    {numbikesavailable} bikes available, including {ebike} e-bikes

![umap-api-parameters.png](../static/tutoriels/10-jintegre-des-donnees-distantes/umap-api-parameters.png)

#### Filter data at the source

The Results panel in the **API** tab shows us the existence of the
property `is_installed`. This makes it possible to detect stations that
are not in service, which we do not wish to display on our
map.

The **Request panel for the API** call allows you to generate a query,
displayed under this panel (**API Call URL**), and view the
data produced by this query in the **Results** panel. This
also allows you to add parameters to the request, to filter the
data produced. The **refine** parameter allows you to filter the data
based on the value of one or more properties. If we
specify `is_installed` for the property name and `NON` for the
value, we can see the number of stations that are not in
service and that we do not want to integrate into our map.

The data produced using the **API** tab is in GBFS format,
which uMap doesn't support. Exporting requests in GeoJSON format
accept the same parameters. To produce the filtered data in
GeoJSON format, we have to edit the request *manually*.
Let's go step by step (warning: it's a bit geeky):

1.  Enter `is_installed` and `OUI` in the field **refine**
2.  Remove the value from the `limit` field, because we don't want to
    *limit* the response to only 20 stations.
3.  Look at the generated query:
    `/api/explore/v2.1/catalog/datasets/velib-disponibilite-en-temps-reel/records?refine=is_installed%3AOUI`,
    It consists of 3 sections:
    -   the basic URL, up to the last **`/`** character
    -   the **endpoint** `records`, followed by the **`?`** character
    -   the parameter `refine=is_installed%3AOUI` (`%3A` is the *encoding* for
        the **`:`** character)
4.  Now the request generated for the GeoJSON export:
    `https://opendata.paris.fr/api/explore/v2.1/catalog/datasets/velib-disponibilite-en-temps-reel/exports/geojson?lang=fr&timezone=Europe%2FBerlin`,
    It consists of the same sections:
    -   the basic URL :
        `https://opendata.paris.fr/api/explore/v2.1/catalog/datasets/velib-disponibilite-en-temps-reel/exports/`
    -   the endpoint `geojson?`
    -   the list of parameters `lang=fr&timezone=Europe%2FBerlin` (`%2F`
        is the encoding for the **`&`** character lets you separate
        several parameters)
5.  We can combine the URL and endpoint of the GeoJSON request,
    followed by the parameter `refine=is_installed%3AOUI` (the parameters
    `lang` and `timezone` are not useful here):

    `https://opendata.paris.fr/api/explore/v2.1/catalog/datasets/velib-disponibilite-en-temps-reel/exports/geojson?refine=is_installed%3AOUI`

Use this query as the URL for the remote data in our **Vélib’ Stations**
layer so that only stations that are in service will be displayed.

Note that the `exclude` parameter can be used to exclude more than just those
stations whose `is_installed` property has the value `NON`. We
can use the same mechanism to exclude stations that don't have
any bikes available:

    https://opendata.paris.fr/api/explore/v2.1/catalog/datasets/velib-disponibilite-en-temps-reel/exports/geojson?exclude=is_installed%3ANON&exclude=numbikesavailable%3A0

### 4. I inject parameters into the request

uMap allows you to inject parameters into a request, with syntax
`{paramX}`. These parameters depend on the status of the map at the time of
the sending of the request:

-   the coordinates of the map's center: {lat} and {lng}
-   the map's *bounding_box*: {bbox} or {west}, {south}, {east} and
    {north}
-   zoom level: {zoom}

The open data portal can take into account some of these parameters
to refine the request. Our goal here is to recover the
availability of stations **in the visible part of the map**,
that is, within the *bounding_box*. This helps to reduce the
volume of data transferred and display it faster.

#### Use the API console of the open data portal

The API tab of the dataset allows you to access the **Full API console**
In the Dataset section, we choose the *endpoint* **Export a dataset**.

![umap-api-console.png](../static/tutoriels/10-jintegre-des-donnees-distantes/umap-api-console.png)

After that, a form will appear where you can fill in the different
parameters:

-   **dataset_id** is the identifier of the dataset:
    `velib-disponitite-in-time-reel`
-   for **format** we select `geojson`
-   we can filter the stations in service again with the
    **refine** parameter : `is_installed:OUI`

![umap-api-console-dataset.png](../static/tutoriels/10-jintegre-des-donnees-distantes/umap-api-console-dataset.png)

Set the **where** parameter using the `in_bbox()` function (see the
[documentation
OpenDataSoft](https://help.opendatasoft.com/apis/ods-explore-v2/#section/ODSQL-predicates/in_bbox()))
and – for the moment – use hardcoded latitude and longitude (somewhere to
Paris):

![umap-api-console-bbox.png](../static/tutoriels/10-jintegre-des-donnees-distantes/umap-api-console-bbox.png)

**coordonnees_geo** is the name of the field containing the geometry in the
original data, which can be found by exporting it as a format
other than GeoJSON.

Let's test now that the query works by clicking **Execute**:
the response code 200 indicates that the request worked, and it is
possible to download the resulting file.

![umap-api-console-execute.png](../static/tutoriels/10-jintegre-des-donnees-distantes/umap-api-console-execute.png)

#### Make the request dynamic

Now let's change our *static* request (all parameters are
hardcoded) to make it *dynamic*, replacing the coordinates of the
bounding_box by the parameters that will be injected by uMap. We
do not use the `{bbox}` parameter here,  because the order of the values
​​does not correspond to that expected by the open data API. Therefore the
function is written:

    in_bbox(coordonnees_geo,{south},{west},{north},{east})

which is encoded as:

    in_bbox%28coordonnees_geo%2C{south}%2C{west}%2C{north}9%2C{east}%29

The complete encoded request is therefore:

    https://opendata.paris.fr/api/explore/v2.1/catalog/datasets/velib-disponibilite-en-temps-reel/exports/geojson?where=in_bbox%28coordonnees_geo%2C{south}%2C{west}%2C{north}9%2C{east}%29&limit=-1&refine=is_installed%3AOUI

All that's left is to use this query as a URL for our remote data.

Note that it is not necessary to use the encoded shape, because uMap
performs the encoding. The URL can therefore be more readable:

    https://opendata.paris.fr/api/explore/v2.1/catalog/datasets/velib-disponibilite-en-temps-reel/exports/geojson?where=in_bbox(coordonnees_geo,{south},{west},{north},{east})&limit=-1&refine=is_installed:OUI

## Let's take stock

The map produced for this tutorial can be seen here:
<http://u.osmfr.org/m/1051915/>

You have seen how to **take advantage of open data** without manual
export, which allows our map to stay up to date (provided
of course the data is updated by its producer). You
have also seen how to **optimize the request** by injecting the
*bounding box* of the visible part of the card.

Other sites make data available via API; the only challenge
now is to understand the syntax of the requests by reading the
documentation and testing the requests.


??? info "License"

    Work initiated by Antoine Riche on [Carto’Cité](https://wiki.cartocite.fr/doku.php?id=umap:10_-_j_integre_des_donnees_distantes) under license [CC-BY-SA 4](https://creativecommons.org/licenses/by-sa/4.0/deed.en).
