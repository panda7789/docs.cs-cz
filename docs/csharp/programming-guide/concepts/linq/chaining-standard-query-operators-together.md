---
title: Zřetězení standardních dotazovacích operátorů pohromadě (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: e09b918ab6c33c8e3ccae6f99826dd86f4a2d1e6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487613"
---
# <a name="chaining-standard-query-operators-together-c"></a>Zřetězení standardních dotazovacích operátorů pohromadě (C#)
Toto je poslední téma v [kurzu: Zřetězení dotazů (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) kurzu.  
  
 Také je možné zřetězit standardních operátorů pro dotazování. Například můžete interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operátor a také funguje opožděné způsobem. Žádné mezilehlých výsledků jsou materializovaného tímto plánem.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.Linq.Enumerable.Where%2A> metoda je volána před voláním `ConvertCollectionToUpperCase`. <xref:System.Linq.Enumerable.Where%2A> Metoda funguje v téměř stejným způsobem jako opožděné metod používaných v předchozích příkladech v tomto kurzu `ConvertCollectionToUpperCase` a `AppendString`.  
  
 Jedním rozdílem je, že v tomto případě <xref:System.Linq.Enumerable.Where%2A> metoda prochází dochází k rozdělení kolekce, zjistí, že první položka nepředává predikátu a potom získá další položky, které předávají. Pak bude vrácen druhé položky.  
  
 Základní myšlenka je však stejný: Pokud mají být nejsou vyhodnocena zprostředkující kolekce.  
  
 V případě – výrazy dotazů používají, jsou převedeny na volání do standardních operátorů pro dotazování a stejné zásady platí.  
  
 Všechny příklady v této části, které jsou dotazování na dokumenty Office Open XML používat stejný princip. Odložené provedení a opožděné vyhodnocení jsou některé základní koncepty, musíte porozumět efektivně používat LINQ (a LINQ to XML).  
  
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
  