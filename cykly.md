# cykly

```
*&---------------------------------------------------------------------*
*& Report  Z18FAI_07_cykly
*&
*&---------------------------------------------------------------------*
*& Description:
*&   jak se zobrazují výsledky v různých datových typech proměnných
*&   technické informace - způsoby tiskových výstupů,...
*&
*&---------------------------------------------------------------------*
*& Autor: fajkusovai
*& Datum: 24. 3. 2021
*&
*& Datum    Autor       Změny
*&
*&-------------------------------------------------------------------- *

REPORT z18fai_07_cykly.

*-----------------------------------*
* DECLARATIONS
DATA:
      gv_opak TYPE i VALUE 5,
      gv_count TYPE i VALUE 1,
      gv_zbytek TYPE i.
" CONSTANTS:

* DO CYKLUS
" 5x vedle sebe vypsat slovo Ahoj
DO 5 TIMES.
  WRITE: 'Ahoj.'.
ENDDO.
SKIP. ULINE.

" cyklus s použitím proměnné
" 5x vypsat vedle sebe slovo "proměnná"
DO gv_opak TIMES.
  WRITE: 'Proměnná'.
ENDDO.
SKIP. ULINE.

" vypsat vedle sebe čísla 1-10
DO 15 TIMES.
  WRITE: gv_count.
  gv_count = gv_count + 1.
ENDDO.
SKIP. ULINE.

" jiná možnost
DO 10 TIMES.
  WRITE: sy-index.    " systémová proměnná, čítač
ENDDO.
ULINE.

"---------------------------------
" ENDLESS DO CYKLUS (NEKONEČNÝ CYKLUS)
" v cyklu musíme ošetřit, kdy se má skončit

WRITE: / 'Endless cycle'.
FORMAT COLOR = 0.

DO .
  " každý druhý řádek vybarvit jinou barvou
  IF sy-index MOD 2 = 0.
    FORMAT COLOR = 5.
  ELSE.
    FORMAT COLOR = 6.
  ENDIF.
  WRITE: / sy-index.

  " po 10 opakováních vystoupit z cyklu
  IF sy-index = 8.
    EXIT.
  ENDIF.

ENDDO.
ULINE.

"----------------------------------
" CONTINUE - možnost přeskočit část programu, pokud je splněna podmínka
"  vypsat čísla prvních 5 řádků, kromě 3
write: / 'CONTINUE'.
format COLOR = 0.
DO 5 TIMES.
  IF sy-index = 1.
     CONTINUE.
  ENDIF.
  WRITE: / SY-INDEX.

ENDDO.
uline.

"---------------------------------
"  CHECK - vykoná se pouze ta část programu, která splňuje podmínku
" vypište čísla 1-10 a vedle, zda je číslo liché nebo sudé
" vypsat jenom sudá čísla

DO 10 TIMES.
  check sy-index mod 2 = 0.
  write: / sy-index, 'sudé číslo'.

ENDDO.
SKIP. ULINE.

"--------------------------------
" cyklus WHILE
" každý druhý řádek pomocí WHILE, celkem 10 řádků

wRITE: / 'WHILE'.

WHILE sy-index <= 10 .
  write: / sy-index.

ENDWHILE.
```
