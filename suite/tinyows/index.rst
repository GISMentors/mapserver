*******
TinyOWS
*******

`TinyOWS <http://mapserver.org/tinyows/index.html>`_ je implementace standardu
`OGC WFS-T <http://opengeospatial.org/standards/wfs>`_ na straně serveru pomocí
knihoven projektu MapServer. Standard WFS umožňuje stahovat vektorové objekty ze
serveru, transakční WFS umožňuje jejich editaci.

Na WFS-T lze také pohlížet jako na aplikační rozhraní k prostorové databázi.
TinyOWS je programováno s podporou pro PostgreSQL/PostGIS. TinyOWS umí pracovat
se standardním konfiguračním souborem pro MapServer - `mapfile` - nebo s
vlastním formátem konfigurace (XML).

.. note:: TinyOWS v součastnosti (2017) podporuje pouze verzi 1.0 a 1.1
        standardu WFS. To je potřeba mít na paměti např. v souvislosti s
        implementací INSPIRE, který vyžaduje WFS 2.0.

.. toctree::
    :maxdepth: 1

    instalace
    konfigurace
    testovani
