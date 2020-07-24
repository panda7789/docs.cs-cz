---
title: Zřetězení standardních operátorů dotazu (C#)
description: Tento příklad ukazuje, jak lze v jazyce C# také zřetězit standardní operátory dotazu. Dotaz nevyhodnotit mezilehlé výsledky.
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 41a7e4c7910c783d07181fe16254b0cac6902794
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104067"
---
# <a name="chaining-standard-query-operators-together-c"></a>Zřetězení standardních operátorů dotazu (C#)
Toto je poslední téma v [kurzu: zřetězení dotazů společně (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) .  
  
 Standardní operátory dotazu je také možné zřetězit dohromady. Například můžete interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operátor a funguje také opožděným způsobem. Žádné mezilehlé výsledky nejsou materializované.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.Linq.Enumerable.Where%2A> je metoda volána před voláním `ConvertCollectionToUpperCase` . <xref:System.Linq.Enumerable.Where%2A>Metoda pracuje téměř přesně stejným způsobem jako opožděné metody používané v předchozích příkladech v tomto kurzu `ConvertCollectionToUpperCase` a `AppendString` .  
  
 Jedním rozdílem je, že v tomto případě <xref:System.Linq.Enumerable.Where%2A> Metoda prochází ze své zdrojové kolekce, určuje, že první položka neprojde predikátem, a poté získá další položku, která je předána. Následně výsledkem bude druhá položka.  
  
 Základní nápad je ale stejný: zprostředkující kolekce nejsou materializované, pokud je nemusíte.  
  
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
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
