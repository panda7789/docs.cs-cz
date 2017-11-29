---
title: "Řetězení příklad dotazů (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 74d3dcaca686487d79a90f28faf4d9c00218f6a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
