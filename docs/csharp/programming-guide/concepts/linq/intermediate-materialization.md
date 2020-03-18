---
title: Zprostředkující materializace (C#)
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: af1eb7df7da02d8e72fc102cda4ee5f329dc7974
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253166"
---
# <a name="intermediate-materialization-c"></a>Zprostředkující materializace (C#)
Pokud nejste opatrní, v některých situacích můžete výrazně změnit paměť a profil výkonu aplikace tím, že způsobí předčasné materializace kolekcí v dotazech. Některé operátory standardní dotaz způsobit materializaci jejich zdrojové kolekce před získávání jeden prvek. Například <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> nejprve iterates prostřednictvím celé jeho zdrojové kolekce, pak seřadí všechny položky a nakonec výnosy první položku. To znamená, že je nákladné získat první položku objednané kolekce; každá položka poté není drahá. To dává smysl: Pro tento operátor dotazu by bylo nemožné provést jinak.  
  
## <a name="example"></a>Příklad  
 Tento příklad změní předchozí příklad. Metoda `AppendString` volá <xref:System.Linq.Enumerable.ToList%2A> před iterace prostřednictvím zdroje. To způsobí materializaci.  
  
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
        // the following statement materializes the source collection in a List<T>  
        // before iterating through it  
        foreach (string str in source.ToList())  
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
ToUpper: source >def<  
ToUpper: source >ghi<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 V tomto příkladu uvidíte, <xref:System.Linq.Enumerable.ToList%2A> že `AppendString` volání způsobí výčet celého zdroje před získávání první položky. Pokud by zdrojem bylo velké pole, výrazně by to změnilo profil paměti aplikace.  
  
 Standardní operátory dotazů lze také zřetězit dohromady. Poslední téma v tomto kurzu ilustruje toto.  
  
- [Zřetězení operátorů standardních dotazů dohromady (C#)](./chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a>Viz také

- [Kurz: Řetězení dotazů dohromady (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
