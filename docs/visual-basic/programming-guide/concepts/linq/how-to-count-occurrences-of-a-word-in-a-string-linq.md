---
title: 'Postupy: Počet výskytů slova v řetězci (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
ms.openlocfilehash: b3d34503e87aff1180dca4cb8233d668d35b0255
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051738"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a>Postupy: Počet výskytů slova v řetězci (LINQ) (Visual Basic)
Tento příklad ukazuje, jak můžete počítat výskyty zadaného slova v řetězci dotazu LINQ. Všimněte si, že počet, nejprve provést <xref:System.String.Split%2A> metoda je volána k vytvoření pole slov. Je snížení výkonu <xref:System.String.Split%2A> metody. Pokud je počet slov pouze operace s řetězci, měli byste zvážit použití <xref:System.Text.RegularExpressions.Regex.Matches%2A> nebo <xref:System.String.IndexOf%2A> metody místo. Ale pokud výkon není kritický problém nebo jste už rozdělili věty nad ním provádět jiné typy dotazů, pak je vhodné zprostředkovatel LINQ slouží pro počet slov nebo frází také.  
  
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
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `Imports` příkaz pro obor názvů System.Linq.  
  
## <a name="see-also"></a>Viz také:

- [LINQ a řetězce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
