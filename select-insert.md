# select, insert

```
*&---------------------------------------------------------------------*
*& Report  Z18FAI_01_VZOR
*&
*&---------------------------------------------------------------------*
*& Description:
*&   jak se zobrazují výsledky v různých datových typech proměnných
*&   technické informace - způsoby tiskových výstupů,...
*&
*&---------------------------------------------------------------------*
*& Autor: fajkusovai
*& Datum: 13. 1. 2021
*&
*& Datum    Autor       Změny
*&
*&-------------------------------------------------------------------- *

REPORT z18fai_13_select_insert.
TABLES z18fai_book.

*-----------------------------------*
* DECLARATIONS

" CONSTANTS:


TYPES:
ts_book   TYPE z18fai_book,
tt_book   TYPE STANDARD TABLE OF ts_book.


DATA:
      GV_POCITADLO TYPE I,
      gs_book TYPE ts_book,
      gt_book TYPE tt_book.

*-----------------------------------*
* MAIN LOGIC
GV_POCITADLO = 0.
SELECTION-SCREEN BEGIN OF BLOCK b01 WITH FRAME TITLE text-001.
  PARAMETERS:
  p_genre TYPE z18fai_book-genre.
  SELECTION-SCREEN end of block b01.


select * from z18fai_book.
  IF  P_GENRE = Z18FAI_BOOK-GENRE.
    gv_pocitadlo = gv_pocitadlo + 1.
  ENDIF.

  ENDSELECT.
  " write: z18fai_book-isbn.
  WRITE: gv_pocitadlo.

  "VÝPIS NEJVYŠŠÍHO ISBN
  select * from z18fai_book.
    ENDSELECT.
    write: / 'Nejvyšší isbn:', z18fai_book-isbn.

  " VLOŽENÍ 3 ZÁZNAMŮ POMOCÍ DO
  gs_book-isbn = z18fai_book-isbn.

  " vyčistit interní tabulku
  clear gt_book.
  DO 3 TIMES.
    gs_book-isbn = gs_book-isbn + 1.
    gs_book-title = 'TITLE ' && gs_book-isbn.
    gs_book-author = 'AUTHOR ' && gs_book-isbn.
    gs_book-genre = 'GENRE ' && gs_book-isbn.
    append gs_book to gt_book.
  ENDDO.

  insert z18fai_book from table gt_book.
```
