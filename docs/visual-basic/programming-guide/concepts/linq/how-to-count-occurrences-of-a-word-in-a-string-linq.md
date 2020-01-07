---
title: 'Postupy: Počítání výskytů slova v řetězci (LINQ)'
ms.date: 07/20/2015
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
ms.openlocfilehash: 07742e7e99291e056e4c91a31b2e588e36a6e177
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348188"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a>Postupy: počítání výskytů slova v řetězci (LINQ) (Visual Basic)

Tento příklad ukazuje, jak pomocí dotazu LINQ spočítat výskyty zadaného slova v řetězci. Všimněte si, že k provedení tohoto počtu je nejprve volána metoda <xref:System.String.Split%2A> pro vytvoření pole slov. Do metody <xref:System.String.Split%2A> se účtují náklady na výkon. Pokud je jedinou operací na řetězci spočítat slova, měli byste zvážit použití metod <xref:System.Text.RegularExpressions.Regex.Matches%2A> nebo <xref:System.String.IndexOf%2A>. Pokud ale výkon není kritickým problémem nebo jste už tuto větu rozdělili, abyste mohli provádět další typy dotazů, je vhodné použít LINQ k počítání slov nebo frází.

## <a name="example"></a>Příklad

```vb
Class CountWords

    Shared Sub Main()

        Dim text As String = "Historically, the world of data and the world of objects" &
                  " have not been well integrated. Programmers work in C# or Visual Basic" &
                  " and also in SQL or XQuery. On the one side are concepts such as classes," &
                  " objects, fields, inheritance, and .NET Framework APIs. On the other side" &
                  " are tables, columns, rows, nodes, and separate languages for dealing with" &
                  " them. Data types often require translation between the two worlds; there are" &
                  " different standard functions. Because the object world has no notion of query, a" &
                  " query can only be represented as a string without compile-time type checking or" &
                  " IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" &
                  " objects in memory is often tedious and error-prone."

        Dim searchTerm As String = "data"

        ' Convert the string into an array of words.
        Dim dataSource As String() = text.Split(New Char() {" ", ",", ".", ";", ":"},
                                                 StringSplitOptions.RemoveEmptyEntries)

        ' Create and execute the query. It executes immediately
        ' because a singleton value is produced.
        ' Use ToLower to match "data" and "Data"
        Dim matchQuery = From word In dataSource
                      Where word.ToLowerInvariant() = searchTerm.ToLowerInvariant()
                      Select word

        ' Count the matches.
        Dim count As Integer = matchQuery.Count()
        Console.WriteLine(count & " occurrence(s) of the search term """ &
                          searchTerm & """ were found.")

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub
End Class
' Output:
' 3 occurrence(s) of the search term "data" were found.
```

## <a name="compile-the-code"></a>Kompilace kódu

Vytvořte projekt konzolové aplikace Visual Basic s příkazem `Imports` pro obor názvů System. Linq.

## <a name="see-also"></a>Viz také:

- [LINQ a řetězce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
