####
Úvod
####

MapServer je mapový server. Slouží k publikování prostorových dat a k základním
analýzám nad prostorovými daty. MapServer podporuje celou řadu služeb `OGC
<http://opengeospatial.org>`_  a vlastní proprietární verzi aplikačního
rozhraní.

MapServer *nemá grafické uživatelské rozhraní* - ovládá se pomocí (většinou)
ručně vytvořeného textového souboru.


::

    # Příklad mapy se dvěma vrstvami. 
    # Původní zdroj: http://mapserver.org/tutorial/example1-2-map.html#example1-2-map
    
    # Řádky uvozené znamek '#' jsou považovány za komentář

    # MapFile začíná klíčovým slovem `MAP` a rozpadá se do hierarchických sekcí
    # Každá sekce začíná klíčovým slovem, např. `MAP, LAYER, CLASS, PROJECTION,
    # ...` a končí slovem `END`
    # Pro větší přehlednost se většinou používá odsazení podle úrovně zanoření.

    # Sekci `MAP` jsou některé základní definice
    MAP
        IMAGETYPE      PNG
        EXTENT         -97.238976 41.619778 -82.122902 49.385620
        SIZE           400 300
        SHAPEPATH      "/ms4w/apps/tutorial/data"
        IMAGECOLOR     255 255 255

        # definice vrstvy je uvozena klíčovým slovem `LAYER`

        LAYER 
            NAME         states_poly
            DATA         states_ugl
            STATUS       OFF
            TYPE         POLYGON

            # objekt `CLASS` definuje vzhled vrstvy, legendu pro jednotlivé
            # atributy, podmínky pro zařazení vektorového prvku do legendy
            CLASS
                NAME       "States"

                # a objekt `STYLE` definuje, jak se budou vybrané prvky
                # vykreslovat
                STYLE
                   COLOR    232 232 232
                END
            END
        END # Zde končí definice první vrstvy

        LAYER # začátek další vrstvy
            NAME         states_line
            DATA         states_ugl
            STATUS       OFF
            TYPE         LINE

            CLASS
                NAME       "State Boundary"
                STYLE
                    COLOR    32 32 32
                END
            END
        END # konec další vrstvy
    END # Konec definice MapFilu
