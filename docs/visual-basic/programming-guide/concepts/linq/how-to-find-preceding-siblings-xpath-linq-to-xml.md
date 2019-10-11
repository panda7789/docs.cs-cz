---
title: 'Postupy: Vyhledání předcházejících položek na stejné úrovni (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 59055718-d0a7-4db3-8901-18dd33587703
ms.openlocfilehash: 1ad57c1b6f06843bd757257c8ecda637ad0e71b6
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250092"
---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="d2fb5-102">Postupy: Vyhledání předcházejících položek na stejné úrovni (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2fb5-102">How to: Find Preceding Siblings (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="d2fb5-103">Toto téma porovnává osu XPath `preceding-sibling` na ose [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] podřízené <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d2fb5-103">This topic compares the XPath `preceding-sibling` axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] child <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> axis.</span></span>  
  
 <span data-ttu-id="d2fb5-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="d2fb5-104">The XPath expression is:</span></span>  
  
 `preceding-sibling::*`  
  
 <span data-ttu-id="d2fb5-105">Všimněte si, že výsledky obou <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> a <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> jsou v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="d2fb5-105">Note that the results of both <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> and <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> are in document order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2fb5-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2fb5-106">Example</span></span>  
 <span data-ttu-id="d2fb5-107">Následující příklad vyhledá prvek `FullAddress` a potom načte předchozí prvky pomocí osy `preceding-sibling`.</span><span class="sxs-lookup"><span data-stu-id="d2fb5-107">The following example finds the `FullAddress` element, and then retrieves the previous elements using the `preceding-sibling` axis.</span></span>  
  
 <span data-ttu-id="d2fb5-108">Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d2fb5-108">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim co As XElement = XElement.Load("CustomersOrders.xml")  
Dim add As XElement = co.<Customers>.<Customer>. _  
        <FullAddress>.FirstOrDefault  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = add.ElementsBeforeSelf()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = add.XPathSelectElements("preceding-sibling::*")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list2  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="d2fb5-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d2fb5-109">This example produces the following output:</span></span>  
  
```console
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d2fb5-110">Související témata</span><span class="sxs-lookup"><span data-stu-id="d2fb5-110">See also</span></span>

- [<span data-ttu-id="d2fb5-111">LINQ to XML pro uživatele XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2fb5-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
