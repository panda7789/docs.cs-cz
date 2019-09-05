---
title: 'Postupy: Najít seznam podřízených elementů (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 7c589dd8-f680-4cdb-9d6a-78d57e2555e8
ms.openlocfilehash: 63b0fec504ff8424e9e96318c46191a150b72f46
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253838"
---
# <a name="how-to-find-a-list-of-child-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="2cd82-102">Postupy: Najít seznam podřízených elementů (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2cd82-102">How to: Find a List of Child Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="2cd82-103">Toto téma porovnává osu podřízených elementů XPath [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s <xref:System.Xml.Linq.XContainer.Elements%2A> osou.</span><span class="sxs-lookup"><span data-stu-id="2cd82-103">This topic compares the XPath child elements axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>  
  
 <span data-ttu-id="2cd82-104">Výraz XPath je:`./*`</span><span class="sxs-lookup"><span data-stu-id="2cd82-104">The XPath expression is: `./*`</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cd82-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="2cd82-105">Example</span></span>  
 <span data-ttu-id="2cd82-106">Tento příklad vyhledá všechny podřízené prvky `Address` elementu.</span><span class="sxs-lookup"><span data-stu-id="2cd82-106">This example finds all of the child elements of the `Address` element.</span></span>  
  
 <span data-ttu-id="2cd82-107">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2cd82-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument cpo = XDocument.Load("PurchaseOrders.xml");  
XElement po = cpo.Root.Element("PurchaseOrder").Element("Address");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = po.Elements();  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements("./*");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="2cd82-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="2cd82-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Name>Ellen Adams</Name>  
<Street>123 Maple Street</Street>  
<City>Mill Valley</City>  
<State>CA</State>  
<Zip>10999</Zip>  
<Country>USA</Country>  
```  
