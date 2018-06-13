---
title: Výkon zřetězené dotazů (technologie LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: dca2fa37a18209c5970172cb084151a58ea4ebc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336362"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a>Výkon zřetězené dotazů (technologie LINQ to XML) (C#)
Jednou z nejdůležitějších výhod LINQ (a technologie LINQ to XML) je, že zřetězené dotazy můžete provést i jediný rozsáhlejších, složitějších dotaz.  
  
 Zřetězené dotaz je dotaz, který používá jiný dotaz jako zdroj. Například v následujícím kódu jednoduchý `query2` má `query1` jako svůj zdroj:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    new XElement("Child", 3),  
    new XElement("Child", 4)  
);  
  
var query1 = from x in root.Elements("Child")  
             where (int)x >= 3  
             select x;  
  
var query2 = from e in query1  
             where (int)e % 2 == 0  
             select e;  
  
foreach (var i in query2)  
    Console.WriteLine("{0}", (int)i);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
4  
```  
  
 Tento dotaz zřetězené poskytuje stejný profil výkonu jako iterace v rámci odkazovaného seznamu.  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A> Má osa v podstatě stejný výkon jako iterace v rámci odkazovaného seznamu. <xref:System.Xml.Linq.XContainer.Elements%2A> je implementovaný jako iterace s odložené provedení. To znamená, že některé činnosti provede kromě iterace v rámci odkazovaného seznamu, jako například přidělování objekt iterator a udržování přehledu o stavu spuštění. Tato práce je možné rozdělit do dvou kategorií: práce, kterou je provést v době je nastavený iterator a práci, kterou se provádí při každé iteraci. Instalační program práce malé, pevné množství práce, a práci při každé iteraci je úměrná počet položek ve zdrojové kolekci.  
  
-   V `query1`, `where` klauzule způsobí, že dotaz pro volání <xref:System.Linq.Enumerable.Where%2A> metoda. Tato metoda je také implementovaný jako iterace. Instalační program pracovní se skládá z vytvoření instance delegáta, který bude odkazovat výrazu lambda, plus normální instalace pro iterace. Přičemž při každém opakování se nazývá delegát provést predikátu. Instalační program práci a práci při každé iteraci je podobná objem práce při iterace v rámci ose.  
  
-   V `query1`, klauzule select způsobí, že dotaz pro volání <xref:System.Linq.Enumerable.Select%2A> metoda. Tato metoda má stejný profil výkonu jako <xref:System.Linq.Enumerable.Where%2A> metoda.  
  
-   V `query2`, i `where` klauzule a `select` klauzule mají stejný profil výkonu jako v `query1`.  
  
 Iterace prostřednictvím `query2` je proto přímo úměrné k počet položek ve zdroji prvního, jinými slovy, lineární doba dotazu. Odpovídající příklad jazyka Visual Basic by měla mít stejný profil výkonu.  
  
 Další informace o iterátory najdete v tématu [yield](../../../../csharp/language-reference/keywords/yield.md).  
  
 Podrobnější kurz řetězení dotazy společně, najdete v části [kurz: řetězení dotazy společně](http://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c).  
  
## <a name="see-also"></a>Viz také  
 [Výkon (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
