# deklarace

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

REPORT Z18FAI_03_DEKLARACE.

*-----------------------------------*
* DECLARATIONS

" CONSTANTS:    deklarace konstant

DATA:       " deklarace proměnných
      gv_integer                  type i,
      gv_integer_value            type i value -152,
      gv_packed_number            type p,
      gv_packed_decimal           type p decimals 2,
      gv_packed_dec_value         type p DECIMALS 2 VALUE 5,
      gv_float                    TYPE f,
      gv_float_value              TYPE f value -400,
      gv_numeric                  type n,
      gv_numeric_length           type n length 6,
      gv_numeric_length_value     type n length 6 value 150,
      gv_char                     type c, " length 15 value 'ahoj všich',
      gv_string                   type String value 'ahoj',
      gv_date                     type d value '20210210',  " zadávat ve tvaru YYYYMMDD  -> vypisuje ve tvaru DDMMYYYY
      gv_date_sy                  type sy-datum value '20210210',      " !!! netiskne aktuálí datum
      gv_time                     type t value '133015',
      gv_time_sy                  type sy-uzeit value '133015'.

" TYPES:


*-----------------------------------*
* MAIN LOGIC
write: / 'Integer:', 30 gv_integer, '|'.
write: / 'Integer s hodnotou:', 30 gv_integer_value, '|'.
write: / 'Packed:', 30 gv_packed_number, '|'.
write: / 'Packed decimal:', 30 gv_packed_decimal, '|'.
write: / 'Packed decimal value:', 30 gv_packed_dec_value, '|'.
write: / 'Float:', 30 gv_float, '|'.
write: / 'Float value:', 30 gv_float_value, '|'.
write: / 'Numeric:', 30 gv_numeric, '|'.
write: / 'Numeric length:', 30 gv_numeric_length, '|'.
write: / 'Numeric length value:', 30 gv_numeric_length_value, '|'.
write: / 'Character:', 30 gv_char, '|'.
write: / 'String:', 30 gv_string, '|'.
write: / 'Datum:', 30 gv_date, '|'.
write: / 'Datum sy-datum:', 30 gv_date_sy, '|'.
write: / 'Time:', 30 gv_time, '|'.
write: / 'Time sy-uzeit:', 30 gv_time_sy, '|'.
```
