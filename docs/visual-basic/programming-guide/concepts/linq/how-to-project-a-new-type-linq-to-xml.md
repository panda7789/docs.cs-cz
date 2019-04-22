---
title: 'Postupy: Projektování nového typu (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
ms.openlocfilehash: a94180705674c8aee3ce45607f89fdbba1c873b7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834657"
---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a>Postupy: Projektování nového typu (LINQ to XML) (Visual Basic)
Další příklady v této části ukázaly, dotazy, které vracejí výsledky jako <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> z `string`, a <xref:System.Collections.Generic.IEnumerable%601> z `int`. Toto jsou běžné typy výsledků, ale nejsou vhodná pro každý scénář. V mnoha případech můžete vrátit dotazech <xref:System.Collections.Generic.IEnumerable%601> nějakého jiného typu.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak vytvořit instanci objektů v `Select` klauzuli. Kód nejdřív definuje novou třídu s konstruktorem a pak změní `Select` příkaz tak, aby novou instanci třídy nový výraz.  
  
 Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
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
  
 V tomto příkladu `M:System.Xml.Linq.XElement.Element` metodu, která byla zavedena v tématu [jak: Načtení jednoho podřízeného elementu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md). Také používá k načtení hodnoty prvků, které jsou vráceny pomocí přetypování `M:System.Xml.Linq.XElement.Element` metody.  
  
 Tento příklad vytvoří následující výstup:  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a>Viz také:

- [Projekce a transformace (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
