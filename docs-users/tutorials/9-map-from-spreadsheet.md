!!! abstract "What You'll Learn"

    - Structure data to be able to geocode it
    - Geocode addresses and check the output
    - Import a data table into uMap
    - Inject the content of the table into the tooltips
    - Configure the sorting and filter of data

## Step-by-step procedures

The objective of this tutorial is to create a map in important
data in uMap. This can be useful in several situations:

-   view data you have found on an open portal
    data, for example <https://data.nantesmetropole.fr/>
-   add contact info (customers, suppliers, competitors, etc.) to the map
    based on a spreadsheet you maintain

The challenge is to set the visual position automatically for each element
according to its **geographical location**, defined by a **longitude** and
a **latitude** (a.k.a, **GPS point**). For this, the data must be
**geocoded**, for example as a table consisting of two columns:
latitude and longitude.

Even though the open data source will likely be geocoded, it is usually not
the case that the addresses contained in your contact file will. In this case,
it is necessary to go through a step of **geocoding**, which consists of
converting each address to latitude and longitude. Let's deal
with this case, step by step.

### 1. Create a table of addresses

To convert addresses to longitude and latitude we will
use a **geocoder**. It uses a database
of geocoded addresses, from which it searches for the address to
geocode. Here are some tips to follow to make the task of geocoding
easier and obtain good results:

-   divide each address into **several columns**: address,
    postal code and city
-   in the address column, enter **number followed by the street name**, for
    example `14 Main Street`, or the name of the neighborhood
-   place any other address element (mailbox, floor, etc.) in
    another field

Here are some well-structured addresses, from the
file [NYC OpenData Queens Library Branches](https://data.cityofnewyork.us/api/v3/views/kh3d-xhq7/query.csv):

| NAME             | ADDRESS_1                      | ADDRESS_2         | CITY             | ZIP   |
| ---------------- | ------------------------------ | ----------------- | ---------------- | ----- |
| South Jamaica    | 108-41 Guy R. Brewer Boulevard |                   | Jamaica          | 11433 |
| Long Island City | 37-44 21 Street                |                   | Long Island City | 11101 |
| Elmhurst         | 86-01 Broadway                 |                   | Elmhurst         | 11373 |
| McGoldrick       | 155-06 Roosevelt Avenue        | off Northern Blvd | Flushing         | 11354 |
| Bellerose        | 250-06 Hillside Avenue         |                   | Bellerose        | 11426 |
| Far Rockaway     | 1637 Central Avenue            |                   | Far Rockaway     | 11691 |
| Windsor Park     | 79-50 Bell Boulevard           |                   | Bayside          | 11364 |
| Ozone Park       | 92-24 Rockaway Boulevard       |                   | Ozone Park       | 11417 |

The use of uppercase or lowercase letters does not usually matter.
The table may of course contain additional columns, as in this instance
the columns NAME and ADDRESS_2.

!!! note

    For the rest of the steps, it is important that the
    spreadsheet complies with the following rules:

    -   the first row of the spreadsheet must contain the column names or
        headers, the other lines contain the data and nothing else
    -   column headers must not contain any spaces, punctuation or
        other special characters
    -   the column headers must all be unique
    -   the cells must not contain a return or new line characters
    -   the cells must not contain any RETURN (↵) or new line characters
    -   the cells must not be merged

    In other words, the spreadsheet must represent a **tabular database**
    or simple CSV file.

### 2. Convert the addresses into geographical coordinates

Several **geocoders** are available on the internet. The quality of
geocoding may differ depending on several factors:

-   your address is incomplete or contains an error, for example an
    invalid postal code
-   the geocoder's address database contains incorrect addresses or is not
    not up to date
-   the algorithm responsible for comparing your address to those in the
    database makes some faulty assumptions

No geocoder is perfect. It is therefore important to **check the
quality of geocoding**, or even compare and combine the result of
several geocoders. Most geocoders produce, alongside
each latitude and longitude, a score to evaluate
the quality of the output.

In France the site <https://adresse.data.gouv.fr> gives access to the *Base
Adresse Nationale* (BAN). It provides several tools, including the [geocoder
CSV](https://adresse.data.gouv.fr/csv) which can geocode a list
addresses very quickly with good results.

[DoGeocodeur](https://dogeo.fr/_apps/DoGeocodeur/) is a
particularly well-made site. It can choose between several geocoders
(Google, IGN, BAN...), combine their result and display the result
on a map, then allows you to manually reposition any address.
It also uses CSV files.

!!! note
    CSV, or *comma-separated values*, refers to a text file containing
    rows of tabular, whose values (the content of each cell) are separated
    by commas or by another character.
    The important thing is that this **separator** is not
    contained in the value. A semicolon is often used
    as a separator to create a CSV file, or the TAB (↹) character (a.k.a. TSV).

To geocode the addresses of a table, follow these steps:

1.  Export the table to a file in CSV format, choosing the
    separator (recommended: semicolon) and character set
    (encoding) **UTF-8**. Include column headers if
    given the option. For example, here is the CSV export panel for
    LibreOffice Calc:

    ![export_csv_libreoffice_calc.png](../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/export_csv_libreoffice_calc.png)

2.  Import the CSV file into the geocoding site of your choice,
    this usually asks you to select the names of
    columns corresponding to the address, the postal code and the municipality
3.  Check the result of the geocoding, adjust it and update it as
    needed
4.  Export the result, which will also be in CSV format

!!! note
    To export a CSV file to UTF-8 with Microsoft
    Excel, the **Web Options** menu in the **Save as** window 
    allows you to select **Unicode (UTF-8)** under the **Encoding** tab.
    Unfortunately this **does not work for MS Excel 2016 or Office
    365/Excel**, this is a [bug
    known](https://answers.microsoft.com/en-us/msoffice/forum/all/office-365excel-generates-incorrect-csv-utf-8/56516c38-78d8-40f5-90b3-f5d9db3d6d10).

    To get around this bug, one possibility is to use the editor
    [Notepad++](https://notepad-plus-plus.org/) that you need to install. Do
    not change the encoding when exporting CSV, then open the file in
    Notepad++, convert to UTF-8 in the **Encoding** menu, and finally
    save the file.

### 3. Import the geocoded table into a layer

Click on
**Import data** to display the panel of the same name, then
select the previously geocoded file.

<shot-scraper
    data-output="static/tutoriels/upload-data.png"
    data-url="https://umap.openstreetmap.fr/fr/map/new/"
    data-alt="Data import button."
    data-width="46"
    data-height="47"
    data-selector=".leaflet-toolbar-icon.upload-data"
    data-padding="5"
    >Data import button.</shot-scraper>


![importer_des_donnees.png](../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/importer_des_donnees.png)

Verify that uMap has recognized **CSV** for the data format, and
choose to import it into a **new layer**.

Finally, click on **Import**. The data will be loaded then
displayed on the map. Any rows without a geographical location
are ignored and a message is displayed.

!!! note

    uMap uses the first line of the CSV file to
    identify column names or headers, especially **latitude** and
    **longitude** which are used to position the points (**lat** and
    **lon** are also allowed). Check that these columns headers exist
    if the operation fails. Also make sure that
    coordinates are expressed in **decimal degrees**, with one PERIOD character
    separating the decimals. Example: 48.40 is correct but 48,40 and 48°24’
    are not valid for uMap.

Note that you can directly paste the data into the
import panel. However, it is worthwhile to use a file that you 
can keep on your device.

Finally you can re-import the data, for example after you have
updated it. Then select the same layer and check the box
**Replace the content of the layer**.

### 4. Insert the contents of the table into the tooltips

![infobulle_nom_du_calque.png](../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/infobulle_nom_du_calque.png)

Now click on an imported marker from the previous step:
the tooltip will display the name of the layer (in this case the name of the
imported file if you have not renamed it) rather than the name set in the
data table.

There are many possible ways to fix this.

#### Change the field used

![cle_du_libelle.png](../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/cle_du_libelle.png)

Edit the layer and
under the Advanced Properties tab, change the **Key for label**.
Enter a column header used in the imported file. Every tooltip
now displays the contents of this column.

![infobulle_nom_correct.png](../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/infobulle_nom_correct.png)

!!! note
    Respect case sensitivity, that is to say the uppercase and
    lowercase. The column header must not contain any spaces,
    punctuation, or other special characters.

#### Show a table

![popup_tableau.png](../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/popup_tableau.png)

The content of the row can
be displayed in the tooltips, in the form of a table with two
columns : the header and the corresponding value.

In the **Interaction Options** tab of the layer, change the **Style of
the popup** in **Table**. Here is an example of a result:

![infobulle_tableau.png](../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/infobulle_tableau.png)

![modifier_tableau.png](../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/modifier_tableau.png)

Note that you
can edit the content of the table by clicking **Edit in a
array** in the layer selector. You can then delete or
Rename columns, or even modify the cells of the table.

#### Define the template of the tooltips

The above picture is not
not particularly nice with its capital labels.

In an [earlier tutorial](5-multimedia-tooltips.md) we saw
how to format the content of a tooltip. We can use the
same syntax to define the content of **all the tooltips of a
layer**, by integrating the content of the cells of the table.

In the **Interaction Options** tab of the layer, edit the **Popup
Content Template**.
Format the layout of the popups (titles,
bold character, etc.) as seen below. To *inject* the content
from a cell in the tooltip, simply add the column header
set between braces, for example **{NOM}**.
You can use all the fields in the table in the template.

![gabarit_popup.png](../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/gabarit_popup.png)

This is the result of the template:

![infobulle_avec_gabarit.png](../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/infobulle_avec_gabarit.png)

**This approach is very powerful.** You can use it for
injecting, for each row of the table, you could inject a link to a website
(and perhaps any associated link text), an image or an iframe. Simply
integrate the column headers and their curly braces into the formatting syntax,
for example, `[[{SITE_LINK}|{LINK_TEXT}]]` or
again `{{{IMAGE_URL}}}`.

### 5. Configure sorting and filters

![config_filtres.png](../static/tutoriels/9-je-cree-une-carte-a-partir-dun-tableur/config_filtres.png)

We saw in the [Browsing a uMap](1-browsing-a-map.md) tutorial that
it's possible to see all the map data in the form
of a list. This list can also be filtered by the user, for example,
based on a keyword.

<shot-scraper
    data-output="static/tutoriels/map-settings.png"
    data-url="https://umap.openstreetmap.fr/fr/map/new/"
    data-alt="Button of the options of the map."
    data-width="46"
    data-height="47"
    data-selector=".leaflet-toolbar-icon.update-map-settings"
    data-padding="5"
    >Button of the options of the map.</shot-scraper>

To allow
users to filter the data, you need to specify to uMap
which field(s) should have the "filter word" applied to them. This is done in
the **Default properties** tab of the **Card Properties**. You
can specify multiple field names (column headers); the filter
will apply to each field.

Note that you can also sort the list by selecting the
**Sort Key**, that is, the column header used for sorting
(ascending only). Finally you can set the default key for
the label, which will be used if it is not defined for the
layer.

!!! note
    Sorting and filter keys apply to the entire dataset,
    all layers combined. If your map consists of
    multiple layers, it is recommended to use the same key name
    to designate the same type of information. For example, avoid using
    **City** for one layer and **Town** for another; instead, use
    **City** for both.

## Let's take stock

This tutorial is probably the most complex of the series, but
you can appreciate now the opportunities uMap offers to integrate
external data.

??? info "License"

    Work initiated by Antoine Riche on [Carto’Cité](https://wiki.cartocite.fr/doku.php?id=umap:10_-_j_integre_des_donnees_distantes) under license [CC-BY-SA 4](https://creativecommons.org/licenses/by-sa/4.0/deed.en).
