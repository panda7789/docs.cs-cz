---
title: Řetězení příklad dotazů (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: d28f5f4ed4f9e6deb5f6f3d381d310ebcef6e132
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="chaining-queries-example-c"></a>Řetězení příklad dotazů (C#)
Tento příklad vychází z předchozího příkladu a zobrazuje, co se stane, když jste řetězu společně dva dotazy, které obě používají odložené provedení a opožděné vyhodnocení.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je zavádí další metodou rozšíření, `AppendString`, který připojí zadaný řetězec na každý řetězec ve zdrojové kolekci a pak vypočítá nových řetězců.  
  
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
  
 Co by měl být vymazat z tohoto příkladu je, že i když budeme mít zřetězen dohromady dotazy, které vrací kolekce, jsou materializována žádné zprostředkující kolekce. Místo toho každá položka předat z jedné opožděné metody na další. Výsledkem mnohem menší nároky paměti než přístup, které by nejprve trvat jedno pole řetězců, a poté vytvořit druhé pole řetězců, které mají byl převeden na velká písmena a nakonec vytvořte třetí pole řetězců, kde má každý řetězec vykřičníku body, přidá se k němu.  
  
 Další téma v tomto kurzu znázorňuje zprostředkující materialization:  
  
-   [Zprostředkující Materialization (C#)](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)  
  
## <a name="see-also"></a>Viz také  
 [Kurz: Řetězení dotazy společně (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
