---
title: 'Postupy: načtení jednoho podřízeného elementu (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
ms.openlocfilehash: 2e89df700c505eca9d1c91634e4cce8594a1d599
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347547"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a>Postupy: načtení jednoho podřízeného elementu (LINQ to XML) (Visual Basic)
Toto téma vysvětluje, jak načíst jeden podřízený prvek s názvem podřízeného prvku. Pokud znáte název podřízeného prvku a že existuje pouze jeden prvek, který má tento název, může být vhodné načíst pouze jeden prvek namísto kolekce.  
  
 Metoda <xref:System.Xml.Linq.XContainer.Element%2A> vrací první podřízenou <xref:System.Xml.Linq.XElement> se zadaným <xref:System.Xml.Linq.XName>.  
  
 Pokud chcete načíst jeden podřízený prvek v Visual Basic, společný přístup je použít vlastnost XML a poté načíst první prvek pomocí notace Array indexer.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití metody <xref:System.Xml.Linq.XContainer.Element%2A>. Tento příklad převezme strom XML s názvem `po` a vyhledá první prvek s názvem `Comment`.  
  
 Visual Basic příklad ukazuje použití notace indexeru pole k načtení jednoho prvku.  
  
 Tento příklad používá následující dokument XML: [vzorový soubor XML: typická nákupní objednávka (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný kód pro XML, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: typická nákupní objednávka v oboru názvů](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim e As XElement = po.<aw:DeliveryNotes>(0)  
        Console.WriteLine(e)  
    End Sub  
End Module  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML osy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
