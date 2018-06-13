---
title: Odložené provedení příklad (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 8613f2335e5b3cb2a012f5309307e081b9400709
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335923"
---
# <a name="deferred-execution-example-c"></a>Odložené provedení příklad (C#)
Toto téma ukazuje, jak odložené provedení a opožděné vyhodnocení ovlivnit provádění vaší technologie LINQ to XML dotazy.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje pořadí provádění při použití metody rozšíření, která používá odložené provedení. V příkladu deklaruje pole tři řetězců. Ji pak iteruje kolekcí vrácený `ConvertCollectionToUpperCase`.  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source {0}", str);  
            yield return str.ToUpper();  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        var q = from str in stringArray.ConvertCollectionToUpperCase()  
                select str;  
  
        foreach (string str in q)  
            Console.WriteLine("Main: str {0}", str);  
    }  
}  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 Všimněte si, že když iterace v rámci kolekce vrácené `ConvertCollectionToUpperCase`, každé položky se načítají z pole řetězců zdroje a převeden na velká písmena před další položky se načítají z pole řetězců zdroje.  
  
 Uvidíte, že celé pole řetězce není převeden na velká písmena, před každou položku v kolekci vrácený při zpracování ve `foreach` smyčky v `Main`.  
  
 Další téma v tomto kurzu znázorňuje řetězení dotazy společně:  
  
-   [Řetězení příklad dotazů (C#)](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)  
  
## <a name="see-also"></a>Viz také  
 [Kurz: Řetězení dotazy společně (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
