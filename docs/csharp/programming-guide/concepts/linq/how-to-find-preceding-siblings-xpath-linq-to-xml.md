---
title: Jak najít předchozí na stejné úrovni (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
ms.openlocfilehash: 08fc2073f76f37bd0381a05a7969d1c7748d6252
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141055"
---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-c"></a>Jak najít předchozí na stejné úrovni (XPath-LINQ to XML) (C#)
Toto téma porovnává `preceding-sibling` osu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> XPath s podřízenou osou.  
  
 Výraz XPath je:  
  
 `preceding-sibling::*`  
  
 Všimněte si, <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> že <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> výsledky obou a jsou v pořadí dokumentů.  
  
## <a name="example"></a>Příklad  
 Následující příklad najde `FullAddress` prvek a potom načte předchozí `preceding-sibling` prvky pomocí osy.  
  
 Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML).](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
  
XElement add = co.Element("Customers").Element("Customer").Element("FullAddress");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = add.ElementsBeforeSelf();  
  
// XPath expression  
IEnumerable<XElement> list2 = add.XPathSelectElements("preceding-sibling::*");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list2)  
    Console.WriteLine(el);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```output  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
