---
title: 'Postupy: řazení elementů na více klíčů (C#)'
ms.date: 07/20/2015
ms.assetid: 3b2760b6-d607-4ac7-b784-5c6524e2a0e0
ms.openlocfilehash: 14c5e0282ce3018424461870e1d2c59814fc3f40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320571"
---
# <a name="how-to-sort-elements-on-multiple-keys-c"></a><span data-ttu-id="cb2c6-102">Postupy: řazení elementů na více klíčů (C#)</span><span class="sxs-lookup"><span data-stu-id="cb2c6-102">How to: Sort Elements on Multiple Keys (C#)</span></span>
<span data-ttu-id="cb2c6-103">Toto téma ukazuje, jak řadit na několik klíčů.</span><span class="sxs-lookup"><span data-stu-id="cb2c6-103">This topic shows how to sort on multiple keys.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb2c6-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="cb2c6-104">Example</span></span>  
 <span data-ttu-id="cb2c6-105">V tomto příkladu výsledky jsou seřazené první podle přesouvání PSČ, potom k datu objednávky.</span><span class="sxs-lookup"><span data-stu-id="cb2c6-105">In this example, the results are ordered first by the shipping postal code, then by the order date.</span></span>  
  
 <span data-ttu-id="cb2c6-106">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Zákazníci a objednávky (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="cb2c6-106">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
var sortedElements =  
    from c in co.Element("Orders").Elements("Order")  
    orderby (string)c.Element("ShipInfo").Element("ShipPostalCode"),  
            (DateTime)c.Element("OrderDate")  
    select new {  
        CustomerID = (string)c.Element("CustomerID"),  
        EmployeeID = (string)c.Element("EmployeeID"),  
        ShipPostalCode = (string)c.Element("ShipInfo").Element("ShipPostalCode"),  
        OrderDate = (DateTime)c.Element("OrderDate")  
    };  
foreach (var r in sortedElements)  
    Console.WriteLine("CustomerID:{0} EmployeeID:{1} ShipPostalCode:{2} OrderDate:{3:d}",  
        r.CustomerID, r.EmployeeID, r.ShipPostalCode, r.OrderDate);  
```  
  
 <span data-ttu-id="cb2c6-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="cb2c6-107">This code produces the following output:</span></span>  
  
```  
CustomerID:LETSS EmployeeID:1 ShipPostalCode:94117 OrderDate:6/25/1997  
CustomerID:LETSS EmployeeID:8 ShipPostalCode:94117 OrderDate:10/27/1997  
CustomerID:LETSS EmployeeID:6 ShipPostalCode:94117 OrderDate:11/10/1997  
CustomerID:LETSS EmployeeID:4 ShipPostalCode:94117 OrderDate:2/12/1998  
CustomerID:GREAL EmployeeID:6 ShipPostalCode:97403 OrderDate:5/6/1997  
CustomerID:GREAL EmployeeID:8 ShipPostalCode:97403 OrderDate:7/4/1997  
CustomerID:GREAL EmployeeID:1 ShipPostalCode:97403 OrderDate:7/31/1997  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:7/31/1997  
CustomerID:GREAL EmployeeID:6 ShipPostalCode:97403 OrderDate:9/4/1997  
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:9/25/1997  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:1/6/1998  
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:3/9/1998  
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:4/7/1998  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:4/22/1998  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:4/30/1998  
CustomerID:HUNGC EmployeeID:3 ShipPostalCode:97827 OrderDate:12/6/1996  
CustomerID:HUNGC EmployeeID:1 ShipPostalCode:97827 OrderDate:12/25/1996  
CustomerID:HUNGC EmployeeID:3 ShipPostalCode:97827 OrderDate:1/15/1997  
CustomerID:HUNGC EmployeeID:4 ShipPostalCode:97827 OrderDate:7/16/1997  
CustomerID:HUNGC EmployeeID:8 ShipPostalCode:97827 OrderDate:9/8/1997  
CustomerID:LAZYK EmployeeID:1 ShipPostalCode:99362 OrderDate:3/21/1997  
CustomerID:LAZYK EmployeeID:8 ShipPostalCode:99362 OrderDate:5/22/1997  
```  
  
## <a name="example"></a><span data-ttu-id="cb2c6-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="cb2c6-108">Example</span></span>  
 <span data-ttu-id="cb2c6-109">Následující příklad ukazuje stejný dotaz pro formát XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cb2c6-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="cb2c6-110">Další informace najdete v tématu [práci s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="cb2c6-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="cb2c6-111">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Zákazníci a objednávky v Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="cb2c6-111">This example uses the following XML document: [Sample XML File: Customers and Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-in-a-namespace.md).</span></span>  
  
```csharp  
XElement co = XElement.Load("CustomersOrdersInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
var sortedElements =  
    from c in co.Element(aw + "Orders").Elements(aw + "Order")  
    orderby (string)c.Element(aw + "ShipInfo").Element(aw + "ShipPostalCode"),  
            (DateTime)c.Element(aw + "OrderDate")  
    select new  
    {  
        CustomerID = (string)c.Element(aw + "CustomerID"),  
        EmployeeID = (string)c.Element(aw + "EmployeeID"),  
        ShipPostalCode = (string)c.Element(aw + "ShipInfo").Element(aw + "ShipPostalCode"),  
        OrderDate = (DateTime)c.Element(aw + "OrderDate")  
    };  
foreach (var r in sortedElements)  
    Console.WriteLine("CustomerID:{0} EmployeeID:{1} ShipPostalCode:{2} OrderDate:{3:d}",  
        r.CustomerID, r.EmployeeID, r.ShipPostalCode, r.OrderDate);  
```  
  
 <span data-ttu-id="cb2c6-112">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="cb2c6-112">This code produces the following output:</span></span>  
  
```  
CustomerID:LETSS EmployeeID:1 ShipPostalCode:94117 OrderDate:6/25/1997  
CustomerID:LETSS EmployeeID:8 ShipPostalCode:94117 OrderDate:10/27/1997  
CustomerID:LETSS EmployeeID:6 ShipPostalCode:94117 OrderDate:11/10/1997  
CustomerID:LETSS EmployeeID:4 ShipPostalCode:94117 OrderDate:2/12/1998  
CustomerID:GREAL EmployeeID:6 ShipPostalCode:97403 OrderDate:5/6/1997  
CustomerID:GREAL EmployeeID:8 ShipPostalCode:97403 OrderDate:7/4/1997  
CustomerID:GREAL EmployeeID:1 ShipPostalCode:97403 OrderDate:7/31/1997  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:7/31/1997  
CustomerID:GREAL EmployeeID:6 ShipPostalCode:97403 OrderDate:9/4/1997  
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:9/25/1997  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:1/6/1998  
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:3/9/1998  
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:4/7/1998  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:4/22/1998  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:4/30/1998  
CustomerID:HUNGC EmployeeID:3 ShipPostalCode:97827 OrderDate:12/6/1996  
CustomerID:HUNGC EmployeeID:1 ShipPostalCode:97827 OrderDate:12/25/1996  
CustomerID:HUNGC EmployeeID:3 ShipPostalCode:97827 OrderDate:1/15/1997  
CustomerID:HUNGC EmployeeID:4 ShipPostalCode:97827 OrderDate:7/16/1997  
CustomerID:HUNGC EmployeeID:8 ShipPostalCode:97827 OrderDate:9/8/1997  
CustomerID:LAZYK EmployeeID:1 ShipPostalCode:99362 OrderDate:3/21/1997  
CustomerID:LAZYK EmployeeID:8 ShipPostalCode:99362 OrderDate:5/22/1997  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb2c6-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb2c6-113">See Also</span></span>  
 [<span data-ttu-id="cb2c6-114">Základní dotazy (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="cb2c6-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
