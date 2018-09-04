---
title: Přechodná Materializace (C#)
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 56c4bb57a931362b3e14f6a8da917ae6907565d6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516540"
---
# <a name="intermediate-materialization-c"></a>Přechodná Materializace (C#)
Pokud si nejste pozor, v některých situacích je možné výrazně změnit profil paměti a výkonu vaší aplikace tak, že předčasné materializace kolekce v dotazech. Některé operátory standardního dotazu způsobit materializace kolekce zdroje před získávání jeden element. Například <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> nejprve Iteruje přes kolekci jeho celý zdrojový pak seřadí všechny položky a nakonec vrací první položky. To znamená, že se jedná o nákladné získat první položku uspořádanou kolekci; Každá položka po tomto datu není nákladné. To dává smysl: by bylo možné pro daný operátor dotazu postupovat jinak.  
  
## <a name="example"></a>Příklad  
 Tento příklad upravuje předchozí příklad. `AppendString` Volání metody <xref:System.Linq.Enumerable.ToList%2A> před provede iterace přes zdrojové. To způsobí, že materializace.  
  
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
  
 Tento příklad vytvoří následující výstup:  
  
```  
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
  
 V tomto příkladu vidíte, že volání <xref:System.Linq.Enumerable.ToList%2A> způsobí, že `AppendString` výčet jeho celý zdrojový před získávání první položky. Pokud zdroj velkého pole, by to výrazně změnit paměti profilu aplikace.  
  
 Také je možné zřetězit standardních operátorů pro dotazování. V posledním tématu v tomto kurzu ukazuje to.  
  
-   [Zřetězení standardních dotazovacích operátorů pohromadě (C#)](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a>Viz také

- [Kurz: Zřetězení dotazů společně (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
