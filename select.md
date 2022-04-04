# select

```
*&---------------------------------------------------------------------*
*& Report  Z18FAI_09_SELECT
*&
*&---------------------------------------------------------------------*
*& Description:
*&   úprava db tabulel - SELECT, INSERT, UPDATE, APPEND, DELETE
*&    - zápis u jednotlivých operací
*&
*&---------------------------------------------------------------------*
*& Autor: fajkusovai
*& Datum: 4. 10. 2021
*&
*& Datum    Autor       Změny
*&
*&--------
REPORT z18fai_09_select.

*-----------------------------------*
* DECLARATIONS

" CONSTANTS:

" DATA:


" TYPES:


*-----------------------------------*
* MAIN LOGIC
" JEDEN ŘÁDEK, VŠECHNY FIELDY

" DECLARATIONS
*DATA:
*      gs_z18fai_book  TYPE z18fai_book.       " gs... = global strukture, jeden řádek tabulky
*
*WRITE: 'JEDEN ŘÁDEK, VŠECHNY FIELDY.'.
*SELECT SINGLE *
*  FROM z18fai_book
*  INTO gs_z18fai_book.
*  " WHERE title = 'DÁŠENKA'.            u podmínek pozor na datové typy a velikost písmen
*
*WRITE: / gs_z18fai_book.

*"**********************************************************
" SELECT  - jeden řádek, vybrané fieldy
* DECLARATION
TYPES:
    BEGIN OF ts_book_spec,              " kostra - které fieldy z db tabulky
      " isbn    type z18fai_book-isbn,
      author  TYPE z18fai_book-author,  " TYPE - podle datového elementu z db tabulky!
      title   TYPE z18fai_book-title,
     END OF ts_book_spec.

data:
      gs_book_spec   type ts_book_spec.   " jeden řádek podle kostry

write: / 'JEDEN ŘÁDEK, VYBRANÉ FIELDY:'.
select single author title
  from z18fai_book
  into gs_book_spec.

write: / gs_book_spec.
skip.
*
*"*************************************************************
*" SELECT - všechny řádky, vybrané fieldy
*" pro více řádků potřebujeme interní tabulku (INTERNAL TABLE)
*
**types:
**  begin of ts_book_spec,
**    isbn  type z18fai_book-isbn,   " TYPE - podle datového elementu z db tabulky!
**    title type z18fai_book-title,
**   end of ts_book_spec.
**
**types:
**  " jakého typu je interní tabulka, my budeme používat pouze STANDARDNÍ TABULKY (ne - SORTED, HASHED)
**   tt_book_spec type STANDARD TABLE OF ts_book_spec.
**
**data:
**      gt_book_spec  type tt_book_spec,
**      gs_book_spec  type ts_book_spec.
**
**select isbn title
**  from z18fai_book
**  into table gt_book_spec
**  up to 5 rows.     " obdoba LIMIT v RDS
**
**" zápis do interní tabulky
**  LOOP AT gt_book_spec into gs_book_spec.
**    write: / gs_book_spec.                  " vypsání záznamů po řádcích
**
**  ENDLOOP.
*
**************************************************************
** SELECT - VŠECHNY ZÁZNAMY, VŠECHNY FIELDY
** pomocí interní tabulky
*
*TYPES:
*  ts_book   TYPE z18fai_book,    " kostra podle db tabulky
*  tt_book   TYPE STANDARD TABLE OF ts_book.
*
*DATA:
*  gt_book TYPE tt_book,
*  gs_book TYPE ts_book.
*
*SELECT *
*  FROM z18fai_book
*  INTO TABLE gt_book
*  UP TO 5 ROWS.
*
*LOOP AT gt_book INTO gs_book.
*  WRITE: / gs_book.
*
*ENDLOOP.
```
