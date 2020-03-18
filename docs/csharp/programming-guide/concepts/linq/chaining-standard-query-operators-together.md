---
title: Zřetězení operátorů standardních dotazů dohromady (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 37df654b2bfdcc135460e5ded2ceec1eca33b35a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204206"
---
# <a name="chaining-standard-query-operators-together-c"></a>Zřetězení operátorů standardních dotazů dohromady (C#)
Toto je poslední téma v [kurzu: Řetězení dotazy společně (C#).](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)  
  
 Standardní operátory dotazu lze také zřetězit dohromady. Například můžete interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operátor a také pracuje v líné způsobem. Nezhmotňují se žádné průběžné výsledky.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je metoda `ConvertCollectionToUpperCase`volána před voláním <xref:System.Linq.Enumerable.Where%2A> . Metoda <xref:System.Linq.Enumerable.Where%2A> funguje téměř přesně stejným způsobem jako opožděné metody použité v `ConvertCollectionToUpperCase` předchozích příkladech v tomto kurzu a `AppendString`.  
  
 Jeden rozdíl je, že <xref:System.Linq.Enumerable.Where%2A> v tomto případě metoda iterates prostřednictvím své zdrojové kolekce, určuje, že první položka neprojde predikáta a pak získá další položku, která přejde. Potom dává druhou položku.  
  
 Základní myšlenka je však stejná: Zprostředkující kolekce se nezhmotňují, pokud nemusí být.  
  
 Při použití výrazů dotazu jsou převedeny na volání standardních operátorů dotazů a platí stejné zásady.  
  
 Všechny příklady v této části, které se dotazují na dokumenty Office Open XML, používají stejný princip. Odložené spuštění a opožděné vyhodnocení jsou některé základní koncepty, které je nutné pochopit efektivně používat LINQ (a LINQ na XML).  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
