---
title: 'Postupy: dotaz na znaky v řetězci (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: f2102a8cb149fa9c7886826e509bf254fad5eb95
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582715"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a>Postupy: dotaz na znaky v řetězci (LINQ) (Visual Basic)

Vzhledem k tomu, že třída <xref:System.String> implementuje obecné rozhraní <xref:System.Collections.Generic.IEnumerable%601>, může být libovolný řetězec dotazován jako posloupnost znaků. Nejedná se však o běžné použití LINQ. Pro komplexní operace porovnávání vzorů použijte třídu <xref:System.Text.RegularExpressions.Regex>.

## <a name="example"></a>Příklad

Následující příklad vyhledá řetězec, který určí počet číslic, které obsahuje. Všimněte si, že po prvním spuštění dotazu je dotaz znovu použit. To je možné, protože samotný dotaz neukládá žádné skutečné výsledky.

```vb
Class QueryAString

    Shared Sub Main()

        ' A string is an IEnumerable data source.
        Dim aString As String = "ABCDE99F-J74-12-89A"

        ' Select only those characters that are numbers
        Dim stringQuery = From ch In aString
                          Where Char.IsDigit(ch)
                          Select ch
        ' Execute the query
        For Each c As Char In stringQuery
            Console.Write(c & " ")
        Next

        ' Call the Count method on the existing query.
        Dim count As Integer = stringQuery.Count()
        Console.WriteLine(System.Environment.NewLine & "Count = " & count)

        ' Select all characters before the first '-'
        Dim stringQuery2 = aString.TakeWhile(Function(c) c <> "-")

        ' Execute the second query
        For Each ch In stringQuery2
            Console.Write(ch)
        Next

        Console.WriteLine(System.Environment.NewLine & "Press any key to exit")
        Console.ReadKey()
    End Sub
End Class
' Output:
' 9 9 7 4 1 2 8 9
' Count = 8
' ABCDE99F
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Vytvořte projekt konzolové aplikace VB.NET s příkazem `Imports` pro obor názvů System. Linq.

## <a name="see-also"></a>Viz také:

- [LINQ a řetězce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [Postupy: kombinování dotazů LINQ s regulárními výrazy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
