---
title: Dotazování na znaky v řetězci (LINQ) (C#)
description: Můžete zadat dotaz na řetězec jako posloupnost znaků v LINQ. V tomto příkladu jazyka C# se dotazuje na řetězec, který určuje počet číslic, které obsahuje.
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: 3512be7c30843fcd8e881eab59761706a84a3ac8
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104553"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a>Dotazování na znaky v řetězci (LINQ) (C#)
Vzhledem k tomu <xref:System.String> , že třída implementuje obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní, může být libovolný řetězec dotazován jako posloupnost znaků. Nejedná se však o běžné použití LINQ. Pro komplexní operace porovnávání vzorů použijte <xref:System.Text.RegularExpressions.Regex> třídu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vyhledá řetězec, který určí počet číslic, které obsahuje. Všimněte si, že po prvním spuštění dotazu je dotaz znovu použit. To je možné, protože samotný dotaz neukládá žádné skutečné výsledky.  
  
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
 Vytvořte projekt konzolové aplikace v jazyce C# se `using` direktivami pro obory názvů System. Linq a System.IO.  
  
## <a name="see-also"></a>Viz také

- [LINQ a řetězce (C#)](./linq-and-strings.md)
- [Jak kombinovat dotazy LINQ s regulárními výrazy (C#)](./how-to-combine-linq-queries-with-regular-expressions.md)
