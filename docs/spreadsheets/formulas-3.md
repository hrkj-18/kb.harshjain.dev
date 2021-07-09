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