---
title: 'Postupy: projektu anonymní typ (C#)'
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 6ecb29c59d16b64b1dfb7018a2d22ae81242ee81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320674"
---
# <a name="how-to-project-an-anonymous-type-c"></a>Postupy: projektu anonymní typ (C#)
V některých případech můžete chtít projektu dotaz pro nový typ, i když víte, že použijete tento typ se pouze na krátkou dobu. Je velké množství práce navíc k vytvoření nového typu jenom pro použití v projekci. V takovém případě má efektivnější přístup projekt anonymního typu. Anonymní typy umožňují definovat třídu, pak deklarovat a inicializovat objekt třídy, bez nutnosti poskytnutí název třídy.  
  
 Anonymní typy jsou implementace C# matematickém koncept *řazené kolekce členů*. Matematický výraz řazené kolekce členů, pochází z pořadí jednoho, double, triple, čtyřikrát, pětkrát, n řazené kolekce členů. Odkazuje na konečné pořadí objektů, každý z konkrétního typu. To se někdy říká seznam dvojic název hodnota. Například obsah adresy [ukázkový soubor XML: typické nákupní objednávka (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) dokumentu XML může být vyjádřena takto:  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Když vytvoříte instanci anonymního typu, je vhodné si ho představit jako vytváření pořadí n řazené kolekce členů. Pokud píšete dotaz, který vytvoří řazené kolekce členů v `select` klauzule, dotaz vrátí `IEnumerable` řazené kolekce členů.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `select` klauzule projekty anonymního typu. V příkladu se pak použije `var` vytvořit `IEnumerable` objektu. V rámci `foreach` smyčky, proměnné iterace stane instanci anonymního typu vytvořen ve výrazu dotazu.  
  
 Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Zákazníci a objednávky (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
  
## <a name="see-also"></a>Viz také  
 [Projekce a transformace (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
