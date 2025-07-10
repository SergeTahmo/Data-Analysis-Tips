' =======================================
'  Excel Data Formatting Cheat Sheet
' =======================================

' ========== 1. Format Numbers ==========
' Use: Home Tab → Number Group → Format Cells
' Shortcut: Ctrl + 1

' Currency Format:
=TEXT(A2, "$#,##0.00")

' Percentage Format:
=TEXT(A2, "0.00%")

' Thousands Separator:
=TEXT(A2, "#,##0")

' Custom Decimal Places:
=ROUND(A2, 2)

' ========== 2. Format Dates ==========
' Format as YYYY-MM-DD:
=TEXT(A2, "yyyy-mm-dd")

' Format as Month Name:
=TEXT(A2, "mmmm")

' Extract Year, Month, Day:
=YEAR(A2)
=MONTH(A2)
=DAY(A2)

' ========== 3. Combine & Clean Text ==========
' Proper Case:
=PROPER(A2)

' UPPERCASE:
=UPPER(A2)

' lowercase:
=LOWER(A2)

' Remove spaces:
=TRIM(A2)

' Remove line breaks:
=SUBSTITUTE(A2, CHAR(10), "")

' ========== 4. Format Phone Numbers ==========
' US Format (123) 456-7890:
=TEXT(A2, "(\###) \###\-####")

' ========== 5. Conditional Formatting ==========
' Highlight cells > 1000:
' Home → Conditional Formatting → Highlight Cells → Greater Than

' Color scale for ranges:
' Home → Conditional Formatting → Color Scales

' ========== 6. Format Cells with Rules ==========
' Home → Conditional Formatting → New Rule → Use a formula:
=ISBLANK(A2)                 ' Format empty cells
=AND(A2>0, A2<100)           ' Format custom range

' ========== 7. Dynamic Formatting with IF ==========
' Show label based on value:
=IF(A2>500, "High", "Low")

' Combine text with numbers:
="Total: $" & TEXT(A2, "#,##0.00")

' ========== 8. Cell Formatting Shortcuts ==========
' Ctrl + 1 : Format Cells dialog
' Ctrl + Shift + $ : Currency
' Ctrl + Shift + % : Percent
' Ctrl + Shift + # : Date
' Ctrl + Shift + @ : Time
' Ctrl + Shift + ^ : Scientific
' Ctrl + Shift + ! : Number (2 decimal places)

' ========================================
'  Tips:
' - Always format dates using ISO (yyyy-mm-dd) for consistency
' - Use TEXT() to convert formatted values to strings for exports
' - Use conditional formatting to create smart visual indicators
' ========================================
