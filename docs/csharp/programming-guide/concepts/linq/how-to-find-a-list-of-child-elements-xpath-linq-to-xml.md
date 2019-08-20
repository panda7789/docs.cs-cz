---
title: 'Postupy: Najít seznam podřízených elementů (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 7c589dd8-f680-4cdb-9d6a-78d57e2555e8
ms.openlocfilehash: 8a2ddc13a0a48fbe30ce629527149bacaaab3fd1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593671"
---
# <a name="how-to-find-a-list-of-child-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="a27f2-102">Postupy: Najít seznam podřízených elementů (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a27f2-102">How to: Find a List of Child Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="a27f2-103">Toto téma porovnává osu podřízených elementů XPath [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s <xref:System.Xml.Linq.XContainer.Elements%2A> osou.</span><span class="sxs-lookup"><span data-stu-id="a27f2-103">This topic compares the XPath child elements axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>  
  
 <span data-ttu-id="a27f2-104">Výraz XPath je:`./*`</span><span class="sxs-lookup"><span data-stu-id="a27f2-104">The XPath expression is: `./*`</span></span>  
  
## <a name="example"></a><span data-ttu-id="a27f2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a27f2-105">Example</span></span>  
 <span data-ttu-id="a27f2-106">Tento příklad vyhledá všechny podřízené prvky `Address` elementu.</span><span class="sxs-lookup"><span data-stu-id="a27f2-106">This example finds all of the child elements of the `Address` element.</span></span>  
  
 <span data-ttu-id="a27f2-107">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a27f2-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="a27f2-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a27f2-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Street>123 Maple Street</Street>  
<City>Mill Valley</City>  
<State>CA</State>  
<Zip>10999</Zip>  
<Country>USA</Country>  
```  
  