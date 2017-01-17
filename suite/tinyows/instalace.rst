Instalace
=========

Ze zdrojových kódů
------------------

Instalace ze zdrojových kódu probíhá klasickým stažením ze serveru GITHub a
trojkombinací příkazů `./configure; make; make install`::

        $ git clone git://github.com/mapserver/tinyows.git
        $ cd tinyows
        $ autoconf
        $ ./configure
        $ make
        $ sudo make install
        $ sudo make install-demo

Z balíčku
---------
Minimálně pro distribuci `Ubuntu <http://ubuntu.com>`_ jsou dostupné balíky a
instalovat lze klasicky příkazem `apt-get`::

    $ sudo apt-get install tinyows

Microsoft Windows
-----------------
TinyOWS bohužel není jednoduchou formou na platformě MS Windows dostupné.
Existuje sice `popis <http://gis-lab.info/qa/tinyows-compile-vce-eng.html>`_
postupu, ale vyžaduje značně pokročilé znalosti.
