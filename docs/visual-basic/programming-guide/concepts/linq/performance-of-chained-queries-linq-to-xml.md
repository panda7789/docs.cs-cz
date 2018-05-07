---
title: Výkon zřetězené dotazů (technologie LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: d390fc0e45967cd98697320eb6f61a51cb1c19da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a>Výkon zřetězené dotazů (technologie LINQ to XML) (Visual Basic)
Jednou z nejdůležitějších výhod LINQ (a technologie LINQ to XML) je, že zřetězené dotazy můžete provést i jediný rozsáhlejších, složitějších dotaz.  
  
 Zřetězené dotaz je dotaz, který používá jiný dotaz jako zdroj. Například v následujícím kódu jednoduchý `query2` má `query1` jako svůj zdroj:  
  
```vb  
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))  
  
Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x  
  
Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e  
  
For Each i As var In query2  
    Console.WriteLine("{0}", CInt(i))  
Next  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
4  
```  
  
 Tento dotaz zřetězené poskytuje stejný profil výkonu jako iterace v rámci odkazovaného seznamu.  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A> Má osa v podstatě stejný výkon jako iterace v rámci odkazovaného seznamu. <xref:System.Xml.Linq.XContainer.Elements%2A> je implementovaný jako iterace s odložené provedení. To znamená, že některé činnosti provede kromě iterace v rámci odkazovaného seznamu, jako například přidělování objekt iterator a udržování přehledu o stavu spuštění. Tato práce je možné rozdělit do dvou kategorií: práce, kterou je provést v době je nastavený iterator a práci, kterou se provádí při každé iteraci. Instalační program práce malé, pevné množství práce, a práci při každé iteraci je úměrná počet položek ve zdrojové kolekci.  
  
-   V `query1`, `Where` klauzule způsobí, že dotaz pro volání <xref:System.Linq.Enumerable.Where%2A> metoda. Tato metoda je také implementovaný jako iterace. Instalační program pracovní se skládá z vytvoření instance delegáta, který bude odkazovat výrazu lambda, plus normální instalace pro iterace. Přičemž při každém opakování se nazývá delegát provést predikátu. Instalační program práci a práci při každé iteraci je podobná objem práce při iterace v rámci ose.  
  
-   V `query1`, klauzule select způsobí, že dotaz pro volání <xref:System.Linq.Enumerable.Select%2A> metoda. Tato metoda má stejný profil výkonu jako <xref:System.Linq.Enumerable.Where%2A> metoda.  
  
-   V `query2`, i `Where` klauzule a `Select` klauzule mají stejný profil výkonu jako v `query1`.  
  
 Iterace prostřednictvím `query2` je proto přímo úměrné k počet položek ve zdroji prvního, jinými slovy, lineární doba dotazu.  
  
## <a name="see-also"></a>Viz také  
 [Výkon (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
