---
title: Příklad zřetězení dotazů (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 45e3a4f341ca8eb06ff0f553e0f933956e6c6546
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70205417"
---
# <a name="chaining-queries-example-c"></a>Příklad zřetězení dotazů (C#)
Tento příklad vychází z předchozího příkladu a ukazuje, co se stane, když zřetězení dohromady dva dotazy, které oba používají odložené spuštění a opožděné vyhodnocení.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je zavedena `AppendString`jiná metoda rozšíření , která připojí zadaný řetězec ke každému řetězci ve zdrojové kolekci a pak dává nové řetězce.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
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
  
 V tomto příkladu uvidíte, že každá metoda rozšíření pracuje jeden po druhém pro každou položku ve zdrojové kolekci.  
  
 Co by mělo být jasné z tohoto příkladu je, že i když jsme zřetězené společně dotazy, které výnos kolekce, žádné zprostředkující kolekce jsou materialized. Místo toho každá položka je předánz jedné opožděné metody na další. Výsledkem je mnohem menší nároky na paměť než přístup, který by nejprve trvat jedno pole řetězců, pak vytvořit druhé pole řetězců, které byly převedeny na velká písmena a nakonec vytvořit třetí pole řetězců, kde každý řetězec má vykřičník připojených bodů.  
  
 Další téma v tomto kurzu ilustruje zprostředkující materializaci:  
  
- [Zprostředkující materializace (C#)](./intermediate-materialization.md)  
  
## <a name="see-also"></a>Viz také

- [Kurz: Řetězení dotazů dohromady (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
