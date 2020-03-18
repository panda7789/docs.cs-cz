---
title: Jak promítat anonymní typ (C#)
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 7797c8bfb12943af1ce7f975b170bf002aa7d6fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345724"
---
# <a name="how-to-project-an-anonymous-type-c"></a>Jak promítat anonymní typ (C#)
V některých případech můžete chtít promítnout dotaz na nový typ, i když víte, že tento typ budete používat pouze na krátkou dobu. Je to hodně práce navíc vytvořit nový typ jen pro použití v projekci. Efektivnější přístup v tomto případě je projekt na anonymní typ. Anonymní typy umožňují definovat třídu, pak deklarovat a inicializovat objekt této třídy, aniž by třídy název.  
  
 Anonymní typy jsou implementace C# matematického konceptu *řazené kolekce členů*. The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple. Odkazuje na konečnou sekvenci objektů, každý z určitého typu. Někdy se tomu říká seznam párů název/hodnota. Například obsah adresy v [ukázkovém souboru XML: Typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML dokument může být vyjádřen a to to toto:  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Když vytvoříte instanci anonymního typu, je vhodné si ji myslet jako vytvoření řazené kolekce členů pořadí n. Pokud napíšete dotaz, který vytvoří `select` řazenou `IEnumerable` kolekce členů v klauzuli, dotaz vrátí n-tice.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu klauzule `select` projekty anonymní typ. Příklad pak `var` používá k `IEnumerable` vytvoření objektu. V `foreach` rámci smyčky se iterace proměnná stane instanci anonymního typu vytvořeného ve výrazu dotazu.  
  
 Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML).](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)  
  
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
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  