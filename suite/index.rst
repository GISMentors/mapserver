###############
MapServer Suite
###############

MapServer Suite (http://mapserver.org/products.html) je soubor projektů
postavený okolo knihoven původně vyvíjených pro MapServer. Jedná se zejména o

MapServer
    Vlastní program MapServer - zejména pro poublikaci rastrových a vektorových
    dat. MapServer je napsán v programovacím jazyce C a je tedy nejrychlším
    programem svého druhu (ve své kategorii). O MapServeru je celý tento
    dokument.
MapCache
    Pro ještě rychlejší produkci dat je zde projekt MapCache, sloužící k tvorbě
    a udržování dlaždicových cachí. V nových verzích podporuje i vektorové
    formáty.
TinyOWS
    Na rozdíl od MapServeru, který podporuje v základu pouze publikační část
    standardu OGC Web Feature Service (`WFS
    <http://opengeospatial.org/standards/wfs>`_), přidává TinyOWS podporu pro
    transakční WFS-T. Tímto způsobem lze editovat vektorová data uložená na
    serveru v databázi `PostgreSQL/PostGIS <http://postgis.org>_`.
