!!! abstract "What We'll Learn"

    - Import the outline of a municipality
    - Import contours of departments or regions
    - Import a point of interest (libraries, car parks, ...) which is registered on OpenStreetMap

## Step-by-step procedures

It is advisable to check if the data does not exist before embarking on their drawing. You can save valuable time with the imported assistant built into uMap and keep a card that is not too heavy on loading.

Here are the two actions to perform once a pre-existing card, or a new blank card open:

- Click on the data import tool in the right bar and select the already ready-made data
- Click on "Import" and if necessary wrap the map, because default figures are used

uMap allows you to use data produced by many services and placed in open data in different formats. We will see later (intermediate level) where to search for these sources. Already, you can use the import wizard to recover administrative contours and points of interest with one click.

### Resources available (20/09/2024)

As of September 20, 2024, the following imports are available:

- contour of a commune
- contours of departments and regions
- data from OpenStreetMap placed in [GeoDataMine](https://geodatamine.fr/). As the name suggests, GeoDataMine is a real wealth of data very useful for public services:
    - Playground
    - Bicycle-can-drive
    - Banks and DAB
    - Base Address
    - Libraries
    - Cemetery
    - Cinemas
    - Shops
    - Carpooling
    - Waste and recycling... until Toilets
- overpass : to familiarize yourself with the types of queries to fill in in the wizard, consult the more advanced tutorials and the [ wiki page](https://wiki.openstreetmap.org/wiki/Overpass_turbo/Wizard)


!!! note
    Is there a lack of data? Do not hesitate to contribute to add them and you will be the first beneficiaries!


### Click on the data import tool

Here is a brief review of the various imports proposed and to finish the import of the location of the libraries of Clermont-Ferrand:

![Animated gif showing the use of the import assistant](../../static/tutoriels/importer.gif)

## 1. Importing the outline of a municipality

Click the import tool at the bottom of the right bar, and then click on the “Import Wizards” link.

Click on "Communes France" and select the desired municipality from a drop-down list. Once the municipality is selected, the format is recognized automatically (geojson) and then the type of layer (click on "? » to know what choice to operate)

1. To simply copy the data, choose “Copy to layer”.
2. To change the card if the outline changes, choose “Associate with the layer as remote data”.

!!! note
    The code displayed is not the postal code but the INSEE code of the municipality.

Here is the result with the municipality of Arles (the largest in metropolitan France, a certain gain if we save money to draw its outline!)
![A map with the drawing of the imported commune of Arles](../../static/tutoriels/importer-arles.png)

Once this import has been made, everything is adjustable: contour color, background, display yes no of a label.

## 2. Import contours of departments or regions

Click the import tool at the bottom of the right bar, and then click on the “Import Wizards” link.

Click on “National contours” then either departments or regions and finally the type of layer (see above the explanation). All departments are imported:

![A map with the drawing of each department imported](../../static/tutoriels/importer-departements.png)

##3. Importing a point of interest from GeoDataMine

Click the import tool at the bottom of the right bar, and then click on the “Import Wizards” link.

Click on “GeoDataMine (OSM themes)” and select the desired information, roads, buildings, shops, utilities, ...
For example, by selecting the drinking water points of the CA du Grand Avignon, then “Copy in a layer”

![A map with drinking water points from OpenStreetMap](../../static/tutoriels/importer-geodatamine.png)

Here is a real saving of time rather than placing pointer after pointer all the water points.

## 4. The combined map

Of course, we can quite combine the different layers of information and present for example the map of the Drinking Water Points in the CA of the Grand Avignon, with the contours of the municipalities that make up the EPCI, the department and the region:

### Drinking water points of the Grand Avignon

![A map combining several imports](../../static/tutoriels/importer-multi.png)

[View full screen map](https://umap.openstreetmap.fr/fr/map/points-deau-potable-grand-avignon_1116739?scaleControl=false&miniMap=false&scrollWheelZoom=true&zoomControl=true&editMode=disabled&moreControl=true&searchControl=null&tilelayersControl=null&embedControl=null&datalayersControl=true&onLoadPanel=none&captionBar=false&captionMenus=true#11/43.9889/4.7962){ .md-button }

In this case, it will be necessary to delete all unnecessary information in the data table that is accessible in the left bar for each layer.

To save time: select all departments and deselect only the Vaucluse, then click on “Delete selected rows”.



