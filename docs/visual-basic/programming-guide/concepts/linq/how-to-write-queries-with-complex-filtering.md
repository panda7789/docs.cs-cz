---
title: "Postupy: zápis dotazů s komplexní filtrování (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 15ed0dcf87ad05b1da984aca494d28c1b19eb685
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a>Postupy: zápis dotazů s komplexní filtrování (Visual Basic)
Někdy budete chtít zapisovat XML dotazů LINQ s komplexní filtry. Například můžete chtít najít všechny elementy, které mají podřízený element s určitým názvem a hodnotou. Toto téma poskytuje příklad zápisu dotaz s komplexní filtrování.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak najít všechny `PurchaseOrder` prvky, které podřízený `Address` element, který má `Type` atribut rovno "Přesouvání" a podřízená `State` element rovno "NY". Používá vnořený dotaz v `Where` klauzuli a `Any` vrátí operátor `True` Pokud kolekce obsahuje všechny elementy v ní.  
  
 Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: více nákupních objednávek (technologie LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
 Další informace o `Any` operátor, najdete v části [operace kvantifikátoru (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).  
  
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
  
 Tento kód vytvoří následující výstup:  
  
```  
99505  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro formát XML, který je v oboru názvů. Další informace najdete v tématu [práci s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: více nákupních objednávek v Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
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
  
 Tento kód vytvoří následující výstup:  
  
```  
99505  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [Základní dotazy (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [Vlastnost osy podřízeného souboru XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [Vlastnost osy atributu XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)  
 [Vlastnost hodnoty XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [Operace projekce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
 [Operace kvantifikátoru (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
