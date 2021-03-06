#### Time Format

OhMyDash follows time format specification from [Moment JS](https://momentjs.com/docs/#/displaying/format/). 

Common Time Format

|             | Token | Output |
| ------------| ------| --- |
|Month	|M	|1 2 ... 11 12|
|       |MM	|01 02 ... 11 12|
|Quarter|Q	 | 1 2 3 4|
|       |Qo	 |1st 2nd 3rd 4th|
|Day of Month	|D	|1 2 ... 30 31|
||DD|	01 02 ... 30 31|
|Day of Week	|d	|0 1 ... 5 6|
||dd|	Su Mo ... Fr Sa|
||ddd|	Sun Mon ... Fri Sat|
||dddd|	Sunday Monday ... Friday Saturday|
|Year	|YY	|70 71 ... 29 30|
||YYYY|	1970 1971 ... 2029 2030|
|AM/PM|	A|	AM PM|
||a|	am pm|
|Hour|	H|	0 1 ... 22 23|
|    |HH |	00 01 ... 22 23|
||h|	1 2 ... 11 12|
||hh|	01 02 ... 11 12|
|Minute|	m|	0 1 ... 58 59|
||mm	|00 01 ... 58 59|
|Second|	s|	0 1 ... 58 59|
||ss|	00 01 ... 58 59|
||Z|	-07:00 -06:00 ... +06:00 +07:00|
||ZZ|	-0700 -0600 ... +0600 +0700|
|Unix Timestamp|	X|	1360013296|
|Unix Millisecond Timestamp|	x|	1360013296123|
<br>


#### Number Format

OhMyDash follows number format specification from [Numeral JS](http://numeraljs.com/#format).

Common Date Format

|Number    |Format|	String|
|----------|------| ------|
|10000	|'0,0.0000'|	10,000.0000|
|10000.23|	'0,0'	|10,000|
|10000.23|	'+0,0'	|+10,000|
|-10000	|'0,0.0'	|-10,000.0|
|10000.1234|'0.000'	|10000.123|
|100.1234|'00000'	|00100|
|1000.1234|	'000000,0'|	001,000
|10	|'000.00'|	010.00|
10000.1234	'0[.]00000'|	10000.12340|
|-10000|	'(0,0.0000)'|	(10,000.0000)|
|-0.23 |'.00'|	-.23|
|-0.23 |	'(.00)'|	(.23)|
|0.23 |	'0.00000'|	0.23000|
|0.23 |	'0.0[0000]'	|0.23|
|1230974|	'0.0a'|	1.2m|
|1460 |	'0 a'|	1 k|
|-104000 |	'0a'|	-104k|
|1	|'0o'|	1st|
|100|	'0o'|	100th|
