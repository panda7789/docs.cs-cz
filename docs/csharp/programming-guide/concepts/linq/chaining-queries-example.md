---
title: Příklad řetězení dotazů (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: b77de6b1e5bd81ac70165640aecf0d4ce89be03d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702630"
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

- [Kurz: Zřetězení dotazů (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
