---
title: 'Postupy: vyhledání seznamu podřízených elementů (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 2868abfd-9f7b-412a-9cb5-f643f0fed146
ms.openlocfilehash: aab185cd4c157c7ee671418368668d46b4bb2a4a
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72249978"
---
# <a name="how-to-find-a-list-of-child-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="7b807-102">Postupy: vyhledání seznamu podřízených elementů (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b807-102">How to: Find a List of Child Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="7b807-103">Toto téma porovnává osu podřízených elementů XPath s osou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A>.</span><span class="sxs-lookup"><span data-stu-id="7b807-103">This topic compares the XPath child elements axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>  
  
 <span data-ttu-id="7b807-104">Výraz XPath je: `./*`</span><span class="sxs-lookup"><span data-stu-id="7b807-104">The XPath expression is: `./*`</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b807-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b807-105">Example</span></span>  
 <span data-ttu-id="7b807-106">Tento příklad vyhledá všechny podřízené prvky elementu `Address`.</span><span class="sxs-lookup"><span data-stu-id="7b807-106">This example finds all of the child elements of the `Address` element.</span></span>  
  
 <span data-ttu-id="7b807-107">Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7b807-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")  
Dim po As XElement = cpo.Root.<PurchaseOrder>.<Address>.FirstOrDefault  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = po.Elements()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("./*")  
  
If (list1.Count() = list2.Count()) AndAlso _  
    (list1.Intersect(list2).Count() = list1.Count()) Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="7b807-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7b807-108">This example produces the following output:</span></span>  
  
```console
Results are identical  
<Name>Ellen Adams</Name>  
<Street>123 Maple Street</Street>  
<City>Mill Valley</City>  
<State>CA</State>  
<Zip>10999</Zip>  
<Country>USA</Country>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b807-109">Související témata</span><span class="sxs-lookup"><span data-stu-id="7b807-109">See also</span></span>

- [<span data-ttu-id="7b807-110">LINQ to XML pro uživatele XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b807-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
