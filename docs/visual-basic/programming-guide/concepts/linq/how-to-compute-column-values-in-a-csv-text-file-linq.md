---
title: 'Postupy: Výpočet hodnot sloupce v textovém souboru CSV (LINQ)'
ms.date: 07/20/2015
ms.assetid: 88b2b9f3-c82e-41f3-b1b4-26ede5973a02
ms.openlocfilehash: 679d53787b1392181696c05e0327ca1b1b910015
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357501"
---
# <a name="how-to-compute-column-values-in-a-csv-text-file-linq-visual-basic"></a>Postupy: výpočet hodnot sloupce v textovém souboru CSV (LINQ) (Visual Basic)

Tento příklad ukazuje, jak provádět agregované výpočty, jako je součet, průměr, minimum a maximum ve sloupcích souboru. csv. Příklady zásad, které jsou zde uvedeny, lze použít na jiné typy strukturovaného textu.

### <a name="to-create-the-source-file"></a>Vytvoření zdrojového souboru

1. Zkopírujte následující řádky do souboru s názvem skóre. csv a uložte ho do složky projektu. Předpokládejme, že první sloupec představuje ID studenta, přičemž následující sloupce představují skóre ze čtyř zkoušek.

    ```csv
    111, 97, 92, 81, 60
    112, 75, 84, 91, 39
    113, 88, 94, 65, 91
    114, 97, 89, 85, 82
    115, 35, 72, 91, 70
    116, 99, 86, 90, 94
    117, 93, 92, 80, 87
    118, 92, 90, 83, 78
    119, 68, 79, 88, 92
    120, 99, 82, 81, 79
    121, 96, 85, 91, 60
    122, 94, 92, 91, 91
    ```

## <a name="example"></a>Příklad

```vb
Class SumColumns

    Public Shared Sub Main()

        Dim lines As String() = System.IO.File.ReadAllLines("../../../scores.csv")

        ' Specifies the column to compute
        ' This value could be passed in at runtime.
        Dim exam = 3

        ' Spreadsheet format:
        ' Student ID    Exam#1  Exam#2  Exam#3  Exam#4
        ' 111,          97,     92,     81,     60
        ' one is added to skip over the first column
        ' which holds the student ID.
        SumColumn(lines, exam + 1)
        Console.WriteLine()
        MultiColumns(lines)

        ' Keep the console window open in debug mode.
        Console.WriteLine("Press any key to exit...")
        Console.ReadKey()

    End Sub

    Shared Sub SumColumn(ByVal lines As IEnumerable(Of String), ByVal col As Integer)

        ' This query performs two steps:
        ' split the string into a string array
        ' convert the specified element to
        ' integer and select it.
        Dim columnQuery = From line In lines
                           Let x = line.Split(",")
                           Select Convert.ToInt32(x(col))

        ' Execute and cache the results for performance.
        ' Only needed with very large files.
        Dim results = columnQuery.ToList()

        ' Perform aggregate calculations
        ' on the column specified by col.
        Dim avgScore = Aggregate score In results Into Average(score)
        Dim minScore = Aggregate score In results Into Min(score)
        Dim maxScore = Aggregate score In results Into Max(score)

        Console.WriteLine("Single Column Query:")
        Console.WriteLine("Exam #{0}: Average:{1:##.##} High Score:{2} Low Score:{3}",
                     col, avgScore, maxScore, minScore)

    End Sub

    Shared Sub MultiColumns(ByVal lines As IEnumerable(Of String))

        Console.WriteLine("Multi Column Query:")

        ' Create the query. It will produce nested sequences.
        ' multiColQuery performs these steps:
        ' 1) convert the string to a string array
        ' 2) skip over the "Student ID" column and take the rest
        ' 3) convert each field to an int and select that
        '    entire sequence as one row in the results.
        Dim multiColQuery = From line In lines
                            Let fields = line.Split(",")
                            Select From str In fields Skip 1
                                        Select Convert.ToInt32(str)

        Dim results = multiColQuery.ToList()

        ' Find out how many columns we have.
        Dim columnCount = results(0).Count()

        ' Perform aggregate calculations on each column.
        ' One loop for each score column in scores.
        ' We can use a for loop because we have already
        ' executed the multiColQuery in the call to ToList.

        For j As Integer = 0 To columnCount - 1
            Dim column = j
            Dim res2 = From row In results
                       Select row.ElementAt(column)

            ' Perform aggregate calculations
            ' on the column specified by col.
            Dim avgScore = Aggregate score In res2 Into Average(score)
            Dim minScore = Aggregate score In res2 Into Min(score)
            Dim maxScore = Aggregate score In res2 Into Max(score)

            ' Add 1 to column numbers because exams in this course start with #1
            Console.WriteLine("Exam #{0} Average: {1:##.##} High Score: {2} Low Score: {3}",
                              column + 1, avgScore, maxScore, minScore)

        Next
    End Sub

End Class
' Output:
' Single Column Query:
' Exam #4: Average:76.92 High Score:94 Low Score:39

' Multi Column Query:
' Exam #1 Average: 86.08 High Score: 99 Low Score: 35
' Exam #2 Average: 86.42 High Score: 94 Low Score: 72
' Exam #3 Average: 84.75 High Score: 91 Low Score: 65
' Exam #4 Average: 76.92 High Score: 94 Low Score: 39
```

Dotaz funguje pomocí <xref:System.String.Split%2A> metody pro převod každého řádku textu na pole. Každý prvek pole představuje sloupec. Nakonec se text v každém sloupci převede na jeho číselné vyjádření. Pokud je soubor soubor oddělený tabulátory, stačí aktualizovat argument v `Split` metodě na `\t` .

## <a name="compile-the-code"></a>Kompilovat kód

Vytvořte projekt konzolové aplikace Visual Basic s `Imports` příkazem pro obor názvů System. Linq.

## <a name="see-also"></a>Viz také

- [LINQ a řetězce (Visual Basic)](linq-and-strings.md)
- [LINQ a souborové adresáře (Visual Basic)](linq-and-file-directories.md)
