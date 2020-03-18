---
title: Jak dotaz ovat znaky v řetězci (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: d85e488a38a6167505732103b4c540cade6ea9bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345684"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a>Jak dotaz ovat znaky v řetězci (LINQ) (C#)
Vzhledem <xref:System.String> k tomu, <xref:System.Collections.Generic.IEnumerable%601> že třída implementuje obecné rozhraní, může být libovolný řetězec dotazován jako posloupnost znaků. To však není běžné použití LINQ. Pro operace porovnávání složitých vzorů použijte třídu. <xref:System.Text.RegularExpressions.Regex>  
  
## <a name="example"></a>Příklad  
 Následující příklad dotazuje řetězec určit počet číselných číslic, které obsahuje. Všimněte si, že dotaz je "znovu použít" po jeho prvním spuštění. To je možné, protože dotaz sám neukládá žádné skutečné výsledky.  
  
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
 Vytvořte projekt aplikace konzoly `using` Jazyka C# se direktivami pro obory názvů System.Linq a System.IO.  
  
## <a name="see-also"></a>Viz také

- [LINQ a řetězce (C#)](./linq-and-strings.md)
- [Jak kombinovat dotazy LINQ s regulárními výrazy (C#)](./how-to-combine-linq-queries-with-regular-expressions.md)
