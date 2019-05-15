---
title: 'Postupy: Dotazu na znaky v řetězci (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: fba5d8ca6c0c060c76b1ecf4f66434ce0884e733
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593315"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a>Postupy: Dotazu na znaky v řetězci (LINQ) (Visual Basic)
Vzhledem k tomu, <xref:System.String> třída implementuje obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní, libovolný řetězec může být dotázán jako posloupnost znaků. Ale to není běžné použití odkazu LINQ. Pro komplexní porovnávání vzorů operace, použijte <xref:System.Text.RegularExpressions.Regex> třídy.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se dotazuje řetězec a chce určit počet číslic, které obsahuje. Všimněte si, že dotaz je "znovu" po provedení první. To je možné, protože samotný dotaz nejsou uložené žádné skutečné výsledky.  
  
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
Vytvoření projektu aplikace konzoly VB.NET, pomocí `Imports` příkaz pro obor názvů System.Linq.
  
## <a name="see-also"></a>Viz také:

- [LINQ a řetězce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [Postupy: Kombinace dotazů LINQ s regulárními výrazy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
