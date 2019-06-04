---
title: 'Postupy: Projektování anonymního typu (C#)'
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 68b008d70474c927a7911dc77e60afb634035b77
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485124"
---
# <a name="how-to-project-an-anonymous-type-c"></a>Postupy: Projektování anonymního typu (C#)
V některých případech můžete chtít dotaz na nový typ projektu i v případě, že víte, že použijete tento typ se jenom na krátkou dobu. Je hodně práce navíc k vytvoření nového typu pouze pro použití v projekci. V tomto případě je efektivnější přístup k projektu anonymního typu. Anonymní typy umožňují definovat třídu, pak deklarovat a inicializovat objekt této třídy bez názvu třídy.  
  
 Anonymní typy jsou implementace jazyka C# matematické konceptu *řazené kolekce členů*. Matematický výraz řazené kolekce členů, pochází z pořadí jeden, double, triple, čtyřikrát, pětkrát, n řazené kolekce členů. Odkazuje na konečnou sekvenci objektů, každý z určitého typu. To se říká se jim seznam dvojic název/hodnota. Například obsah adresy [ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) dokument XML může být vyjádřen takto:  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Když vytvoříte instanci anonymního typu, je vhodné si ho představit jako vytvoření n-tice n pořadí. Pokud píšete dotaz, který vytvoří řazenou kolekci členů v `select` klauzule, dotaz vrátí `IEnumerable` řazené kolekce členů.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `select` klauzule projekty anonymního typu. Příklad poté použije `var` vytvořit `IEnumerable` objektu. V rámci `foreach` smyčky, iterační proměnná stane instanci anonymního typu vytvořené ve výrazu dotazu.  
  
 Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
  
 Tento kód vytvoří následující výstup:  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  