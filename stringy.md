# Stringy

### CONDENSE

- odstraní zbytečné mezery, ponechá vždy jen jednu mezeru

```
CONDENSE retezec.
```

- `NO-GAPS` úplně odstraní mezery:

```
CONDENSE retezec NO-GAPS.
```

### STRLEN

- délka řetězce (no shit Sherlock)
- pozor na mezery v závorce, cuz abap je retarded

```
STRLEN( retezec )
```

### SHIFT

- posun textových řetězců

mazání znaků zleva:

```
SHIFT gv_telefon LEFT DELETING LEADING '0'.
# 0000123456 ► 123456
```

mazání znaků zprava:

```
SHIFT gv_telefon BY 3 PLACES RIGHT.
0000123456 ► 0000123
```

### SPLIT

- rozdělení řetězce na základě oddělovacího znaku

```
SPLIT adresa
	AT ' '
	INTO ulice
			 cislo_popisne
			 mesto.
```

### změna znaku nebo skupiny znaků v řetězci

- jméno Jitka Nováková změníme na Dana Nováková

```
gv_jmeno = 'Jitka Nováková'.
gv_jmeno(5) = 'Lenka'.

gv_jmeno(5) = 'Jana'.
write: / 'Záměna jmen 2: ', gv_jmeno. 
# ale přibude mezera mezi slovy
CONDENSE gv_jmeno. # odstranit nadbytečné mezery
```

### CONCATENATE

- spojování řetězců

```
CONCATENATE retezec1 retezec2
	into spojeny_retezec
	SEPARATED BY ' '.
```

### velká a malá písmena

```
to_upper( retezec ).
to_lower( retezec ).
```

### Obsolete (zastaralé)

- `MOVE`
- `REPLACE`
- SAP a ABAP
