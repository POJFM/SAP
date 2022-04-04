# update, delete

```
DATA:

      gt_book TYPE STANDARD TABLE OF z18fai_book,
      gs_book TYPE z18fai_book.



*-----------------------------------*
* MAIN LOGIC

* 1. UPDATE záznamu v db tabulce
UPDATE z18fai_book
  SET title = 'title hodnota'
      author = 'author hodnota'
  WHERE isbn = 12.

IF sy-subrc = 0.
  WRITE: / 'update OK'.
ELSE.
  WRITE: / 'něco se pokazilo'.
ENDIF.

* 2. UPDATE pomocí struktury
" připravit jednotlivé hodnoty
gs_book-isbn = 14.
gs_book-title = 'title gs'.
gs_book-author = 'author gs'.
gs_book-genre = 'drama'.

" provést UPDATE
UPDATE z18fai_book FROM gs_book.

IF sy-subrc = 0.
  WRITE: / 'update gs OK'.
ELSE.
  WRITE: / 'gs - něco se pokazilo'.
ENDIF.

* 3. UPDATE Z INTERNÍ TABULKY (běkolik záznamů najednou
" deklarace interní tabulky gt_book + strukturu gs_book
" pokud bychom měli záznamy v interní tabulce -> vyklírovat
CLEAR gt_book.

" připravit záznamy
gs_book-isbn = 1.
gs_book-title = 'title gt1'.
gs_book-author = 'author gt1'.
gs_book-genre = 'drama'.
APPEND gs_book TO gt_book.    " vložení záznamu do intermí tabulky!!!

gs_book-isbn = 2.
gs_book-title = 'title gt2'.
gs_book-author = 'author gt2'.
gs_book-genre = 'drama'.
APPEND gs_book TO gt_book.

gs_book-isbn = 3.
gs_book-title = 'title gt3'.
gs_book-author = 'author gt3'.
gs_book-genre = 'drama'.
APPEND gs_book TO gt_book.

" aktualizace záznamů
UPDATE z18fai_book FROM TABLE gt_book.

*====================================================
* DELETE
" 1. DELETE - preferovaný způsob - pomocí podmínky

DELETE FROM z18fai_book WHERE isbn = 251.
IF sy-subrc = 0.
  WRITE: / 'Záznam byl úspěšné smazán.'.
ENDIF.

" 2. DELETE ze struktury - NEDOPORUČUJE SE, NEVÍM PŘESNĚ, CO MAŽEME

" vyklírovat strukturu
CLEAR gs_book.
gs_book-isbn = 3.
DELETE z18fai_book FROM gs_book.
```
