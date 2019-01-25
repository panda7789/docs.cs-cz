---
title: Výkon zřetězených dotazů (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: e099d4d725a0603df61f5e308ce9897feec0af29
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677314"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a>Výkon zřetězených dotazů (LINQ to XML) (C#)
Jednou z vašich nejdůležitějších výhod LINQ (a LINQ to XML) je, že zřetězených dotazů můžete provádět i pomocí jediného dotazu větší a složitější.  
  
 Zřetězené dotaz je dotaz, který používá jiný dotaz jako zdroj. Například v následujícím jednoduchého kódu `query2` má `query1` jako svůj zdroj:  
  
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
  
 Tento dotaz zřetězené poskytuje stejný profil výkonu jako iterace propojeného seznamu.  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A> Osy je v podstatě stejný výkon jako iterace propojeného seznamu. <xref:System.Xml.Linq.XContainer.Elements%2A> je implementován jako iterátor s odloženého provedení. To znamená, že nemusí nějakou práci navíc iterace propojeného seznamu, například přidělování objekt iterátoru a sledování stavu spuštění. Tuto práci je možné rozdělit do dvou kategorií: práce, která se provádí v době iterátor nastaven a práce, která se provádí při každé iteraci. Nastavení je malý, pevné množství práce a práci při každé iteraci je přímo úměrný počtu položek v kolekci zdroje.  
  
-   V `query1`, `where` klauzule dotazu pro volání způsobí, že <xref:System.Linq.Enumerable.Where%2A> metody. Tato metoda je také implementováno jako iterátor. Nastavení se skládá z vytvoření instance delegáta, který bude odkazovat na výraz lambda, a navíc normální instalace iterátor. S každou iterací delegáta je volána k provedení predikát. Instalační program práce a práce při každé iteraci je podobný práci během iterace na ose.  
  
-   V `query1`, klauzule select způsobí, že dotaz tak, aby volání <xref:System.Linq.Enumerable.Select%2A> metody. Tato metoda má stejný profil výkonu, jako <xref:System.Linq.Enumerable.Where%2A> metody.  
  
-   V `query2`, obojí `where` klauzule a `select` klauzule mají stejný profil výkonu jako v `query1`.  
  
 Iterace přes `query2` tedy přímo úměrné k počet položek ve zdroji prvního dotazu jinými slovy, lineárním čase. Odpovídající příklad jazyka Visual Basic by měla mít stejný profil výkonu.  
  
 Další informace o iterátorech naleznete v tématu [yield](../../../../csharp/language-reference/keywords/yield.md).  
  
 Podrobnější kurz na zřetězení dotazů, najdete v tématu [kurzu: Zřetězení dotazů](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).  
  
## <a name="see-also"></a>Viz také:

- [Výkon (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
