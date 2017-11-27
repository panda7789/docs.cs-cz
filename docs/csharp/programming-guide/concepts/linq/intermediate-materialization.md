---
title: "Zprostředkující Materialization (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 46d347921e24bc5504c69534d7b5c087818a6c7f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="intermediate-materialization-c"></a>Zprostředkující Materialization (C#)
Pokud si nejste opatrní, v některých situacích můžete výrazně změnit profilem paměti a výkon vaší aplikace tak, že předčasné materialization kolekcí v dotazech. Některé standardní operátory dotazu způsobit materialization jejich zdrojové kolekci před je jediným elementem. Například <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> nejprve iteruje jeho celý zdrojový kolekce, pak seřadí všechny položky a nakonec vypočítá první položka. To znamená, že je nákladné získat první položka uspořádanou kolekci; Každá položka po tomto datu není nákladné. To dává smysl: by bylo možné pro tento dotaz operátor neurčí jinak.  
  
## <a name="example"></a>Příklad  
 Tento příklad mění předchozí příklad. `AppendString` Volání metod <xref:System.Linq.Enumerable.ToList%2A> před iterace v rámci zdroji. To způsobí, že materialization.  
  
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
  
 V tomto příkladu můžete uvidíte, že volání <xref:System.Linq.Enumerable.ToList%2A> způsobí, že `AppendString` výčet jeho celý zdrojový před je první položka. Pokud zdroj byly velké pole, by to výrazně změnit paměti profil aplikace.  
  
 Standardní operátory dotazu lze také zřetězen dohromady. To ukazuje poslední téma v tomto kurzu.  
  
-   [Řetězení standardní operátory dotazu společně (C#)](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a>Viz také  
 [Kurz: Řetězení dotazy společně (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
