---
title: 'Postupy: projektu nový typ (technologie LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
ms.openlocfilehash: da45c527ef9943cabf207a0b475a8a2114d5c6d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642027"
---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a>Postupy: projektu nový typ (technologie LINQ to XML) (Visual Basic)
Další příklady v této části ukázaly, dotazy, které vracejí výsledky jako <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> z `string`, a <xref:System.Collections.Generic.IEnumerable%601> z `int`. Toto jsou běžné typy výsledků, ale nejsou vhodná pro každý scénář. V mnoha případech můžete své dotazy vrátit <xref:System.Collections.Generic.IEnumerable%601> některé typu.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak k vytváření instancí objektů v `Select` klauzule. Kód nejdřív definuje novou třídu s konstruktor a pak upravením `Select` příkaz tak, aby výraz novou instanci třídy novou třídu.  
  
 Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: typické nákupní objednávka (technologie LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Public Class NameQty  
    Public name As String  
    Public qty As Integer  
    Public Sub New(ByVal n As String, ByVal q As Integer)  
        name = n  
        qty = q  
    End Sub  
End Class  
  
Public Class Program  
    Shared Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
  
        Dim nqList As IEnumerable(Of NameQty) = _  
            From n In po...<Item> _  
            Select New NameQty( _  
                n.<ProductName>.Value, CInt(n.<Quantity>.Value))  
  
        For Each n As NameQty In nqList  
            Console.WriteLine(n.name & ":" & n.qty)  
        Next  
    End Sub  
End Class  
```  
  
 Tento příklad používá `M:System.Xml.Linq.XElement.Element` metoda, která byla zavedená v tématu [postupy: načtení jeden podřízený Element (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md). Také používá k načtení hodnoty prvků, které se vrátí pomocí položky CAST `M:System.Xml.Linq.XElement.Element` metoda.  
  
 Tento příklad vytvoří následující výstup:  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a>Viz také  
 [Projekce a transformace (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
