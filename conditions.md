# podmínky

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
*& Datum: 10. 3. 2021
*&
*& Datum    Autor       Změny
*&
*&-------------------------------------------------------------------- *

REPORT z18fai_06_conditions.

*-----------------------------------*
* DECLARATIONS

CONSTANTS:
  BEGIN OF gc_cast_dne,                           " začátek deklarace konstanty se strukturou
    rano    type syuzeit  value '060000',         " jednotlivé fieldy struktury
    dopoledne     type syuzeit  value '090000',
    odpoledne     type syuzeit  value '120000',
    vecer         type syuzeit  value '180000',
  END OF gc_cast_dne.                             " konec deklarace konstanty se strukturou

DATA:
      gv_num1   TYPE i  VALUE 20,
      gv_num2   TYPE i  VALUE 30,
      gv_vysl   TYPE i,
      gv_month  TYPE i,
      gv_time   type t,                            " čas ve tvaru HHMMSS
      gv_sy_time   type sy-uzeit.   " JAKÝ DATOVÝ TYP POUŽIJEME?     " čas ve tvaru HH:MM:SS


" TYPES:


*-----------------------------------*
* MAIN LOGIC

" 2 ČÍSLA -> menší, větší, rovno
WRITE: / 'Porovnání 2 čísel'.
IF gv_num1 > gv_num2.
  WRITE: / gv_num1, 'je větší než', gv_num2.
ELSEIF gv_num1 = gv_num2.
  WRITE: / gv_num1, 'je rovno', gv_num2.
ELSE.
  WRITE: / gv_num1, 'je menší než', gv_num2.
ENDIF.

ULINE.
SKIP.

" CASE - přepiš měsíc do češtiny (měsíce 1-3)
WRITE: / 'Měsíc do češtiny'.
gv_month = 10.

CASE gv_month.
  WHEN 1.
    WRITE: / 'Leden'.
  WHEN 2.
    WRITE: / 'Únor'.
  WHEN 3.
    WRITE: / 'Březen'.
  WHEN OTHERS.
    WRITE: / 'Mimo rozsah'.
ENDCASE.

ULINE.
SKIP.

" pozdrav podle denní doby
" 6-9 dobré ráno, 9-12 dobré dopoledne, 12-18 dobré odpoledne, 18-21 dobrý večer
" nadeklarovat KONSTANTU, která je STRUKTUROU (obsahuje další fieldy)
" Write: /
```
