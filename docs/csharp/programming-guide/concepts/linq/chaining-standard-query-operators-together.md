---
title: Zřetězení standardních operátorů dotazů (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 89cf7f526bdc60881e901d7ca8f556e97488b220
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594837"
---
# <a name="chaining-standard-query-operators-together-c"></a>Zřetězení standardních operátorů dotazů (C#)
Toto je poslední téma v [tomto kurzu: Zřetězení dotazů spolu (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) kurz.  
  
 Standardní operátory dotazu je také možné zřetězit dohromady. Například můžete interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operátor a funguje také opožděným způsobem. Žádné mezilehlé výsledky nejsou materializované.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.Linq.Enumerable.Where%2A> je metoda volána před voláním `ConvertCollectionToUpperCase`. Metoda pracuje téměř přesně stejným způsobem jako opožděné metody používané v předchozích příkladech v tomto `ConvertCollectionToUpperCase` kurzu a `AppendString`. <xref:System.Linq.Enumerable.Where%2A>  
  
 Jedním rozdílem je, že v tomto případě <xref:System.Linq.Enumerable.Where%2A> Metoda prochází ze své zdrojové kolekce, určuje, že první položka neprojde predikátem, a poté získá další položku, která je předána. Následně výsledkem bude druhá položka.  
  
 Základní nápad je však stejný: Mezilehlé kolekce nejsou materializované, pokud je nepotřebujete.  
  
 Pokud jsou výrazy dotazu použity, jsou převedeny na volání standardních operátorů dotazu a platí stejné zásady.  
  
 Všechny příklady v této části, které se dotazují na dokumenty Office Open XML, používají stejný princip. Odložené provádění a opožděné hodnocení jsou některé ze základních konceptů, které je potřeba pochopit, abyste mohli efektivně používat LINQ (a LINQ to XML).  
  
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
            where s.CompareTo("D") >= 0  
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
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  