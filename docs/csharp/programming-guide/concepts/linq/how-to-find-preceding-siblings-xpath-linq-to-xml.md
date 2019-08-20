---
title: 'Postupy: Najde předchozí položky na stejné úrovni (XPath-LINQ to XMLC#) ().'
ms.date: 07/20/2015
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
ms.openlocfilehash: d47a2d72efd8891108999d5576da52eb2b6285b1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593432"
---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-c"></a><span data-ttu-id="dc19b-102">Postupy: Najde předchozí položky na stejné úrovni (XPath-LINQ to XMLC#) ().</span><span class="sxs-lookup"><span data-stu-id="dc19b-102">How to: Find Preceding Siblings (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="dc19b-103">Toto téma porovnává osu `preceding-sibling` XPath [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s podřízenou <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> osou.</span><span class="sxs-lookup"><span data-stu-id="dc19b-103">This topic compares the XPath `preceding-sibling` axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] child <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> axis.</span></span>  
  
 <span data-ttu-id="dc19b-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="dc19b-104">The XPath expression is:</span></span>  
  
 `preceding-sibling::*`  
  
 <span data-ttu-id="dc19b-105">Všimněte si, že výsledky obou <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> a <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> jsou v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="dc19b-105">Note that the results of both <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> and <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> are in document order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc19b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="dc19b-106">Example</span></span>  
 <span data-ttu-id="dc19b-107">Následující příklad vyhledá `FullAddress` prvek a potom načte předchozí prvky `preceding-sibling` pomocí osy.</span><span class="sxs-lookup"><span data-stu-id="dc19b-107">The following example finds the `FullAddress` element, and then retrieves the previous elements using the `preceding-sibling` axis.</span></span>  
  
 <span data-ttu-id="dc19b-108">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="dc19b-108">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="dc19b-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="dc19b-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
