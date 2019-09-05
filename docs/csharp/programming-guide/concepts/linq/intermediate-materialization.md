---
title: Zprostředkující materializace (C#)
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: af1eb7df7da02d8e72fc102cda4ee5f329dc7974
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253166"
---
# <a name="intermediate-materialization-c"></a>Zprostředkující materializace (C#)
Pokud nejste opatrní, v některých situacích můžete významně změnit velikost paměti a profilu výkonu aplikace tím, že ve svých dotazech dojde k předčasnému materializování kolekcí. Některé standardní operátory dotazu způsobují materializaci své zdrojové kolekce před tím, než budou vracet jediný element. Například <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> první projde celou zdrojovou kolekcí a pak seřadí všechny položky a nakonec vyřadí první položku. To znamená, že je nákladné získat první položku seřazené kolekce. u každé položky pak není nákladné. To je smysl: To by nebylo možné, aby tento operátor dotazu jinak nepoužil.  
  
## <a name="example"></a>Příklad  
 Tento příklad změní předchozí příklad. `AppendString` Metoda volá<xref:System.Linq.Enumerable.ToList%2A> před iterací ve zdroji. Příčinou je materializace.  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        // the following statement materializes the source collection in a List<T>  
        // before iterating through it  
        foreach (string str in source.ToList())  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
ToUpper: source >ghi<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 V tomto příkladu vidíte, že volání z důvodu <xref:System.Linq.Enumerable.ToList%2A> `AppendString` vyčíslení celého zdroje před vyvoláním první položky. Pokud by byl zdrojem velké pole, významně byste tím změnili profil paměti aplikace.  
  
 Standardní operátory dotazu je také možné zřetězit dohromady. Toto je znázorněno v posledním tématu tohoto kurzu.  
  
- [Zřetězení standardních operátorů dotazů (C#)](./chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a>Viz také:

- [Kurz: Zřetězení dotazů společně (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
