---
title: Řetězení standardní operátory dotazu společně (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 9e59c12873b8e8afeaad43b8ffbe400b43b55747
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="chaining-standard-query-operators-together-c"></a>Řetězení standardní operátory dotazu společně (C#)
Toto je poslední téma v [kurz: řetězení dotazy společně (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md) kurzu.  
  
 Také můžete se propojit standardní operátory dotazu. Například můžete interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operátor a také funguje opožděné způsobem. Tímto se materializovat žádné mezilehlých výsledků.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.Linq.Enumerable.Where%2A> metoda je volána před provedením volání `ConvertCollectionToUpperCase`. <xref:System.Linq.Enumerable.Where%2A> Metoda funguje v téměř úplně stejně jako opožděné metody použité v předchozích příkladech v tomto kurzu `ConvertCollectionToUpperCase` a `AppendString`.  
  
 Jedním rozdílem je, že v tomto případě <xref:System.Linq.Enumerable.Where%2A> metoda iteruje zdrojová kolekce, zjistí, že první položka nepředává predikátu a pak získá další položky, které předávají. Vypočítá pak druhou položku.  
  
 Však základní Rada je stejný: zprostředkující kolekce nejsou materializována, pokud mají být.  
  
 Pokud se používají výrazy dotazů, se převedou na volání standardní operátory dotazu a stejné zásady platí.  
  
 Všechny příklady v této části, které se dotazuje dokumenty používají stejné zásady. Odložené provedení a opožděné vyhodnocení jsou některé základní koncepty, musíte pochopit efektivně používat LINQ (a technologie LINQ to XML).  
  
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
  
## <a name="see-also"></a>Viz také  
 [Kurz: Řetězení dotazy společně (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
