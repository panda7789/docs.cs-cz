---
title: 'Postupy: dotazu na znaky v řetězci (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: db535f55822fa40d8589ddf95f9f78adfa1b6f1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a>Postupy: dotazu na znaky v řetězci (LINQ) (C#)
Protože <xref:System.String> třída implementuje obecná <xref:System.Collections.Generic.IEnumerable%601> rozhraní, může být dotazován libovolný řetězec jako posloupnosti znaků. Je to ale není běžně se používají LINQ. Pro komplexní vzor odpovídající operace, použijte <xref:System.Text.RegularExpressions.Regex> třídy.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se dotazuje řetězec můžete určit počet číslic, které obsahuje. Všimněte si, že dotaz je "opakovaně" po provedení první. To je možné, protože samotný dotaz neukládá skutečné výsledky.  
  
```csharp  
class QueryAString  
{  
    static void Main()  
    {  
        string aString = "ABCDE99F-J74-12-89A";  
  
        // Select only those characters that are numbers  
        IEnumerable<char> stringQuery =  
          from ch in aString  
          where Char.IsDigit(ch)  
          select ch;  
  
        // Execute the query  
        foreach (char c in stringQuery)  
            Console.Write(c + " ");  
  
        // Call the Count method on the existing query.  
        int count = stringQuery.Count();  
        Console.WriteLine("Count = {0}", count);  
  
        // Select all characters before the first '-'  
        IEnumerable<char> stringQuery2 = aString.TakeWhile(c => c != '-');  
  
        // Execute the second query  
        foreach (char c in stringQuery2)  
            Console.Write(c);  
  
        Console.WriteLine(System.Environment.NewLine + "Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
  Output: 9 9 7 4 1 2 8 9  
  Count = 8  
  ABCDE99F  
*/  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší, s odkazem na System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.  
  
## <a name="see-also"></a>Viz také  
 [LINQ a řetězce (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 [Postupy: kombinace dotazů LINQ s regulárními výrazy (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
