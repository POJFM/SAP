# datetime

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

REPORT z18fai_05_date_time.

*-----------------------------------*
* DECLARATIONS

" CONSTANTS:

DATA:
      gv_date     type d,
      gv_date1    type d,
      gv_sydatum  type sy-datum,
      gv_days      type i,
      gv_time_test     type t value '190000',
      gv_time     type sy-uzeit,
      gv_min      type i.

" TYPES:


*-----------------------------------*
* MAIN LOGIC

gv_sydatum = sy-datum.
write: / gv_sydatum.

" přepsat na první den stávajícího měsíce
gv_date = gv_sydatum.
write: / gv_date.   " zobrazí se ve tvaru DDMMYYYY, ale vkládám ve tvaru YYYYMMDD
gv_date+6(2) = 01.
write: / gv_date.
gv_sydatum = gv_date.
write: / gv_sydatum.

gv_date1 = sy-datum.
write: / gv_date1.
gv_date = '20220314'.
write: / 'gv_date:',gv_date.
gv_days = gv_date1 - gv_date.
write: / 'Počet dní do jarních prázdnin: ',gv_days.

gv_time = sy-uzeit.
gv_min = gv_time_test - gv_time.
gv_min = gv_min / 3600.
write: / gv_min.
```
