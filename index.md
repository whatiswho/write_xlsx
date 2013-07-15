---
layout: default
title: WriteXLSX
---
### <a name="contents" class="anchor" href="#contents"><span class="octicon octicon-link" /></a>CONTENTS
* [DESCRIPTION](#description)
* [SYNOPSIS](#synopsis)
* [EXAMPLES](examples.html)
* [WORKBOOK METHOD](workbook.html)
* [WORKSHEET METHOD](worksheet.html)
* [PAGE SET-UP METHOD](page_set_up.html)
* [CELL FORMATTING](cell_formatting.html)
* [FORMAT METHODS](format.html)
* [COLORS IN EXCEL](colors.html)
* [DATES AND TIME IN EXCEL](dates_and_time.html)
* [OUTLINES AND GROUPING IN EXCEL](outlines_and_grouping.html)
* [DATA VALIDATION IN EXCEL](data_validation.html)
* [CONDITIONAL FORMATTING IN EXCEL](conditional_formatting.html)
* [SPARKLINES IN EXCEL](sparklines.html)
* [TABLES IN EXCEL](tables.html)
* [FORMURAS AND FUNCTIONS IN EXCEL](formulas_and_functions.html)
* [CHART METHODS](chart.html)
* [CHART FONTS](chart_fonts.html)
* [SHAPE](shape.html)

### <a name="description" class="anchor" href="#description"><span class="octicon octicon-link" /></a>DESCRIPTION
The WriteXLSX rubygem can be used to create an Excel file in the 2007+ XLSX format.

This is ported to Ruby from Perl module [Excel::Wirter::XLSX](http://search.cpan.org/~jmcnamara/Excel-Writer-XLSX-0.70/).

The XLSX format is the Office Open XML (OOXML) format used by Excel 2007 and later.

Multiple worksheets can be added to a workbook and formatting can be applied to cells.
Text, numbers, and formulas can be written to the cells.

This module cannot, as yet, be used to write to an existing Excel XLSX file.

WriteXLSX uses the same interface as the Writeexcel rubygem which produces an Excel file in binary XLS format.
WriteXLSX supports all of the features of Writeexcel and in some cases has more functionality. For more details see ["Compatibility with Writeexcel"](compatibility_with_writeexcel.html).

The main advantage of the XLSX format over the XLS format is that it allows a larger number of rows and columns in a worksheet.
The XLSX file format also produces much smaller files than the XLS file format.

### <a name="synopsis" class="anchor" href="#synopsis"><span class="octicon octicon-link" /></a>SYNOPSIS

To write a string, a formatted string, a number and a formula to the first worksheet in an Excel workbook called ruby.xlsx:

    require 'write_xlsx'

    # Create a new Excel workbook
    workbook = WriteXLSX.new('ruby.xlsx')

    # Add a worksheet
    worksheet = workbook.add_worksheet

    #  Add and define a format
    format = workbook.add_format
    format.set_bold
    format.set_color('red')
    format.set_align('center')

    # Write a formatted and unformatted string, row and column notation.
    col = row = 0
    worksheet.write(row, col, 'Hi Excel!', format)
    worksheet.write(1, col, 'Hi Excel!')

    # Write a number and a formula using A1 notation
    worksheet.write('A3', 1.2345 )
    worksheet.write('A4', '=SIN(PI()/4)')