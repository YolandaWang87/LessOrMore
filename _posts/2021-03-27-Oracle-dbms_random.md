---
layout: post
title:  Oracle dbms_random Methods
date:   2021-03-27 00:00:00 +0800
categories: Database
tag: SQL
---
Oracle 10g introduced a number of functions that should be used in place of the RANDOM function. In Oracle 11gR1, the RANDOM function was deprecated in favour of these other functions.
<hr>
### SEED
From 10g onward you don't need to explicitly call SEED. In Oracle 10g it is automatically seeded with the date. In later releases it is seeded using the date, user ID, and process ID.<br>
If you want to be "more" random, then use a seed that is more unique, like a timestamp.
```
DBMS_RANDOM.seed (val => TO_CHAR(SYSTIMESTAMP,'YYYYDDMMHH24MISSFFFF'));
```
### VALUE
When called without parameters it produce a number greater than or equal to 0 and less than 1, with 38 digit precision.<br>
If the parameters are used, the resulting number will be greater than or equal to the low value and *less* than the high value, with the precision restricted by the size of the high value.<br>
Use TRUNC or ROUND to alter the precision as required.
```
TRUNC(DBMS_RANDOM.value(1,11))
```
### STRING
The STRING function returns a string of random characters of the specified length. The OPT parameter determines the type of string produced
```
DBMS_RANDOM.string('x',10)
```
string('x',10)= BL69189JC0

### NORMAL
```angular2html
DBMS_RANDOM.normal
```

### DATES
we can add random numbers to an existing date to make it random.
```angular2html
TRUNC(SYSDATE + DBMS_RANDOM.value(0,366))
```


