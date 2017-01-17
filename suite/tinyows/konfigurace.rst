===========
Konfigurace
===========
Stejně jako MapServer se TinyOWS konfiguruje pomocí textového konfiguračního
souboru. Na výběr je buď přidání parametrů do už existujícího souboru `mapfile`
a nebo vytvoření nového konfiguračního souboru ve formátu XML.

Konfigurace pomocí souboru XML
------------------------------
Konfigura prostřednictvím zvláštního souboru je preferovaný způsob práce s
TinyOWS. Výchozí konfigurační soubor je očekávaný v `/etc/tinyows.xml`. Tuto hodnotu
lze přepsat proměnnou prostředí `TINYOWS_CONFIG_FILE`::


        <tinyows online_resource="http://127.0.0.1/cgi-bin/tinyows"
                 schema_dir="/usr/local/tinyows/schema/">

         <pg host="127.0.0.1" user="postgres" password="postgres" dbname="tinyows_demo" port="5432"/>

         <metadata name="TinyOWS Server"
                   title="TinyOWS Server - Demo Service" />

         <layer retrievable="1"
                writable="1"
                ns_prefix="tows"
                ns_uri="http://www.tinyows.org/"
                name="world"
                title="World Administrative Boundaries" />

         <layer retrievable="1"
                writable="1"
                ns_prefix="tows"
                ns_uri="http://www.tinyows.org/"
                name="france"
                title="French Administrative Sub Boundaries (IGN - GeoFLA Departements)" />

        </tinyows>

Element `tinyows`
^^^^^^^^^^^^^^^^^

`online_resource`
    URL vedoucí na webovou službu, povinný parametr
`schema_dir`
    Adresář s uloženými XML schematy - výchozí je `/usr/local/tinyows/schema/`,
    ale např. při instalaci z balíku je to `/usr/share/tinyows/schema/`. Povinný
    parametr.

Další parametry jsou nepovinné

`log`
    cesta k souboru pro logování
`log_level`
    Binární součin: 1:ERROR, 2: EVENT, 4: HTTP QUERY, 8: SQL, 15: vše
`degree_precision`, `meter_precision`
    Počet desetinných míst souřadnic
`display_bbox`
    Bounding box není ve standardu WFS povinný a jeho výpočet je relativně
    náročný - touto volbou ho lze deaktivovat a snížit tak zátěž na serveru.
`estimated_extent`
    Použít méně přesný, ale rychlejší odhadovaný extent
`check_schema`
    Testovat vstupní data pro schématu XML
`encoding`
    Výchozí hodnota je `utf-8`
`wfs_default_version`
    TinyOWS podporuje WFS `1.0.0` nebo `1.1.0`

Element `limits`
^^^^^^^^^^^^^^^^

Tímto elementem lze omezit počet zpracovávaných prvků:

`features`  
    maximální počet vektorových objektů, které jsou odeslány zpět klientovi
`geobbox`
    maximální prostorový rozsah pro prvky ve formě `vychod,zapad,sever,jih`
    
Element `pg`
^^^^^^^^^^^^

Tímto elementem se definuje napojení na databázi PostgreSQL. Parametry jsou
nepovinné a odpovídají standardním parametrům pro připojení k databázi.

* `host`
* `user`
* `password`
* `dbname`
* `port`
* `encoding`

Element `metadata`
^^^^^^^^^^^^^^^^^^

Tento element obsahuje informace o službě. 

`name`
    Povinný parametr - identifikátor služby
`title`
    Povinný parametr - lidsky čitelný identifikátor služby
`keywords`
    klíčová slova oddělená čárkou
`fees`
    ...
`access_constraints`
    ...

Element `abstract`
^^^^^^^^^^^^^^^^^^

Obsahuje delší popis služby

Element `contact`
^^^^^^^^^^^^^^^^^

Detailní popis kontaktu

Povinné údaje
"""""""""""""
`name`
    Název kontaktu
`site`
    URL kontaktu
`email`
    elektronická pošta

Nepovinné údaje
"""""""""""""""
* `ndividual_name`
* `position`
* `phone`
* `fax`
* `online_resource`
* `address`
* `postcode`
* `city`
* `administrative_area`
* `country`
* `hours_of_service`
* `contact_instructions`

Element `layer`
^^^^^^^^^^^^^^^
Vlastní definice vrstev.

Povinné parametry
"""""""""""""""""

`ns_prefix`
    Zkratka jmenného prostoru pro vrstvu 
`ns_uri`
    URI pro zadaný jmenný prostor
`name`
    Identifikátor vrstvy

Nepovinné parametry
"""""""""""""""""""

* `title`
* `retrievable`
* `writable`
* `schema`
* `table`
* `abstract`
* `keywords`
* `srid`
* `geobbox`
* `include_items`
* `exclude_items`
* `pkey`


Konfigurace pomocí souboru `mapfile`
------------------------------------


Pro použití `mapfile` je potřeba nastavit proměnnou prostředí `TINYOWS_MAPFILE`.

Konfigurační hodnoty pro TinyOWS se ukládají do sekce `METADATA` a používají
prefix `tinyows_`.

Podporovány jsou pouze vrstvy s připojením do PostgreSQL/PostGIS. Většina
konfiguračních hodnot pro jednoduché WFS publikované prostřednictvím MapServeru
jsou ignorovány. ::

        MAP
            NAME "TinyOWS"

            WEB
                 METADATA
                            "tinyows_schema_dir" "/usr/local/share/tinyows/schema/"
                            "tinyows_onlineresource" "127.0.0.1/cgi-bin/tinyows.fcgi"
                            "wfs_title" "TinyOWS service provided by a MapFile"
                            "wfs_contact" "foo@bar.net"
                 END
            END

            LAYER
                    NAME 'France'
                    CONNECTIONTYPE postgis
                    CONNECTION "host=127.0.0.1 user=postgres password=postgres dbname=tinyows_demo port=5432"
                    METADATA
                            'wfs_title' 'France'
                            'wfs_namespace_prefix' 'tows'
                            'wfs_namespace_uri' 'http://www.tinyows.org/'
                            'wfs_srs' 'EPSG:27582'
                            'tinyows_table'  'france'
                            'tinyows_writable' '1'
                            'tinyows_retrievable' '1'
                    END
                    DUMP TRUE
            END
        END

Jednotlivé konfigurační hodnoty a jejich převod z XML do `mapfile` je popsán v
`tabulce <http://www.mapserver.org/tinyows/mapfileconfig.html#mapfile-path-of-each-tinyows-config-element>`_.
