---
title: 'Postupy: Vyhledání následnických elementů (XPath – LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e7e2dc9e-bda9-420d-a5b1-4fabf1cca46b
ms.openlocfilehash: 09f12dca7b6278327394126ffb0950682d285f88
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833396"
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="cd67a-102">Postupy: Vyhledání následnických elementů (XPath – LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd67a-102">How to: Find Descendant Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="cd67a-103">Toto téma ukazuje, jak získat následovnické elementy s určitým názvem.</span><span class="sxs-lookup"><span data-stu-id="cd67a-103">This topic shows how to get the descendant elements with a particular name.</span></span>  
  
 <span data-ttu-id="cd67a-104">Výraz XPath je `//Name`.</span><span class="sxs-lookup"><span data-stu-id="cd67a-104">The XPath expression is `//Name`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd67a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd67a-105">Example</span></span>  
 <span data-ttu-id="cd67a-106">Tento příklad vyhledá všech potomků s názvem `Name`.</span><span class="sxs-lookup"><span data-stu-id="cd67a-106">This example finds all descendants named `Name`.</span></span>  
  
 <span data-ttu-id="cd67a-107">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cd67a-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
      Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = po...<Name>  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("//Name")  
  
If (list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count()) Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="cd67a-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="cd67a-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd67a-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd67a-109">See also</span></span>

- [<span data-ttu-id="cd67a-110">LINQ to XML pro uživatele jazyka XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd67a-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
