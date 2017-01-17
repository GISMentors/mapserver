.. only:: latex

   #####
   Obsah
   #####

.. only:: html

   `GISMentors <http://gismentors.cz>`_ | Školení `GRASS GIS
   <http://gismentors.cz/skoleni/grass-gis>`_ | `QGIS
   <http://gismentors.cz/skoleni/qgis>`_ | `PostGIS
   <http://gismentors.cz/skoleni/postgis>`_ | `GeoPython
   <http://gismentors.cz/skoleni/geopython>`_
   
   ****
   Úvod
   ****

.. only:: html

   .. figure:: images/mapserver-logo.png
      :width: 130px
      :align: left

**MapServer** je multiplatformní serverový mapový server určení pro
publikaci prostorových dat prostřednictvím webových služeb OGC a
prostřednictvím proprietárního rozhraní.

.. only:: latex

   .. figure:: images/mapserver-logo.png
      :scale-latex: 80

      Logo projektu MapServer

MapServer (http://mapserver.org) je jeden z nejdéle vyvíjených programů pro
tento účel, původně jako projekt NASA. V současnosti je MapServer vyvíjen
komunitou uživatelů a vývojářů. MapServer je považován za nejrychlejší software
svého druhu.

MapServer je možné konfigurovat pomocí textového konfiguračního souboru (tzv.
`mapfile`), ale je možné jeho knihovny používat i z různých programovacích
jazyků (Perl, Python, PHP, Java, ...).

.. important:: Školení je zaměřeno na verzi `MapServer 7.x`, 
               pokud není uvedeno jinak, tak všechny uvedené postupy
               jsou funkční i ve verzi MapServer 6.x. Případné rozdíly mezi
               těmito verzemi jsou vždy explicitně zdůrazněny. Dále
               předpokládáme nainstalovaný webový server (`Apache
               <http://httpd.apache.org>`_) a textový editor.
 
.. warning:: :red:`Pracovní značně neúplná verze materiálů, která je
             aktuálně ve vývoji!`

.. only:: html
             
   #####   
   Obsah
   #####

Základy práce s programem MapServer
-----------------------------------

.. toctree::
    :maxdepth: 1

    uvod
    zakladni_konfigurace
    raster/index
    vector/index

MapServer Suite
---------------

.. toctree::
    :maxdepth: 1

    suite/index
    suite/tinyows/index
    suite/mapcache/index

MapScript
---------

.. toctree::
    :maxdepth: 1

    mapscript/index

*******
Dodatky
*******

Související materiály
=====================

.. todo:: Zatím prázdné

O dokumentu
===========

Text dokumentu je licencován pod `Creative Commons Attribution-ShareAlike 4.0 International License <http://creativecommons.org/licenses/by-sa/4.0/>`_.

.. figure:: images/cc-by-sa.png 
   :width: 130px
   :scale-latex: 120
              
*Verze textu dokumentu:* |release| (sestaveno |today|)

Autoři
------

Za `GISMentors <http://www.gismentors.cz/>`_:

* `Jáchym Čepický <http://www.gismentors.cz/mentors/cepicky>`_ ``<jachym.cepicky opengeolabs.cz>``

Text dokumentu
--------------

.. only:: latex

   Online HTML verze textu školení je dostupná na adrese:

   * http://training.gismentors.eu/mapserver-zacatecnik/

Zdrojové texty školení jsou dostupné na adrese:

* https://github.com/GISMentors/mapserver-zacatecnik
