# insert selscreen

```
*&---------------------------------------------------------------------*
*& Report  Z18FAI_01_VZOR
*&
*&---------------------------------------------------------------------*
*& Description:
*&   vkládání záznamů pomocí SELECTION-SCREEN
*&   omezení výběru podle domény datového prvku
*&
*&---------------------------------------------------------------------*
*& Autor: fajkusovai
*& Datum: 15. 11. 2021
*&
*& Datum    Autor       Změny
*&
*&-------------------------------------------------------------------- *

REPORT z18fai_12_insert_selscreen.
TABLES z18fai_book.   " připojení db tabulky
*-----------------------------------*
* DECLARATIONS

" CONSTANTS:


" TYPES:


DATA:
       gs_book  type z18fai_book.


*-----------------------------------*
* MAIN LOGIC

SELECTION-SCREEN BEGIN OF BLOCK b01 WITH FRAME TITLE text-001.
PARAMETERS:
  p_isbn  TYPE z18fai_book-isbn,
  p_title  TYPE z18fai_book-title,
  p_author  TYPE z18fai_book-author,
  p_genre  TYPE z18fai_book-genre VALUE CHECK.  "VALUE CHECK - výběr pouze z domény

SELECTION-SCREEN END OF BLOCK b01.

" načtení hodnot parametrů do jednotlivých polí
gs_book-isbn = p_isbn.
gs_book-title = p_title.
gs_book-author = p_author.

" vložení řádku do db tabulky
insert z18fai_book from gs_book.

" kontrola vložení řádku
IF sy-subrc = 0.
  write: / 'Záznam byl vložen.', icon_green_light.
  ELSE.
    write: / 'Záznam nebyl vložen.', icon_red_light.
ENDIF.
```
