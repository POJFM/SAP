# arithmetic

```
*&---------------------------------------------------------------------*
*& Report  Z18FAI_01_VZOR
*&
*&---------------------------------------------------------------------*
*& Description:
*&   Krátké vysvětlení účelu programu, i pro neABAP uživatele
*&   technické informace - způsoby tiskových výstupů,...
*&
*&---------------------------------------------------------------------*
*& Autor: fajkusovai
*& Datum: 13. 1. 2021
*&
*& Datum    Autor       Změny
*&
*&-------------------------------------------------------------------- *

REPORT z18fai_04_arithmetic.

*-----------------------------------*
* DECLARATIONS


" CONSTANTS:

DATA:
      gv_integer    TYPE i,
      gv_float      TYPE f,
      gv_numeric    TYPE n,
      gv_packed     TYPE p,
      gv_packed_dec TYPE p DECIMALS 2,
      gv_vysledek   type i.


" TYPES:


*-----------------------------------*
* MAIN LOGIC

gv_integer = 3 / 4.
gv_float = 3 / 4.
gv_numeric = 3 / 4.
gv_packed = 3 / 4.
gv_packed_dec = 3 / 4.

WRITE: / 'Integer: 3/4 = ',gv_integer.
WRITE: / 'Float: 3/4 = ',gv_float.
WRITE: / 'Numeric: 3/4 = ',gv_numeric.
write: / 'Packed: 3/4 = ',gv_packed.
write: / 'Packed decimal 2 : 3/4 = ',gv_packed_dec.

" sčítání proměnných různých datových typů
gv_vysledek = gv_integer + gv_float.
write: / gv_integer, '+', gv_float, '=', gv_vysledek.

data gv_sydatum   type sy-datum.
gv_sydatum = sy-datum.    " systémová proměnná sy-datum pro zobrazení dnešního datumu
write: / 'Dnes je ', gv_sydatum.

data gv_date    type d.
gv_date = gv_sydatum.
write: / gv_date.

data
        gv_zamesic    type sy-datum.
gv_zamesic = gv_sydatum + 30.
write: / gv_zamesic.
```
