---
title: 'Postupy: řazení elementy (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c2c09279-6c8a-482e-8e71-b1453a815052
ms.openlocfilehash: 868f3eb448393e5c06a37ab68431620638e9dc35
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642087"
---
# <a name="how-to-sort-elements-visual-basic"></a>Postupy: řazení elementy (Visual Basic)
Tento příklad ukazuje, jak napsat dotaz, který seřadí své výsledky.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Číselná Data (technologie LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim prices As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let price = Convert.ToDecimal(el.<Price>.Value) _  
    Order By (price) _  
    Select price  
For Each el As Decimal In prices  
    Console.WriteLine(el)  
Next  
```  
  
 Tento kód vytvoří následující výstup:  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro formát XML, který je v oboru názvů. Další informace najdete v tématu [práci s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Číselná Data v Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim prices As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let price = Convert.ToDecimal(el.<Price>.Value) _  
            Order By (price) _  
            Select price  
        For Each el As Decimal In prices  
            Console.WriteLine(el)  
        Next  
    End Sub  
End Module  
```  
  
 Tento kód vytvoří následující výstup:  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a>Viz také  
 [Řazení dat](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
 [Základní dotazy (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
