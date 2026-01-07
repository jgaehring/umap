!!! abstract "What We'll Learn"

    - Structure data to be able to geocode it
    - Geocode addresses and check the result
    - Import a data table into a uMap card
    - Inject the content of the table into the tooltips
    - Configure the sorting and filter of data

## Step-by-step procedures

The objective of this tutorial is to create a map in important
data in uMap. This can be useful in several situations:

-   view data you have found on an open portal
    data, for example <https://data.nantesmetropole.fr/>
-   place on a card the contacts (customers, suppliers,
    competitors...) that you manage in a spreadsheet

The challenge is to automatically place each element at its **position
geographical**, defined by a **longitude** and a **latitude** (on
also speaks of **GPS point**). For this, the data must be
**geocoded**, for example a table will contain two columns:
Latitude and longitude.

If the *open data* data is sometimes geocoded, it is usually not
not the case of your contact file that contains addresses. He
is in this case necessary to go through a step of **geocoding**, which
It consists of converting each address to latitude and longitude. We
let's deal with this case, step by step.

### 1. I create a board with addresses

To convert addresses to longitude and latitude we will
use a **geocoder**. It uses a database
of geocoded addresses, among which he searches for the address to
Geocoder. Here are some tips to follow to make the task easier
geocoder and obtain good results:

-   divide each address into **several columns** : address, code
    Post and city
-   carry in the address column the **talled of the track preceded by the
    number**, for example `14 rue de la Paix`, or the name of the place-said
-   place any other address element (mailbox, floor...) in
    another field

Here are some well-structured addresses, from
file [Seats of inter-municipal school transport unions in
Loire-Atlantique](https://data.nantesmetropole.fr/explore/dataset/23440034_031-001_sits_shp/export/)
:

| NOM                     | ADRESSE                | COMPL_ADR                    | CP     | VILLE                     |
| ------------------------| -----------------------| -----------------------------| -------| --------------------------|
| C. C. LOIRE et SILLON   | 2 bd de la Loire       |                              | 44260  | SAVENAY                   |
| C. C. COEUR d’ESTUAIRE  | 1 Cours d’Armor        | Route de Savenay             | 44360  | SAINT ETIENNE DE MONTLUC  |
| RESEAU CAP ATLANTIC’    | 4 rue Alphonse Daudet  | Zone Tertiaire de Kerbiniou  | 44350  | GUERANDE                  |
| SITS SUD LOIRE LAC      | ZI de la Seiglerie     |                              | 44270  | MACHECOUL                 |

The use of uppercase or lowercase letters does not usually have
of incidence. The table may of course contain other columns, such as
here the columns NOM and COMPL_ADR.

!!! note

    For the rest of the operations, it is important that the
    spreadsheet complies with the following rules:

    -   the first row of the spreadsheet must contain the column names, the
        other lines contain the data and nothing else
    -   column names must not contain space or accent or
        other special character
    -   the column names must all be different
    -   the cells must not contain a "back carriage" or "jump of
        line"
    -   the cells must not be fused

    In other words, the spreadsheet must represent a **database**.

### 2. I convert the addresses into geographical coordinates

Several **geocoders** are available on the internet. The quality of
geocoding may differ depending on several factors:

-   your address is incomplete or contains an error, for example a
    Bad postal code
-   the address database used contains incorrect addresses or is not
    not up to date
-   the algorithm responsible for comparing your address to those of the database of
    data made of bad assumptions

No geocoder is perfect. It is therefore important to **check the
quality of geocoding**, or even to compare and combine the result of
several geocoders. Most geocoders produce, in
complement to each latitude and longitude, a score to evaluate
the quality of the result.

In France the site <https://adresse.data.gouv.fr> gives access to the Base
National Address (BAN). It provides several tools, including the [geocoder
CSV](https://adresse.data.gouv.fr/csv) which allows to geocode a list
addresses very quickly with good results.

[DoGeocodeur](https://dogeo.fr/_apps/DoGeocodeur/) is a site
Particularly well thought out: he knows how to use several geocoders
(Google, IGN, BAN...) and combine their result, display the result
on a map, and allows you to manually position an address.
It also uses CSV files.

!!! note
    CSV means a text file containing the data of a
    array, whose values (the content of each cell) are separated
    by commas (CSV means *comma-separated values*) ... or by a
    Another character: the important thing is that this **separator** is not
    used within a value. The semicolon is often used
    as a separator to create a CSV file.

To geocode the addresses of a table, the steps to follow are:

1.  export the table to a file in CSV format, choosing the
    separator (advisor: semicolon) and character set
    (encoding) **UTF-8**. Include column headers if option
    You are offered. Here is for example the CSV export panel of
    LibreOffice Calc :
    ![export_csv_libreoffice_calc.png](../../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/export_csv_libreoffice_calc.png)
2.  import the CSV file into the geocoding site of your choice,
    This usually asks you to select the names of
    columns corresponding to the address, the postal code and the municipality
3.  check the result of the geocoding, adjust it and complete it at
    Need
4.  export the result, which will also be in CSV format

!!! note
    To export a CSV file to UTF-8 with Microsoft
    Excel, the **Web Options** menu in the **Save window under**
    allows, in the **Encoding** tab, to select **Unicode (UTF-8)**.
    Unfortunately this **does not work for MS Excel 2016 or Office
    365/Excel**, this is a [bug
    known](https://answers.microsoft.com/en-us/msoffice/forum/all/office-365excel-generates-incorrect-csv-utf-8/56516c38-78d8-40f5-90b3-f5d9db3d6d10).

    To get around this bug, one possibility is to use the editor
    [Notepad++](https://notepad-plus-plus.org/) that you need to install. Ne
    not change the encoding when exporting CSV, and then open the file in
    Notepad++, convert to UTF-8 in the **Encoding** menu, finally
    Save the file.

### 3. I import the geocoded array in a layer

Click on
**Import data** to display the panel of the same name, and then
Select the previously geocoded file.

<shot-scraper
    data-output="static/tutoriels/upload-data.png"
    data-url="https://umap.openstreetmap.fr/fr/map/new/"
    data-alt="Data import button."
    data-width="46"
    data-height="47"
    data-selector=".leaflet-toolbar-icon.upload-data"
    data-padding="5"
    >Data import button.</shot-scraper>


![importer_des_donnees.png](../../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/importer_des_donnees.png)

Verify that uMap has recognized **CSV** for the data format, and
choose to import them into a **new layer**.

Finally click on **Import** : the data is loaded and then
displayed on the map. The lines have no geographical position
are ignored, a message is then displayed.

!!! note

    uMap uses the first line of the CSV file to
    identify column names, especially **latitude** and
    **longitude** which are used to position the points (**lat** and
    **lon** are also included). Check the presence of these names of
    columns if the operation fails. Also be careful of what the
    coordinates are expressed in **decimal degrees**, with one point for
    Delineate the decimals. Example: 48.40 is correct but 48.40 and 48°24’
    are not valid for uMap.

Note that you can directly paste the data into the panel
of import. However, it is interesting to go through a file that you
can keep on your post.

Finally you can re-import the data, for example after you have it
Updated. Then select the same layer and check the box
**Replace the content of the layer**.

### 4. I insert the contents of the board into the tooltips

![infobulle_nom_du_calque.png](../../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/infobulle_nom_du_calque.png)

Now click on an imported marker in the previous step:
the tooltip displays the name of the layer (in this case the name of the file
imported if you have not renamed it) instead of the name present in the
Data table.

There are many possibilities to remedy this.

#### Change the field used

![cle_du_libelle.png](../../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/cle_du_libelle.png)

Edit the layer and
Change, in the Advanced Properties tab, the **Key for label**.
Enter the column name of the imported file. Every tooltip
now display the contents of this column.

![infobulle_nom_correct.png](../../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/infobulle_nom_correct.png)

!!! note
    Respect the breakage, that is to say the capitals and
    tiny. The column name must not contain any special character
    : accents, space, punctuation...

#### Show a table

![popup_tableau.png](../../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/popup_tableau.png)

The content of the painting can
be displayed in the tooltips, in the form of a table with two
columns : the title and the corresponding value.

In the **Interaction Options** tab of the layer, change the **Style of
the popup** in **Table**. Here is an example of a result:

![infobulle_tableau.png](../../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/infobulle_tableau.png)

![modifier_tableau.png](../../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/modifier_tableau.png)

Note that you
can edit the content of the table by clicking **Edit in a
array** in the layer selector. You can then delete or
Rename columns, or even modify the cells of the table.

#### Define the template of the tooltips

![gabarit_popup.png](../../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/gabarit_popup.png)

The above picture is not
not particularly nice with its capital labels.

In the tutorial [5-multimedia-tooltips.md) we saw
How to format the content of a tooltip. We can use the
same syntax to define the content of **all the tooltips of a
layer**, by integrating the content of the cells of the table.

In the **Interaction Options** tab of the layer, edit the **Gabarit
content of the popup**. Define the format of popups (titles,
bold character, etc.) as seen above. To *inject* the content
from a cell in the tooltip, simply add the column name
placed between braces, for example **{NOM}**.

![infobulle_avec_gabarit.png](../../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/infobulle_avec_gabarit.png)

You can use all the fields in the table in the template. Here is to
right an example of a template and the result for a tooltip.

**This approach is very powerful.** You can use it for
injecting, for each row of the table, a link to a website
(and why not the associated text), an image or an iframe. It's enough
to integrate the column name and its embraces, to the syntax
formatting the text, for example `[[{LIEN_SITE}|{TEXTE_LIEN}]]` or
yet `{{{URL_IMAGE}}}`.

### 5. I configure the sorting and filters

![config_filtres.png](../../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/config_filtres.png)

We saw in the tutorial
[I consult a map uMap](1-browsing-a-map.md) that he
is possible to see all the data of the card in the form
of a list. This list can also be filtered by the user, from
of a word for example.

<shot-scraper
    data-output="static/tutoriels/map-settings.png"
    data-url="https://umap.openstreetmap.fr/fr/map/new/"
    data-alt="Button of the options of the map."
    data-width="46"
    data-height="47"
    data-selector=".leaflet-toolbar-icon.update-map-settings"
    data-padding="5"
    >Button of the options of the map.</shot-scraper>

To allow the
users to filter the data should be specified at uMap at
which field(s) the "filter word" should apply. This is done in
the **Default properties** tab of the **Card Properties**. You
can specify multiple field names (column names), filter
will apply to each field.

Note that you can also sort the list by selecting the **Key
of sort**, i.e. the name of the column used for sorting (sorting
ascending only). Finally you can set the default key to
the wording, which will be used if it is not defined for the
Calque.

!!! note
    Sorting and filter keys apply to the whole
    data, all layers combined. If your card consists of
    multiple layers, so it is advisable to use the same key name
    to designate the same type of information. For example, avoid using
    **City** for one layer and **Commune** for another, use instead
    **Commune** for both.

## Let's take stock

This tutorial is probably the most complex of the series. Enjoy
However, the possibilities offered by uMap to integrate data
external.

??? info "License"

    Work initiated by Antoine Riche on [Carto’Cité](https://wiki.cartocite.fr/doku.php?id=umap:10_-_j_integre_des_donnees_distantes) under license [CC-BY-SA 4](https://creativecommons.org/licenses/by-sa/4.0/deed.en).
