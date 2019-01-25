---
title: 'Postupy: Načtení kolekce elementů (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 2269f9de-8fb9-4666-b8a1-a4e754fa6a81
ms.openlocfilehash: b5602e327128dd886b31d2863e089480f97b3aad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642761"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-visual-basic"></a><span data-ttu-id="b3bb5-102">Postupy: Načtení kolekce elementů (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3bb5-102">How to: Retrieve a Collection of Elements (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="b3bb5-103">Toto téma ukazuje, <xref:System.Xml.Linq.XContainer.Elements%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b3bb5-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="b3bb5-104">Tato metoda načte kolekci podřízených elementů elementu.</span><span class="sxs-lookup"><span data-stu-id="b3bb5-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3bb5-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3bb5-105">Example</span></span>  
 <span data-ttu-id="b3bb5-106">Tento příklad provede iteraci podřízených elementů `purchaseOrder` elementu.</span><span class="sxs-lookup"><span data-stu-id="b3bb5-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="b3bb5-107">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b3bb5-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="b3bb5-108">Tento příklad vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="b3bb5-108">This example produces the following output.</span></span>  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3bb5-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3bb5-109">See also</span></span>
- [<span data-ttu-id="b3bb5-110">Osy LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3bb5-110">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
