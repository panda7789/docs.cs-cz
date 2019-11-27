---
title: 'Postupy: Řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ)'
ms.date: 07/20/2015
ms.assetid: 9df137fe-335b-46e0-aecf-ea8a9eddd4e3
ms.openlocfilehash: 15e7666a5fcb5a16628216354c18599f87c7d905
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341519"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-visual-basic"></a>Postupy: řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (Visual Basic)

Následující příklad ukazuje, jak řadit řádky strukturovaného textu, například hodnoty oddělené čárkami, podle libovolného pole na řádku. Pole lze dynamicky určit za běhu. Předpokládat, že pole v souboru skóre. csv reprezentují číslo ID studenta, po kterém následuje řada čtyř výsledků testu.

### <a name="to-create-a-file-that-contains-data"></a>Vytvoření souboru, který obsahuje data

Zkopírujte data výsledků. CSV z tématu [Postupy: spojení obsahu z nepodobných souborů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) a jeho uložení do složky řešení.

## <a name="example"></a>Příklad

```vb
Class SortLines

    Shared Sub Main()
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")

        ' Change this to any value from 0 to 4
        Dim sortField As Integer = 1

        Console.WriteLine("Sorted highest to lowest by field " & sortField)

        ' Demonstrates how to return query from a method.
        ' The query is executed here.
        For Each str As String In SortQuery(scores, sortField)
            Console.WriteLine(str)
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()

    End Sub

    Shared Function SortQuery(
        ByVal source As IEnumerable(Of String),
        ByVal num As Integer) As IEnumerable(Of String)

        Dim scoreQuery = From line In source
                         Let fields = line.Split(New Char() {","})
                         Order By fields(num) Descending
                         Select line

        Return scoreQuery
    End Function
End Class
' Output:
' Sorted highest to lowest by field 1
' 116, 99, 86, 90, 94
' 120, 99, 82, 81, 79
' 111, 97, 92, 81, 60
' 114, 97, 89, 85, 82
' 121, 96, 85, 91, 60
' 122, 94, 92, 91, 91
' 117, 93, 92, 80, 87
' 118, 92, 90, 83, 78
' 113, 88, 94, 65, 91
' 112, 75, 84, 91, 39
' 119, 68, 79, 88, 92
' 115, 35, 72, 91, 70
```

Tento příklad také ukazuje, jak vrátit proměnnou dotazu z funkce.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Vytvořte projekt konzolové aplikace VB.NET s příkazem `Imports` pro obor názvů System. Linq.

## <a name="see-also"></a>Viz také:

- [LINQ a řetězce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
