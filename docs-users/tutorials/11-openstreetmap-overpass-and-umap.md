!!! abstract "What We'll Learn"

    - Create a layer using *remote data* i.e. no
      stored by uMap
    - Use an **Overpass** request as a source of remote data
    - Use a *dynamic request* taking into account the visible extent
      of the map
    - Control the display of layers according to the zoom level

## Step-by-step procedures

The aim of this tutorial is to explore the different ways
display external or remote data on an uMap map,
that is, data that is not stored on the uMap server.
For this we will use data **OpenStreetMap**, which we
Let's extract with the [API
Overpass](https://wiki.openstreetmap.org/wiki/FR:Overpass_API/Overpass_QL).

We will in a few steps create a map of the bike in Nantes,
showing parking and self-service rentals.

### 1. I create a layer displaying the result of an Overpass query

Let's start by showing the stations *Bicloo*, the bike rentals in
Self-service in Nantes. Let’s go step by step:

1.  produce and test the Overpass query with Overpass Turbo
2.  adapt the request to produce data accepted by uMap
3.  export the request
4.  create a uMap layer using this query

#### Create the Overpass query

The site [Overpass Turbo](http://overpass-turbo.eu/) offers an assistant
which facilitates the drafting of a request. Activate the assistant and
enter the following text, which allows you to extract bicycle rentals
located in the municipality of Nantes :

    amenity=bicycle_rental in Nantes

Click on **Build and execute the query** : the query is created
in the editor on the left of the map, and then the result is displayed on the
map.

![Screenshot of the Overpass Turbo site using the assistant](../../static/tutoriels/11-je-valorise-les-donnees-openstreetmap-avec-overpass-et-umap/overpass_turbo_assistant.png)

#### Adapt the query for uMap

Before exporting the request we must adapt it. The Overpass Assistant
Turbo produces queries whose result is in JSON format. uMap
knows how to read data in several formats, including the GeoJSON format,
but not the JSON format produced by Overpass. However, uMap includes
very well the XML format according to the OSM syntax (OpenStreetMap).

For the query to produce data in XML/OSM format, simply
modify in the query editor the clause **`[out:json]`** by
**`[out:xml]`**. You can run the query again and observe
the format difference in the **Data** tab that shows the result
of the request.

![Screenshot of the Overpass Turbo site with XML enabled and data made visible](../../static/tutoriels/11-je-valorise-les-donnees-openstreetmap-avec-overpass-et-umap/overpass_turbo_format_xml.png)

#### Export Overpass query

Export the query by clicking on **Export**: a panel is displayed.
Go to the **Request** part and right click on **compact** to the right of
**Overpass QL** and choose **Copy link address** (with Mozilla Firefox):
The URL of the request is copied to the clipboard.

![Screenshot of the Overpass Turbo site with the progress of the operations to be carried out](../../static/tutoriels/11-je-valorise-les-donnees-openstreetmap-avec-overpass-et-umap/overpass_turbo_exporter.png)

#### Use the query in uMap

![Screenshot from Umap](../../static/tutoriels/11-je-valorise-les-donnees-openstreetmap-avec-overpass-et-umap/umap_requete_overpass_url.png)

In a new uMap card, create a layer and open the tab
**Distant data**. Paste the contents of the
clipboard and select the **osm** format, which corresponds to the format
XML in Overpass.

Note that the URL is *encoded* to be used as a query
HTTP: Special characters like `"` are converted to `%22`. Do not
Don't change!

You can configure the layer as described in the
Previous tutorials.

![Screenshot of the uMap site with the markers displayed](../../static/tutoriels/11-je-valorise-les-donnees-openstreetmap-avec-overpass-et-umap/umap_overpass_infobulle.jpg)

In the same way that the values of a spreadsheet can be displayed in the
tooltips (see [this section](9-map-from-spreadsheet.md)
from the previous tutorial), you can display in the tooltips the
*tags* OpenStreetMap. Available tags are visible in the tab
Data on Overpass Turbo.

For example, the following template allows you to display tooltips like
The one on the right.

    # {name}
    {capacity} locations
    Credit card : {payment:credit_cards}
    {note}

### 2. I display bicycle parking efficiently

Let's add to our menu the bicycle parking. The Overpass request for
obtaining the bicycle car parks of Nantes is similar to the one used
for rentals, and can be created with the assistant:
`amenity=bicycle_parking in Nantes`.

The execution of this request takes almost 5 seconds. This delay is too much
long for a *interactive* card. Also rather than executing the
query when displaying the card we prefer to extract the
data and import them into uMap.

#### Import static data

![Screenshot of the Overpass Turbo site with the place to click](../../static/tutoriels/11-je-valorise-les-donnees-openstreetmap-avec-overpass-et-umap/overpass_turbo_export_geojson.png)

In Overpass Turbo, click **Export**, in the section
**Data** there is a category **GeoJSON**, click on **download**. This
operation converts the result of the query into the GeoJSON format (a
standard format for transferring geographic data over the internet)
and create a file named `export.geojson` in the folder
`Downloads` of your computer
(you can also click **copy** and use your clipboard).

In the uMap card import the file thus produced in a new one
layer (see [this section](9-map-from-spreadsheet.md) from the previous tutorial).
Bicycle parking is displayed but the map
loses fluidity and does not react immediately when zooming or
move. This is due to the high number of markers displayed on the map
(over 1600).

#### Show a density map

![UMap settings to display a density map](../../static/tutoriels/11-je-valorise-les-donnees-openstreetmap-avec-overpass-et-umap/umap_heatmap.png)

A possibility for
Bypassing this problem is to display markers as
clusters, or heatmap, also called map of
density. We choose the second option that allows to take in
counts the number of places of each parking lot, stored in the tag
`capacity`.

Thus the map will show not the number of bicycle parkings but the
number of parking spaces (in OpenStreetMap a single parking lot to
bicycle can represent a large number of *bike support*).

In the properties of the layer, select the Layer Type
**Heatmap**.

Then, in the **Advanced Properties**tap `capacity` in
the **Optional property field to use to calculate the intensity
from the heatmap**. Finally you can adjust the intensity of the color in
modifying the **Ray value for the heatmap**.

The map gains fluidity, but the use of a *heatmap* does not allow
not to identify the precise location of bicycle parking. The stage
following proposes a solution to solve this drawback.

### 3. I display a layer based on the zoom level

When the data of a layer is ***distant*** (i.e.
**no** stored on the uMap server), it is possible to control
display of this data according to the zoom level. It takes for
this drops the data file on a server and determine the URL of
that file.

#### Using a file stored on a server

![umap_donnees_distantes_wordpress.png](../../static/tutoriels/11-je-valorise-les-donnees-openstreetmap-avec-overpass-et-umap/umap_donnees_distantes_wordpress.png)

If you have FTP access to a server, this does not
difficulty. If you have access to the *back office* of a CMS such as
Wordpress, you can probably drop a file. Let's take
Example of Wordpress.

For security Wordpress does not allow to deposit a file in format
JSON. It relies on the extension of the file name, so it is
possible to bypass this constraint by renaming the file.
Proceedings in stages.

1.  rename the file `export.geojson` produced above in
    `parkings-velos-nantes.txt`
2.  in the *back office* Wordpress, add a **Media** and
    select the file so renamed
3.  view the file details and copy its **Web address**, from the
    form
    `http://monsite.fr/wp-content/uploads/2018/01/parkings-velos-nantes.txt`
4.  create a new uMap layer and paste this web address into the
    **URL** field of the **Remote data** tab
5.  select **geojson** format
6.  specify the license that applies to the data: **ODbL 1.0**
    This is OpenStreetMap data
7.  Enable the **With proxy** option at the bottom of this tab: this allows
    the web browser to access a file stored on a different server
    that the uMap server
8.  save the changes to the card

#### Combine two layers using the same file

To combine fluidity of the map and display of each car park us
will associate two layers using the same data:

-   up to zoom level 16, a layer showing the capacity of
    parking in the form of *heatmap*
-   from zoom level 16, a layer showing the car parks to
    Bike in the form of markers

Let's proceed in stages again.

1.  edit the previously created layer and in the **Data tab
    remote** enter the value **16** in the **up to field
    zoom**
2.  duplicate the layer with the **Cloner** action of the **Actions tab
    advanced** : so the new layer is already configured to
    use the file placed on the server
3.  select the **Default layer type** for the new layer
4.  in the **Remote data** tab, enter the value **16** in
    the field **From zoom**

![umap_heatmap_et_infobulle.jpg](../../static/tutoriels/11-je-valorise-les-donnees-openstreetmap-avec-overpass-et-umap/umap_heatmap_et_infobulle.jpg)

Finally you can rename the new layer, configure the type of
marker, and define the popup template, for example:

    # {capacity} locations
    Type : {bicycle_parking}
    Covered : {covered}

The image on the right shows an extract of the map at the zoom level 16,
to which we have chosen to display the two layers.

### 4. I use a dynamic request

Use extracted data rather than a query presents a
disadvantage: the update of the data on OpenStreetMap is not
uploaded to our map. To overcome this we offer you
modify the layer showing the bicycle parking in the form of
markers, so that it uses a dynamic request.

A **dynamic request** allows to *inject* into the request of
*variables* relating to the current status of the uMap card. We're going
use a query that applies to the only visible part of the
card, defined by a rectangle (or *bounding box*). This request
will run with each zoom or displacement of the map (hence the term
*dynamic*) and will pick up bicycle parking inside this
rectangle.

#### Simplify the Overpass request

To facilitate the operation we start with
simplify the Overpass request. The important points are:

1.  place the clause **`[bbox:{{bbox}}]`** at the query header for
    This parameter is only present once
2.  replace the production of the result with clause **`out center;`**
    which allows to convert each *way* (closed or not) to a point

        [out:xml][bbox:{{bbox}}];
        (
         node["amenity"="bicycle_parking"];
         way["amenity"="bicycle_parking"];
        );
        out center;

We then obtain this result on the map:

![Capture the Overpass Turbo site with the new query](../../static/tutoriels/11-je-valorise-les-donnees-openstreetmap-avec-overpass-et-umap/requete_dynamique.png)


#### Adapt and export the query


The operation is delicate, and requires cold blood and concentration:

1.  replace `{{box}}` with `{south},{west},{north},{east}`: this is
    of 4 variables that uMap will replace, when performing the
    request, by the values defining the control of the card.
2. **export** the request using the option **standalone request → download** :
    A text file is produced and downloaded.
    ![Capture the Overpass Turbo site with the new modified request](../../static/tutoriels/11-je-valorise-les-donnees-openstreetmap-avec-overpass-et-umap/requete_dynamique_2.png)

3.  open the file in a text editor and add at the beginning of
    line the base of the URL to execute an Overpass request:
    `http://overpass-api.de/api/interpreter?data=`
4.  Copy the modified query and paste the text into the URL field of
    the **Remote Data** tab
5.  Enable the **Dynamic** option and set the zoom from which
    The layer is displayed
6.  according to the Overpass server used, the option **With
    proxy** must be enabled or disabled (see below)

For convenience the modified request is taken below:

    http://overpass-api.de/api/interpreter?data=[out:xml][bbox:{south},{west},{north},{east}];(node["amenity"="bicycle_parking"];way["amenity"="bicycle_parking"];);out center;


!!! note
    Do not hesitate to use another Overpass server in
    self-service, the list of which is available in the **Settings
    Generals** of Overpass Turbo, for example
    `https://overpass.kumi.systems/`. Attention the latter requires
    **enable** option **With proxy**, while the server
    `http://overpass-api.de/` requires the option to be **disabled**.

!!! note

    Do not use the variable `{bbox}` because it will be
    replaced by coordinates whose order (W,S,N,E) is not that
    expected by Overpass (S,W,N,E)!

You can manipulate below the map produced by this
tutorial. Zoom in until the bicycle parking lots appear and
move the map to see the dynamic aspect of the requests.

<iframe width="100%" height="400px" frameBorder="0" src="https://umap.openstreetmap.fr/fr/map/le-velo-a-nantes_189194?scaleControl=false&miniMap=false&scrollWheelZoom=false&zoomControl=true&allowEdit=false&moreControl=false&searchControl=null&tilelayersControl=null&embedControl=null&datalayersControl=false&onLoadPanel=undefined&captionBar=false"></iframe><p><a href="http://umap.openstreetmap.fr/fr/map/le-velo-a-nantes_189194">Voir en plein écran</a></p>


## Let's take stock

We saw how to create a map showing OpenStreetMap data
Up-to-date, using Overpass requests. Only the layer showing the
density of parking in the form of *heatmap* will require
renew the extraction of data from time to time.

!!! note
    The Overpass servers used in this tutorial are
    self-service servers made available free of charge. These
    servers are also very in demand it should use them with
    moderation.

    If you produce a map for a large number of consultations,
    prefer the use of static data, imported into uMap or
    stored on a server. Thank you!

    If you use Github, this [short
    tutorial](https://hackmd.io/OkwpRqQ7QXC3p8C0jfTUGQ?view) in English
    Explains how to use a *workflow* to execute a query
    Overpass and cache the result.


??? info "License"

    Work initiated by Antoine Riche on [Carto’Cité](https://wiki.cartocite.fr/doku.php?id=umap:10_-_j_integre_des_donnees_distantes) under license [CC-BY-SA 4](https://creativecommons.org/licenses/by-sa/4.0/deed.en).
