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
# <a name="how-to-find-a-list-of-child-elements-xpath-linq-to-xml-c"></a>Postupy: Najít seznam podřízených elementů (XPath-LINQ to XML) (C#)
Toto téma porovnává osu podřízených elementů XPath [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s <xref:System.Xml.Linq.XContainer.Elements%2A> osou.  
  
 Výraz XPath je:`./*`  
  
## <a name="example"></a>Příklad  
 Tento příklad vyhledá všechny podřízené prvky `Address` elementu.  
  
 V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
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
  
 Tento příklad vytvoří následující výstup:  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Street>123 Maple Street</Street>  
<City>Mill Valley</City>  
<State>CA</State>  
<Zip>10999</Zip>  
<Country>USA</Country>  
```  
  