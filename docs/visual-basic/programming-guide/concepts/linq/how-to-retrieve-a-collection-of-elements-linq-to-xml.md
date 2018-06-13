---
title: 'Postupy: načtení kolekci elementů (technologie LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 2269f9de-8fb9-4666-b8a1-a4e754fa6a81
ms.openlocfilehash: 7ebc33ec8d1901ecb795f63b2fd9812d1acba347
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640167"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-visual-basic"></a>Postupy: načtení kolekci elementů (technologie LINQ to XML) (Visual Basic)
Toto téma ukazuje <xref:System.Xml.Linq.XContainer.Elements%2A> metoda. Tato metoda načte kolekci podřízených elementů elementu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu prochází podřízených elementů `purchaseOrder` elementu.  
  
 Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: typické nákupní objednávka (technologie LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
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
  
 Tento příklad vytvoří následující výstup.  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to XML osy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
