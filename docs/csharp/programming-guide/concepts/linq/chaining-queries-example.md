---
title: Příklad řetězení dotazů (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 90c2ba1c9125114f9e26f4afeb3ff6373ff01d9c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594822"
---
# <a name="chaining-queries-example-c"></a>Příklad řetězení dotazů (C#)
Tento příklad sestaví v předchozím příkladu a ukazuje, co se stane, když zřetězení dvou dotazů, které používají odložené provádění a opožděné vyhodnocení.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je zavedena `AppendString`jiná rozšiřující metoda, která připojí zadaný řetězec ke každému řetězci ve zdrojové kolekci a následně vytvoří nové řetězce.  
  
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
        foreach (string str in source)  
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
  
```  
ToUpper: source >abc<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 V tomto příkladu vidíte, že každá metoda rozšíření funguje postupně pro každou položku ve zdrojové kolekci.  
  
 To, co by mělo být z tohoto příkladu jasné, je, že i když jsme zřetězené dotazy, které poskytují kolekce, nematerializují žádné zprostředkující kolekce. Místo toho je každá položka předána z jedné opožděné metody do další. To vede k mnohem menšímu nároky na paměť než k přístupu, který by nejdřív přijal jedno pole řetězců, a pak vytvoří druhé pole řetězců, které se převedlo na velká písmena a nakonec vytvoří třetí pole řetězců, kde má každý řetězec vykřičník připojené body.  
  
 Další téma v tomto kurzu ilustruje mezilehlé vymaterializování:  
  
- [Zprostředkující materializace (C#)](./intermediate-materialization.md)  
  
## <a name="see-also"></a>Viz také:

- [Kurz: Zřetězení dotazů společně (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
