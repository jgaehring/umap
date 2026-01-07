!!! abstract "What We'll Learn"

    - consult data sources
    - discover examples of maps
    - clone a map uMap
    - practical case: use a dataset placed on data.gouv.fr

## Open data (open data)

In addition to the data produced by my OpenStreetMap community, accessible on [GeoDataMine](https://geodatamine.fr/) and in [uMap data import assistant](6-one-click-data-import.md), the open data resources are numerous and varied. Indeed, communities with more than 3 500 inhabitants and public services must place their data in open data in accordance with the [Law for a Digital Republic](https://www.vie-publique.fr/eclairage/20301-loi-republique-numeric-7-October-2016-loi-lemaire-ques-changes). The public data service organizes their publication on [data.gouv.fr](https://www.data.gouv.fr/fr/) which is a generalist portal.

There are also more databases adapted to datasets, for example archives, geographical, socio-economic data... Communities sometimes also make their data available directly on their open data portals. Solution vendors also offer databases.


## 1. Data formats used by uMap

### geojson

This format is used for data such as point, line, string, polygon.

All properties are imported into uMap.

❓ Wide use in uMap.

### gpx

This open format allows the exchange of geographical coordinates from GPS, route points (*waypoints*), traces (*tracks*) or routes (*routes*).

Properties imported into uMap : `name`, `desc`. (format for routes)

❓ Gpx files can come from personal recordings, for example from traces collected hikes.

### kml

Owner format that contains geographical coordinates, markup, styles to represent points, lines, and polygons.

Imported properties in uMap: `name`, `description`.

## csv

It is an open text format representing tabular data in the form of comma-separated values. To use an Excel file, you must first convert it to `.csv`.

Properties imported into uMap: comma, tab or point to separate values. The SRS WGS84 projection is implicit. Only geometric points are imported. The import will refer to the title in the column headers of `lat` and `lon` at the beginning of the header, and is insensitive to the breakage (no matter the capital or lowercase). All other columns are imported as properties.

❓ Very wide use in uMap, both for data in *open data* and for its own data.

### umap

This is the recording format of a card, which is widely used for example to clone a card on the OSM instance and import it to the uMap instance for public agents. uMap imports all data from the card, including layers and properties. This is a good way to save your uMap card.

❓ See below, how to clone a uMap card.

As well as osm and georss.

## 2. Orient yourself on data.gouv.fr

The platform [data.gouv.fr](https://www.data.gouv.fr/fr/) offers harmonized data, specifies the update date and allows to contact the administrator who has deposited the dataset. Simply use the search tool to specify your request and select the desired result.
The main difficulty: to know which dataset would meet the need. In this case, it is advisable to also look at the “themes” and “reuses” at the bottom of the home page.


##3. Gallica! the archives of the National Library of France

[Gallica base](https://gallica.bnf.fr/accueil/fr/content/accueil-fr?mode=desktop) is especially useful for displaying in uMap images, postcards, backgrounds of old cards. It is not mandatory to download the illustration, some maps simply place the link to display:

### Views of cities in the 16th and 17th centuries

![Screenshot of the map](../static/tutoriels/find-data-villes.png)

[Link to online map](https://umap.openstreetmap.fr/fr/map/vues-de-villes-aux-xvie-et-xviie-siecles_635544#7/46.241/-1.329){ .md-button }

Two examples using an old plan as background, in addition to the old images that appear by clicking on a pointer:

### Photographs of Marseille 1862 to 1866 by A. Terris


![ Screenshot of the map](../static/tutoriels/find-data-photos-marseille.png)

[Link to online map](https://umap.openstreetmap.fr/nl/map/photographies-de-marseille-1862-a-1866-par-a-terri_277962#14/43.2909/5.3815){ .md-button }

### Metz 1872

![Screenshot of the map](../static/tutoriels/find-data-metz-1872.png)

[Link to online map](https://umap.incubateur.anct.gouv.fr/fr/map/metz-1872_50#13/49.1201/6.1419){ .md-button }

In these last two cases, the background of the map must be “stowed” before being used in uMap as [custom background](https://forum.openstreetmap.fr/t/integrer-un-fonds-de-carte-personalise-sur-umap/19606).

## 4. Statistical databases

uMap allows to represent quantitative data through [proportional circles](8-proportional-circles.md) or [choroplethic cards](10-embed-remote-data.md#produce-a-card-of-heat-or-heatmap) i.e. color ranges.

The [INSEE](https://www.insee.fr/fr/accueil) and [Eurostat](https://ec.europa.eu/eurostat/fr/data/database) allow general statistical files to be downloaded.

Once a file is saved, you must check the format of the data and modify it if necessary. Beware, for example, of merged cells and spaces between zero series.

##5. Cloning a card uMap

To use the data of a card on another background, make several versions, just clone the card.

Example of need: present on a website the same card several times, diversifying the centering and the backgrounds of cards. The same initial map provides several views from clones.

!!! french-instance "For public officials"

    This feature also allows you to import on [the uMap public agents instance](https://umap.incubateur.anct.gouv.fr/en/) a map made on another instance.

    Here are the actions :

    - save the card you want to clone
    - create a new card - to clone the card to a new instance: connect to the new instance and then create this new card and
    - import the card.

    Both cards co-exist, a change on one card does not impact the other card. If the card is shared on a website, make sure to **update the link** in the event of a change of instance.

### 1. Save the map

Click on the left on “Share and download”

<shot-scraper
    data-output="static/tutoriels/control-embed.png"
    data-url="https://umap.openstreetmap.fr/en/map/new/"
    data-alt="Icon of sharing and integration."
    data-selector=".leaflet-control-embed"
    data-width="48"
    data-height="48"
    data-padding="5"
    >Allows you to share the map or export the data.</shot-scraper>

then once the side screen is displayed:

![Screenshot of the card download panel](../static/tutoriels/find-data-download.png)

Click on “Full Backup” at the bottom.

### 2. Create a map and import the file

Leave this screen, create a new map and then right-click on “Import data” and then once the side screen is displayed:

![Screenshot of the import module](../static/tutoriels/find-data-import-umap.jpg)


The import format recognizes uMap and specifies it.

Click "Import" and save.

## 6. Practical case: use a dataset placed on data.gouv.fr

For use in uMap, the files must contain the geographical coordinates of the objects. If the chosen file does not contain it, see [here](12-display-grist-data.md#2-geocoder-des-addresses-for-agents-publics-only) how to add them (geocoding).

Here are the actions to map the remarkable trees in Metz: search for data, import them into uMap and rework them to improve label placement.

### Search for data

The open platform of French public data lists thousands of datasets. Search for “Metz Trees” in the search tool.

Two solutions to use this data:

* Recover the file in json format: it will be necessary to update the map from time to time when the source data is updated. Benefit: an up-to-date card on a specific date.

or

* use the link to the data: in this case, the map will automatically update (deletion of cut trees for example, addition of new ones). Disadvantage: the card is a T-time card, we do not keep the history in this case.

![Screenshot of the datagouv site](../static/tutoriels/find-data-datagouv.jpg)

You have a choice. Once the file has been downloaded or the link is copied, click in the map on uMap the "Import data" button in the right bar and then in the frame of your choice:

* Browse downloaded files and choose the file of remarkable trees in Geojson format

or

* Paste the stable URL into the intended line

![Screenshot of the import panel (1)](../static/tutoriels/find-data-import-panel-1.png)
![Screenshot of the import panel (2)](../static/tutoriels/find-data-import-panel-2.png)

In “Choose data format”: select `Geojson`. In case you choose the stable URL, you can choose `Associate with the layer as remote data` and in this case the card automatically updates if the file is changed.

Choose `Copy in layer` to keep the card as it is on a date T.

The map is automatically centered on Metz and all the remarkable trees are placed:

![Screenshot of the map](../static/tutoriels/find-data-screenshot-trees.png)

The information in the file is passed down and accessed in a table or by clicking on each tree.

### Change the appearance of pointers to fit the charter of a site

Select the layer in the right bar and change its settings by clicking on the small pen:

![Screenshot of the view panel](../static/tutoriels/find-data-visualize-data.png)

Name : Remarkable trees (or for example Hardwoods or Trees over 50 years old...), as many possibilities as layers and colors. Then click on the properties of the shape to choose the color and shape of the pointer, but also the interaction options: display a label on the fly for example.

![Screenshot of the card and customization panel](../static/tutoriels/find-data-trees-customisation.png)

### Display the names of the trees on the flyby

All data that can be displayed in the label is presented in the columns of the table associated with the layer. Click on the data explorer on the left and then on the "Edit in a table" visual (just to the left of the trash can):

<shot-scraper
    data-output="static/tutoriels/control-browse.png"
    data-url="https://umap.openstreetmap.fr/en/map/new/"
    data-alt="Layer(s) selector icon."
    data-selector=".umap-control-browse"
    data-width="48"
    data-height="48"
    data-padding="5"
    >Layer(s) selector icon.</shot-scraper>

In the case of the Metz remarkable tree file, the name of the trees is filled in as `common_name` and `name_latin`. However, in uMap, by default, the labels that appear use `name`. For the common name to appear, replace `name` with `common_name` on the right in the "Advanced Properties" (Information panel of this layer):

![Screenshot of the card and customization panel](../static/tutoriels/find-data-trees-customisation-advanced.png)

To make the label only display on the flyby, choose `Hiden` a little further down in "Show a label".

!!! note

    - To train, open the settings, the card can be cloned here:
    https://umap.incubateur.anct.gouv.fr/fr/map/diaporama-des-arbres-remarquables-a-metz_528
    - To clone a map, see the explanation at point 5 above.

