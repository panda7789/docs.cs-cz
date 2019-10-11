---
title: 'Postupy: Vyhledání Potomkových elementů (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e7e2dc9e-bda9-420d-a5b1-4fabf1cca46b
ms.openlocfilehash: 3ee496c1a3e797a8edaf5878d9832583396a851f
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250121"
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="ce205-102">Postupy: Vyhledání Potomkových elementů (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce205-102">How to: Find Descendant Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="ce205-103">Toto téma ukazuje, jak získat odvozené prvky s určitým názvem.</span><span class="sxs-lookup"><span data-stu-id="ce205-103">This topic shows how to get the descendant elements with a particular name.</span></span>  
  
 <span data-ttu-id="ce205-104">Výraz XPath je `//Name`.</span><span class="sxs-lookup"><span data-stu-id="ce205-104">The XPath expression is `//Name`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce205-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce205-105">Example</span></span>  
 <span data-ttu-id="ce205-106">Tento příklad vyhledá všechny následníky s názvem `Name`.</span><span class="sxs-lookup"><span data-stu-id="ce205-106">This example finds all descendants named `Name`.</span></span>  
  
 <span data-ttu-id="ce205-107">Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ce205-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="ce205-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ce205-108">This example produces the following output:</span></span>  
  
```console
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce205-109">Související témata</span><span class="sxs-lookup"><span data-stu-id="ce205-109">See also</span></span>

- [<span data-ttu-id="ce205-110">LINQ to XML pro uživatele XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce205-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
