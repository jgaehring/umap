!!! abstract "What We'll Learn"

    - Check the file formats
    - Import the file into uMap
    - Adjust the appearance of circles

## Step-by-step procedures

We will import quantitative data and represent them in the form of proportional circles. We can also represent remote data by proportional circles (see more advanced tutorials).


### 1. Check the file format

To be usable in uMap, the file must be saved in `.csv` format, it must integrate geographic coordinates. Without these two conditions, the data file is not processed.

It is also necessary to avoid the shaping of the space type between blocks of three zeros, otherwise the circles will not be proportional, but all of the same size.

If latitude and longitude are not present, the file must be geocoded.
The website of the National Address Database offers a very practical tool: <https://adresse.data.gouv.fr/csv>

Simply place a file in `.csv` format containing addresses and click on "geocoding". The online tool adds the geographical coordinates of the addresses.

### 2. Import the file into uMap

Click on the import tool in the right bar:

<shot-scraper
    data-output="static/tutoriels/upload-data.png"
    data-url="https://umap.openstreetmap.fr/fr/map/new/"
    data-alt="Data import button."
    data-width="46"
    data-height="47"
    data-selector=".leaflet-toolbar-icon.upload-data"
    data-padding="5"
    >Data import button.</shot-scraper>

Then choose the file, for example here the municipal population of Cher, the format is `.csv` and click on "import":

![](../static/tutoriels/circles-markers.png)

All municipalities are represented by a pointer. It remains to be specified that the data of this layer must be displayed in proportional circles. To do this, click on the tool "Manage the layers" in the right bar:

<shot-scraper
    data-output="static/tutoriels/control-browse.png"
    data-url="https://umap.openstreetmap.fr/en/map/new/"
    data-alt="Layer(s) selector icon."
    data-selector=".umap-control-browse"
    data-width="48"
    data-height="48"
    data-padding="5"
    >Layer selector icon(s).</shot-scraper>

Then in the drop-down menu, select “Proportional Circles” and the data of your table that you want to represent in proportional circles:

![](../static/tutoriels/circles-proportional.jpg)

It is quite possible to adjust the proportionality on the bars of minimum and maximum radius to modify the rendering: the gap is then amplified or rather crushed.

!!! notes

    To change the colors of the circles, see the tutorial
    [Draw on your map](/en/tutorials/4-draw-items/).
