---
title: 'Postupy: Projekt anonymního typu (C#)'
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 3ed14ae6e7bc4b84ae9dc416b76e37443b831c73
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253511"
---
# <a name="how-to-project-an-anonymous-type-c"></a>Postupy: Projekt anonymního typu (C#)
V některých případech můžete chtít vytvořit dotaz na nový typ, i když víte, že tento typ budete používat jenom krátce. Je to mnoho dalších práce pro vytvoření nového typu pouze k použití v projekci. Efektivnější přístup v tomto případě je projekt na anonymní typ. Anonymní typy umožňují definovat třídu a pak deklarovat a inicializovat objekt této třídy, aniž by bylo nutné zadat název třídy.  
  
 Anonymní typy jsou C# implementace matematického konceptu *řazené kolekce členů*. Matematická pojem řazené kolekce členů pochází z sekvence Single, Double, Triple, čtyřnásobná, quintuple, n-Tuple. Odkazuje na konečnou sekvenci objektů, každého konkrétního typu. Někdy se označuje jako seznam párů název/hodnota. Například obsah adresy v [ukázkovém souboru XML: Typický dokument XML s nákupní objednávkou (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) může být vyjádřený takto:  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Když vytváříte instanci anonymního typu, je vhodné ji považovat za vytváření řazené kolekce členů objednávky n. Pokud napíšete dotaz, který v `select` klauzuli vytvoří řazenou kolekci členů, dotaz `IEnumerable` vrátí kolekci řazené kolekce členů.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je `select` klauzule projekt anonymního typu. Příklad následně používá `var` k `IEnumerable` vytvoření objektu. V rámci `foreach` smyčky se proměnná iterace stala instancí anonymního typu vytvořeného ve výrazu dotazu.  
  
 V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
```csharp  
XElement custOrd = XElement.Load("CustomersOrders.xml");  
var custList =  
    from el in custOrd.Element("Customers").Elements("Customer")  
    select new {  
        CustomerID = (string)el.Attribute("CustomerID"),  
        CompanyName = (string)el.Element("CompanyName"),  
        ContactName = (string)el.Element("ContactName")  
    };  
foreach (var cust in custList)  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName);  
```  
  
 Tento kód generuje následující výstup:  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  