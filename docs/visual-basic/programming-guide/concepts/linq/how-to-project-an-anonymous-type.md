---
title: 'Postupy: Projektování anonymního typu'
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: c486fbd7ee8ae917cd0ccf57e2b04e472784b11d
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810557"
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a>Postupy: projektování anonymního typu (Visual Basic)
V některých případech můžete chtít vytvořit dotaz na nový typ, i když víte, že tento typ budete používat jenom krátce. Je to mnoho dalších práce pro vytvoření nového typu pouze k použití v projekci. Efektivnější přístup v tomto případě je projekt na anonymní typ. Anonymní typy umožňují definovat třídu a pak deklarovat a inicializovat objekt této třídy, aniž by bylo nutné zadat název třídy.  
  
 Anonymní typy jsou implementace matematického konceptu *řazené kolekce členů*v jazyce C#. Matematická pojem řazené kolekce členů pochází z sekvence Single, Double, Triple, čtyřnásobná, quintuple, n-Tuple. Odkazuje na konečnou sekvenci objektů, každého konkrétního typu. Někdy se označuje jako seznam párů název/hodnota. Například obsah adresy v [ukázkovém souboru XML: typický dokument XML s nákupní objednávkou (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md) může být vyjádřen následujícím způsobem:  
  
```
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Když vytváříte instanci anonymního typu, je vhodné ji považovat za vytváření řazené kolekce členů objednávky n. Pokud napíšete dotaz, který v klauzuli vytvoří řazenou kolekci členů `Select` , dotaz vrátí `IEnumerable` kolekci řazené kolekce členů.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je `Select` klauzule projekt anonymního typu. Příklad následně používá `Dim` k vytvoření `IEnumerable` objektu. V rámci `For Each` smyčky se proměnná iterace stala instancí anonymního typu vytvořeného ve výrazu dotazu.  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim custList = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select New With { _  
        .CustomerID = el.@<CustomerID>, _  
        .CompanyName = el.<CompanyName>.Value, _  
        .ContactName = el.<ContactName>.Value _  
    }  
For Each cust In custList  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)  
Next  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Viz také

- [Projekce a transformace (LINQ to XML) (Visual Basic)](projections-and-transformations-linq-to-xml.md)
