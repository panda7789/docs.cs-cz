---
title: 'Postupy: vyhledání podřízeného elementu (XPath – LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: adb46c98-a650-42e2-b62d-835920fe8421
ms.openlocfilehash: 122cc269b95a3f35b8eef71e9c7ca1d50af4210b
ms.sourcegitcommit: 869b5832b667915ac4a5dd8c86b1109ed26b6c08
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2018
ms.locfileid: "39332610"
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-visual-basic"></a>Postupy: vyhledání podřízeného elementu (XPath – LINQ to XML) (Visual Basic)
Toto téma srovnává osu XPath podřízený element pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> metody.  
  
 Výraz XPath je `DeliveryNotes`.  
  
## <a name="example"></a>Příklad  
 Tento příklad vyhledá podřízený element `DeliveryNotes`.  
  
 Tento příklad používá následujícího dokumentu XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```vb  
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")  
Dim po As XElement = cpo.Root.<PurchaseOrder>.FirstOrDefault  
  
'LINQ to XML query  
Dim el1 As XElement = po.<DeliveryNotes>.FirstOrDefault  
  
' XPath expression  
Dim el2 As XElement = po.XPathSelectElement("DeliveryNotes")  
' same as "child::DeliveryNotes"  
' same as "./DeliveryNotes"  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="see-also"></a>Viz také  
 [LINQ to XML pro uživatele jazyka XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
