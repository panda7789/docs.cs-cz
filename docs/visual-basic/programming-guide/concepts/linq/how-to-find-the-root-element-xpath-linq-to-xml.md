---
title: 'Postupy: Vyhledání kořenového elementu (XPath – LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 72c3aed5-9522-4454-a876-2070aad13f2e
ms.openlocfilehash: 112be85e8af8fbe31f62ef91db04de72a3793082
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483668"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="b8643-102">Postupy: Vyhledání kořenového elementu (XPath – LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8643-102">How to: Find the Root Element (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="b8643-103">Toto téma ukazuje, jak získat kořenový element, jejichž výraz XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b8643-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="b8643-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="b8643-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="b8643-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b8643-105">Example</span></span>  
 <span data-ttu-id="b8643-106">Tento příklad vyhledá kořenový element.</span><span class="sxs-lookup"><span data-stu-id="b8643-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="b8643-107">Tento příklad používá následujícího dokumentu XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b8643-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim el1 As XElement = po.Root  
  
' XPath expression  
Dim el2 As XElement = po.XPathSelectElement("/PurchaseOrders")  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1.Name)  
```  
  
 <span data-ttu-id="b8643-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b8643-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8643-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8643-109">See Also</span></span>  
 [<span data-ttu-id="b8643-110">LINQ to XML pro uživatele jazyka XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8643-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
