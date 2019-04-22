---
title: 'Postupy: Načtení kolekce elementů (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 2269f9de-8fb9-4666-b8a1-a4e754fa6a81
ms.openlocfilehash: 53572ac3c80e012b95527d32da28c8685cd8cfd3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833623"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-visual-basic"></a><span data-ttu-id="9e2d5-102">Postupy: Načtení kolekce elementů (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e2d5-102">How to: Retrieve a Collection of Elements (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="9e2d5-103">Toto téma ukazuje, <xref:System.Xml.Linq.XContainer.Elements%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9e2d5-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="9e2d5-104">Tato metoda načte kolekci podřízených elementů elementu.</span><span class="sxs-lookup"><span data-stu-id="9e2d5-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e2d5-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="9e2d5-105">Example</span></span>  
 <span data-ttu-id="9e2d5-106">Tento příklad provede iteraci podřízených elementů `purchaseOrder` elementu.</span><span class="sxs-lookup"><span data-stu-id="9e2d5-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="9e2d5-107">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9e2d5-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim childElements As IEnumerable(Of XElement)  
childElements = _  
    From el In po.Elements() _  
    Select el  
For Each el As XElement In childElements  
    Console.WriteLine("Name: " & el.Name.ToString())  
Next  
```  
  
 <span data-ttu-id="9e2d5-108">Tento příklad vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="9e2d5-108">This example produces the following output.</span></span>  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e2d5-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e2d5-109">See also</span></span>

- [<span data-ttu-id="9e2d5-110">Osy LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e2d5-110">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
