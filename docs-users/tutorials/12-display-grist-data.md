!!! abstract "What We'll Learn"

    - Create a Grist template compatible uMap
    - Geocoder addresses (:fontawesome-solid-landmark-flag: for public officials only)
    - Make a document Grist public
    - Link the CSV of Grist with a layer uMap


A [a tutorial film](https://tube.numerique.gouv.fr/w/kya6m1aFtgDcy2LMkgUBya?start=12s)
was created to show the course of this tutorial.


## 1. Create a Grist template compatible uMap

!!! osm-instance "For the general public, associations..."

    Visit the [official Grist website](https://www.getgrist.com/) or your own instance.

!!! french-instance "For public officials"

    Visit the Grist public agents website via
    [The Digital Suite](https://lasuite.numerique.gouv.fr/services/grist).

Create a new empty document :

![Interface to create a new Grist document.](../../static/tutoriels/grist-new-document.png)

Add the necessary columns, plus at least these three columns: `Address`, `Latitude`, `Longitude'.

![Interface of a new empty Grist document.](../../static/tutoriels/grist-empty-document.png)


!!! warning

    Attention, it is necessary to put the columns `Latitude` and `Longitude` in type `Text` :

    ![Interface to enter the column type.](../../static/tutoriels/grist-column-type-text.png)


## 2. Geocoder addresses (:fontawesome-solid-landmark-flag: for public officials only)

!!! french-instance "For public officials"

    This conversion is only accessible to public officials, it consists of
    automatically convert addresses into geographic coordinates
    (Latitude, longitude). If you already have this information in your
    document, you can proceed to step 3 below.


It is now necessary to add the geocoding tool developed by the ANCT.
To do this, click on "Add a view to the page" :

![Interface to create a Grist view.](../../static/tutoriels/grist-empty-view.png)


Then choose `Custom`, select the name of the table in the data source
(here "Table1"), and also select the table in `Select by` :

![Interface to create a custom view Grist.](../../static/tutoriels/grist-custom-view.png)

In the right column, if you are on the Grist instance of the ANCT,
choose "Geocoder" from the drop-down list,
otherwise choose `Custom URL` and add the following URL:

<https://betagouv.github.io/grist-custom-widgets-fr-admin/geocode>

In the right panel, select the columns to connect
the tool on our table :

![Interface to associate columns on a Grist view.](../../static/tutoriels/grist-columns-view.png)

The `Address` column as source, then refers well to the columns `Latitude` and `Longitude'.

You can optionally add a `Standard Address` column (in the spreadsheet)
and reference it here, in this case the geocoder will display the address it has found.
It allows for more control.

Then enter one or more lines of data,
Trying to have an address as accurate as possible:

![Interface to convert via a Grist view.](../../static/tutoriels/grist-conversion-view.png)

Then click on “Specific Treatment” to treat
that the selected line, or on “Global Processing”
to process all the lines of the document.

![Interface to convert via a Grist view (result).](../../static/tutoriels/grist-conversion-view-result.png)


## 3. Make a document Grist public

It is then necessary to make the document Grist public to be able to then reference it on the uMap side.

For this, go to “Manage users”:

![Interface to manage users in Grist.](../../static/tutoriels/grist-user-management.png)

Then activate public access:

![Interface to open permissions in Grist.](../../static/tutoriels/grist-permissions-management.png)


## 4. Link the Grist CSV with a uMap layer

To copy the URL that we will indicate on the uMap side, it is here
(right click “record link”):

![Interface to copy the link to the CSV export in Grist.](../../static/tutoriels/grist-download-csv.png)

The link should look like something like that:

https://grist.incubateur.net/o/docs/api/docs/4McELEs6kBpQAkmzupHy9F/download/csv?viewSection=1&tableId=Table1&activeSortSpec=%5B%5D&filters=%5B%5D&linkingFilter=%7B%22filters%22%3A%7B%7D%2C%22operations%22%3A%7B%7D%7D

Now, create a map on uMap and add a layer:

![Interface to add a layer in uMap.](../../static/tutoriels/grist-umap-newlayer.png)

![Interface to add a layer in uMap with a name.](../../static/tutoriels/grist-umap-newlayer-name.png)

In “Remote Data”, add the Grist URL and choose the `CSV` format:

![Interface to add a layer in uMap with a URL.](../../static/tutoriels/grist-umap-newlayer-url.png)

For a better user experience, you can choose
the `Proxy` option with a cache of the right duration according to frequency
update data in Grist :

![Interface to add a layer in uMap with a proxy.](../../static/tutoriels/grist-umap-newlayer-proxy.png)

To improve data integration, go to the advanced settings
of the card, then in the default properties and:

-   add `Name` as key for label, filter and search
-   add `Category` to generate automatic filters

![Interface to add a layer with filters in uMap.](../../static/tutoriels/grist-umap-newlayer-advanced.png)

And there you go!

![Final card interface in uMap.](../../static/tutoriels/grist-umap-result.png)

