# Messages

- přidání message class

```
REPORT program MESSAGE-ID messageclass.
```

- selection screen pro vybrání message

```
SELECTION-SCREEN begin of block b01 with frame title text-001.
  PARAMETERS:
  p_msga RADIOBUTTON GROUP grp,
  p_msge RADIOBUTTON GROUP grp,
  p_msgi RADIOBUTTON GROUP grp,
  p_msgw RADIOBUTTON GROUP grp,
  p_msgs RADIOBUTTON GROUP grp,
  p_msgx RADIOBUTTON GROUP grp.
SELECTION-SCREEN end of block b01.
```

### A - TERMINATION: zobrazí se v dialogovém okně a program skončí

- zpráva TERMINATION s textem 000

```
IF  p_msga IS NOT INITIAL.
  MESSAGE A000.
ENDIF.
```

### E - ERROR: chybové dialogové okno nebo program skončí

```
IF  p_msge IS NOT INITIAL.
  MESSAGE E001.
ENDIF.
```

### I - INFORMATION: v dialogovém okně

- jakmile uživatel potvrdí zprávý, program pokračuje bezprostředně za příkazem MESSAGE

```
IF  p_msgi = 'X'.
  MESSAGE I002.
ENDIF
```

### W - WARNING: objeví se dialogové okno nebo program skončí

```
IF  p_msgw IS NOT INITIAL.
  MESSAGE W003.
ENDIF.
```

### S - SUCCESS: ve stavovém řádku, program pokračuje dál

```
IF  p_msgs IS NOT INITIAL.
  MESSAGE S004.
ENDIF.
```

### X - EXIT: krátká zpráva nebo výpis (obvykle při chybě programu)

```
IF  p_msgx IS NOT INITIAL.
  MESSAGE X005.
ENDIF.
```
