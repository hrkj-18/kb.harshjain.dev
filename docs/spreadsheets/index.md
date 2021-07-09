# Spreadsheets Course

## Basics
=121+21<br>
142

## Mathematics
\+  <br>
\- <br>
\* <br>
/ <br>
^

## Percentages
= 2 * 21%<br>

## Comparison Operators
<, >: smaller/greater than<br>
<=, >=: smaller/greater than or equal to<br>
=, <>: equal/not equal to

## Text
'23 = 23 in text

## Formatting
Format > Number > More formats

## Absolute references
$A$12

## What IS*() the data type?
=ISTEXT() <br>
=ISNUMBER() <br> 
=ISDATE() <br>
=ISLOGICAL() <br>
=ISURL() <br>
=ISFORMULA() <br>
=ISBLANK() <br>

## Coversion
=N() <br>
=TO_PERCENT() <br>
 <br>
=CONVERT(A2, "sec", "min")

## Logarthmic Transformations
=LOG10() <br>
=LN() <br>

## Exponential transformations
=EXP() <br>
=POW(2,CELL) <br>

## Square and square root transformations
=SQRT() <br>

## Min and Max
=MIN(Range) <br>
=MAX(Range) <br>

## Mean and Median
=SUM(Range) <br>
=AVERAGE(Range) <br>
=MEDIAN(Range) <br>

## Rank
=RANK(value, Range, [is_ascending]) <br>

## Right and Left
=RIGHT(Beauty and the Beast (2017),4) = 017) <br>
=LEFT(Star Wars: The Last Jedi,3) = Sta <br>

## Length and Search
=LEN() <br>
=SEARCH(" ", cell) <br>

## Concatenate
=CONCATENATE(value1, value2, value3, ....) <br>

## Weekday
=WEEKDAY(date, [type]): evaluates to the day of the week of a date. type is 1, 2 or 3. <br>
type = 1: Sunday is day 1 and Saturday is day 7 (default) <br>
type = 2: Monday is day 1 and Sunday is day 7 <br>
type = 3: Monday is day 0 and Sunday is day 6 <br>

=DATEDIF(start_date, end_date, unit)
"Y": the number of years between two dates <br>
"M": the number of months between two dates <br>
"D": the number of days between two dates <br>

## Rounding numbers
ROUND(x, n) rounds x to the nearest n decimal places. <br>
CEILING(x, y) rounds x up to the nearest multiple of y. <br>
FLOOR(x, y) rounds x down to the nearest multiple of y. <br>
=ROUND(0.746, 1) = 0.7 <br>
=ROUND(325, -2) = 300 <br>

=FLOOR(1.0985) = 1 <br>
=FLOOR(1.0985, 0.01) = 1.09 <br>

=CEILING(0.7461, 0.1) = 0.8 <br>

FLOOR(-1.5) is -2 and CEILING(-1.5) is -1 <br>

Google Sheets has two related functions called FLOOR.MATH() and CEILING.MATH(). When given one or two arguments, they behave in the same way as FLOOR() and CEILING() respectively. However, you can pass the value 1 to a third argument to make them round towards or away from zero. <br>

That is, FLOOR.MATH(-1.5, , 1) is -1 and CEILING.MATH(-1.5, , 1) is -2 <br>

## Random Numbers
=RAND() <br>
=RANDBETWEEN(lo, hi) <br>
=NORMINV(RAND(), 3, 2) mean 3 and standard deviation 2 <br>

## Logical Operations
=NOT() <br>
=AND() <br>
=OR() <br>

## Flow Control
=IF(condition, this op if condition true, else this op) <br>
=IFS(condition1, op1, condition2, op2, .....conditionN, opN) <br>
=SWITCH(Range, "value1", opValue1, "value2", opValue2, ....) <br>

## Blanks, missing values, & errors
Error	Cause <br>
#DIV/0!	Dividing by zero. <br>
#VALUE!	Nonsense data in a calculation. <br>
#REF!	Referencing a cell that has been deleted. <br>
#NAME?	Forgetting to quote a string. <br>
#NUM!	Numbers being out of range. <br>
#N/A	Missing value. <br>
#ERROR!	Syntax problem in a formula. <br>

=ISBLANK() <br>
=COUNTBLANK(Range) <br>
=NA() = #N/A <br>
=ISERROR() <br>
=ISERR() <br>

## Cell Addresses
=ROW() <br>
=COLUMN() <br>
=ADDRESS(H5, I5) Absolute <br>
=ADDRESS(H5, I5, 4) Relative <br>
=INDIRECT() <br>
=OFFSET(cell_reference, offset_rows, offset_columns, [height], [width]) <br>
=INDEX(Range, row, column) <br>

## Lookups & matching
=VLOOKUP(search_key, range, index, [is_sorted]) <br>
=SORT(range, sort_column, is_ascending, [sort_column2, ...], [is_ascending2, ...]) <br>
=MATCH(search_key, range, [search_type]) <br>

=UNIQUE(Range) <br>
=COUNTIF(Range,value) <br>
=COUNTIFS(Range1, value1, Range2, value2...) <br>
=SUMIF(Range1, value1 in Range1, Range2) = Sum of values coresponding to value1 in Range2 <br>
=AVERAGEIF(Range1, value1 in Range1, Range2) = Average of values coresponding to value1 in Range2
