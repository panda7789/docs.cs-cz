---
title: Příklad řetězení dotazů (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 8685db7461a1ce97c7a9c0045ed842fa4ac1a1f6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486192"
---
# <a name="chaining-queries-example-c"></a>Příklad řetězení dotazů (C#)
Tento příklad vychází z předchozího příkladu a ukazuje, co se stane, když je řetězec společně dva dotazy, které obě používají odložené provedení a opožděné vyhodnocení.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá jinou metodu rozšíření, `AppendString`, který připojí zadaný řetězec do každého řetězce ve zdrojové kolekci a pak provede nové řetězce.  
  
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
  
 V tomto příkladu vidíte, že funguje každá metoda rozšíření postupně pro každou položku v kolekci zdroje.  
  
 Co by mělo být jasné z tohoto příkladu je, že i když jsme mají zřetězit, dotazy, které vrací kolekce, jsou materializovaného zprostředkující se žádné kolekce. Místo toho každá položka je předán z jedné metody opožděné na další. Výsledkem mnohem menší nároky na paměť než přístupu, které by nejdřív proveďte jedno pole řetězců, pak vytvořte druhé pole řetězců, které byly převedeny na velká písmena a nakonec vytvořit třetí pole řetězců, kde má každý řetězec vykřičník body připojí k němu.  
  
 Další téma v tomto kurzu ukazuje přechodná materializace:  
  
- [Přechodná Materializace (C#)](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)  
  
## <a name="see-also"></a>Viz také:

- [Kurz: Zřetězení dotazů (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
