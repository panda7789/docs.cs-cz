---
title: Příklad řetězení dotazů (C#)
description: Tento příklad ukazuje, co se stane při zřetězení dvou dotazů, které používají odložené provádění a opožděné vyhodnocení v jazyce C#.
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 0cfcfe1c8f537778fd1ef909277d95d83991af51
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105543"
---
# <a name="chaining-queries-example-c"></a>Příklad řetězení dotazů (C#)
Tento příklad sestaví v předchozím příkladu a ukazuje, co se stane, když zřetězení dvou dotazů, které používají odložené provádění a opožděné vyhodnocení.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je zavedena jiná rozšiřující metoda, `AppendString` která připojí zadaný řetězec ke každému řetězci ve zdrojové kolekci a následně vytvoří nové řetězce.  
  
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
  
```output  
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
  
 To, co by mělo být z tohoto příkladu jasné, je, že i když jsme zřetězené dotazy, které poskytují kolekce, nematerializují žádné zprostředkující kolekce. Místo toho je každá položka předána z jedné opožděné metody do další. To vede k mnohem menšímu nároky na paměť než k přístupu, který by nejdřív přijal jedno pole řetězců, pak vytvoří druhé pole řetězců, které se převedlo na velká písmena, a nakonec vytvoří třetí pole řetězců, kde se ke každému řetězci připojí vykřičník.  
  
 Další téma v tomto kurzu ilustruje mezilehlé vymaterializování:  
  
- [Zprostředkující materializace (C#)](./intermediate-materialization.md)  
  
## <a name="see-also"></a>Viz také

- [Kurz: zřetězení dotazů společně (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
