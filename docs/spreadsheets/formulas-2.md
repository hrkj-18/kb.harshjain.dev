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