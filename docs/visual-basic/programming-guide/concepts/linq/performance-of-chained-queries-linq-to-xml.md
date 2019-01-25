---
title: Výkon zřetězených dotazů (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 8a4893a000bc80fa703e7d47aa5d73f02b95a8ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601867"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a>Výkon zřetězených dotazů (LINQ to XML) (Visual Basic)
Jednou z vašich nejdůležitějších výhod LINQ (a LINQ to XML) je, že zřetězených dotazů můžete provádět i pomocí jediného dotazu větší a složitější.  
  
 Zřetězené dotaz je dotaz, který používá jiný dotaz jako zdroj. Například v následujícím jednoduchého kódu `query2` má `query1` jako svůj zdroj:  
  
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
  
 Tento dotaz zřetězené poskytuje stejný profil výkonu jako iterace propojeného seznamu.  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A> Osy je v podstatě stejný výkon jako iterace propojeného seznamu. <xref:System.Xml.Linq.XContainer.Elements%2A> je implementován jako iterátor s odloženého provedení. To znamená, že nemusí nějakou práci navíc iterace propojeného seznamu, například přidělování objekt iterátoru a sledování stavu spuštění. Tuto práci je možné rozdělit do dvou kategorií: práce, která se provádí v době iterátor nastaven a práce, která se provádí při každé iteraci. Nastavení je malý, pevné množství práce a práci při každé iteraci je přímo úměrný počtu položek v kolekci zdroje.  
  
-   V `query1`, `Where` klauzule dotazu pro volání způsobí, že <xref:System.Linq.Enumerable.Where%2A> metody. Tato metoda je také implementováno jako iterátor. Nastavení se skládá z vytvoření instance delegáta, který bude odkazovat na výraz lambda, a navíc normální instalace iterátor. S každou iterací delegáta je volána k provedení predikát. Instalační program práce a práce při každé iteraci je podobný práci během iterace na ose.  
  
-   V `query1`, klauzule select způsobí, že dotaz tak, aby volání <xref:System.Linq.Enumerable.Select%2A> metody. Tato metoda má stejný profil výkonu, jako <xref:System.Linq.Enumerable.Where%2A> metody.  
  
-   V `query2`, obojí `Where` klauzule a `Select` klauzule mají stejný profil výkonu jako v `query1`.  
  
 Iterace přes `query2` tedy přímo úměrné k počet položek ve zdroji prvního dotazu jinými slovy, lineárním čase.  
  
## <a name="see-also"></a>Viz také:
- [Výkon (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
