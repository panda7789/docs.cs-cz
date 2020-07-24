---
title: Příklad odloženého provedení (C#)
description: Informace o tom, jak odložené provádění a opožděné vyhodnocení ovlivňuje provádění vašich LINQ to XML dotazů v jazyce C#.
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 65ba4cc150f2fc9d8f44aee352987ea0eeaab0a5
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103953"
---
# <a name="deferred-execution-example-c"></a>Příklad odloženého provedení (C#)
Toto téma ukazuje, jak odložené provádění a opožděné vyhodnocení ovlivní spuštění dotazů LINQ to XML.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje pořadí spouštění při použití metody rozšíření, která používá odložené provádění. Příklad deklaruje pole tří řetězců. Poté provede iteraci kolekcí vrácenou `ConvertCollectionToUpperCase` .  
  
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
  
```output  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 Všimněte si, že při iteraci v kolekci `ConvertCollectionToUpperCase` , kterou vrátí, každá položka je načtena ze zdrojového pole řetězce a převedena na velká písmena před načtením další položky ze zdrojového pole řetězce.  
  
 Můžete vidět, že celé pole řetězců není převedeno na velká písmena před tím, než se každá položka v vrácené kolekci zpracuje ve `foreach` smyčce v `Main` .  
  
 Další téma v tomto kurzu znázorňuje zřetězení dotazů dohromady:  
  
- [Příklad řetězení dotazů (C#)](./chaining-queries-example.md)  
  
## <a name="see-also"></a>Viz také

- [Kurz: zřetězení dotazů společně (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
