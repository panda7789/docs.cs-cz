---
title: 'Postupy: Načtení jednoho podřízeného elementu (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
ms.openlocfilehash: 52b626cfa7227312b1251a6fc998112268564084
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521917"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a>Postupy: Načtení jednoho podřízeného elementu (LINQ to XML) (Visual Basic)
Toto téma vysvětluje, jak načíst jeden podřízený prvek, název podřízeného prvku. Pokud znáte název podřízeného prvku a že je pouze jeden element, který má tento název, může být vhodné k načtení pouze jednoho prvku, namísto kolekce.  
  
 <xref:System.Xml.Linq.XContainer.Element%2A> Metoda vrací prvního podřízeného <xref:System.Xml.Linq.XElement> se zadaným <xref:System.Xml.Linq.XName>.  
  
 Pokud chcete načíst jeden podřízený prvek v jazyce Visual Basic, běžným přístupem je použít vlastnost XML a pak načíst první prvek pomocí notace indexeru pole.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití <xref:System.Xml.Linq.XContainer.Element%2A> metody. V tomto příkladu má stromové struktuře XML s názvem `po` a vyhledá první prvek s názvem `Comment`.  
  
 Příklad jazyka Visual Basic zobrazí notaci indexeru pro načtení jednoho elementu pole.  
  
 Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
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
 Následující příklad ukazuje stejný kód pro soubor XML, který je v oboru názvů. Další informace najdete v tématu [práce s názvovými prostory XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Typická nákupní objednávka v Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
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
- [Osy LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
