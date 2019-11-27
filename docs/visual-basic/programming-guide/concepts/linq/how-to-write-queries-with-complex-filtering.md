---
title: 'Postupy: zápis dotazů se složitým filtrováním'
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: 28e84b7785948e9d50c08438494b89c906ab8505
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344460"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a>Postupy: zápis dotazů se složitým filtrováním (Visual Basic)
Někdy budete chtít zapisovat LINQ to XML dotazy se složitými filtry. Například může být nutné najít všechny prvky, které mají podřízený element s určitým názvem a hodnotou. Toto téma poskytuje příklad zápisu dotazu se složitým filtrováním.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak najít všechny `PurchaseOrder` prvky, které mají podřízený element `Address`, který má atribut `Type` roven "dodávání" a podřízený element `State` roven "NY". Používá vnořený dotaz v klauzuli `Where` a operátor `Any` vrací `True`, pokud má kolekce nějaké prvky.  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
 Další informace o operátoru `Any` naleznete v tématu [operace kvantifikátoru (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrders.xml")  
Dim purchaseOrders As IEnumerable(Of XElement) = _  
    From el In root.<PurchaseOrder> _  
    Where _  
        (From add In el.<Address> _  
        Where _  
             add.@Type = "Shipping" And _  
             add.<State>.Value = "NY" _  
        Select add) _  
    .Any() _  
    Select el  
For Each el As XElement In purchaseOrders  
    Console.WriteLine(el.@PurchaseOrderNumber)  
Next  
```  
  
 Tento kód generuje následující výstup:  
  
```console  
99505  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek v oboru názvů](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim purchaseOrders As IEnumerable(Of XElement) = _  
            From el In root.<aw:PurchaseOrder> _  
            Where _  
                (From add In el.<aw:Address> _  
                Where _  
                     add.@aw:Type = "Shipping" And _  
                     add.<aw:State>.Value = "NY" _  
                Select add) _  
            .Any() _  
            Select el  
        For Each el As XElement In purchaseOrders  
            Console.WriteLine(el.@aw:PurchaseOrderNumber)  
        Next  
    End Sub  
End Module  
```  
  
 Tento kód generuje následující výstup:  
  
```console  
99505  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Základní dotazy (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [Vlastnost osy podřízeného XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [Vlastnost osy atributu XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [Vlastnost hodnoty XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Operace projekce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [Operace kvantifikátoru (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
