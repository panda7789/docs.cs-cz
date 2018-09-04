---
title: Příklad odloženého provedení (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 0ad1ed2998cfbd612f7f2b60a0d15c7ffcef0daf
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518472"
---
# <a name="deferred-execution-example-c"></a>Příklad odloženého provedení (C#)
Toto téma ukazuje, jak odložené provedení a opožděné vyhodnocení vliv na spuštění vašich dotazech LINQ to XML.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje pořadí provádění, když použijete metodu rozšíření, která používá odloženého provedení. V příkladu deklaruje pole tří řetězců. Pak Iteruje přes kolekci vrácené poskytovatelem `ConvertCollectionToUpperCase`.  
  
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
  
 Všimněte si, že při procházení kolekci vrácené poskytovatelem `ConvertCollectionToUpperCase`, každá položka je načten z řetězcového pole zdroje a převedený na velká písmena před další položky se načtou ze zdrojového pole řetězce.  
  
 Uvidíte, že celého pole řetězce není před každou položku v kolekci vrácené, jsou zpracovávána v převedený na velká písmena `foreach` smyčky v `Main`.  
  
 Další téma v tomto kurzu ukazuje řetězení dotazů dohromady:  
  
-   [Příklad řetězení dotazů (C#)](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)  
  
## <a name="see-also"></a>Viz také

- [Kurz: Zřetězení dotazů společně (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
