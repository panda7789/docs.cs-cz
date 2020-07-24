---
title: Jak promítnout anonymní typ (C#)
description: Naučte se, jak projektovat dotaz anonymnímu typu v jazyce C#. Použití anonymního typu může být snazší než vytváření nového typu pro použití pouze krátce.
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 6598796a4ba95362340f2551b1da6ac6d857eaae
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104634"
---
# <a name="how-to-project-an-anonymous-type-c"></a>Jak promítnout anonymní typ (C#)
V některých případech můžete chtít vytvořit dotaz na nový typ, i když víte, že tento typ budete používat jenom krátce. Je to mnoho dalších práce pro vytvoření nového typu pouze k použití v projekci. Efektivnější přístup v tomto případě je projekt na anonymní typ. Anonymní typy umožňují definovat třídu a pak deklarovat a inicializovat objekt této třídy, aniž by bylo nutné zadat název třídy.  
  
 Anonymní typy jsou implementace matematického konceptu *řazené kolekce členů*v jazyce C#. Matematická pojem řazené kolekce členů pochází z sekvence Single, Double, Triple, čtyřnásobná, quintuple, n-Tuple. Odkazuje na konečnou sekvenci objektů, každého konkrétního typu. Někdy se označuje jako seznam párů název/hodnota. Například obsah adresy v [ukázkovém souboru XML: typický dokument XML s nákupní objednávkou (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) může být vyjádřen následujícím způsobem:  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Když vytváříte instanci anonymního typu, je vhodné ji považovat za vytváření řazené kolekce členů objednávky n. Pokud napíšete dotaz, který v klauzuli vytvoří řazenou kolekci členů `select` , dotaz vrátí `IEnumerable` kolekci řazené kolekce členů.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je `select` klauzule projekt anonymního typu. Příklad následně používá `var` k vytvoření `IEnumerable` objektu. V rámci `foreach` smyčky se proměnná iterace stala instancí anonymního typu vytvořeného ve výrazu dotazu.  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
  