---
title: 'Postupy: vyhledání předcházejících elementů (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
ms.openlocfilehash: d2bd34db7bd839e50ec3e77819230f5f6410b73e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43787115"
---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-c"></a>Postupy: vyhledání předcházejících elementů (XPath – LINQ to XML) (C#)
Toto téma srovnává jazyka XPath `preceding-sibling` osy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] podřízené <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> osy.  
  
 Výraz XPath je:  
  
 `preceding-sibling::*`  
  
 Všimněte si, že výsledky z obou <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> a <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> jsou v pořadí dokumentů.  
  
## <a name="example"></a>Příklad  
 Vyhledá v následujícím příkladu `FullAddress` prvek a poté obnoví předchozí prvky pomocí `preceding-sibling` osy.  
  
 Tento příklad používá následujícího dokumentu XML: [ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
  
 Tento příklad vytvoří následující výstup:  
  
```  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
  
## <a name="see-also"></a>Viz také

- [LINQ to XML pro uživatele jazyka XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
