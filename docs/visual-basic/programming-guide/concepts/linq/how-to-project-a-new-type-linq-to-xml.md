---
title: 'Postupy: Projektování nového typu (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
ms.openlocfilehash: 48fb82e870a4fc4fa16cfb48a127f364e6d81f13
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396503"
---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a>Postupy: projektování nového typu (LINQ to XML) (Visual Basic)
Další příklady v této části obsahují dotazy, které vracejí výsledky od <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> z `string` a do <xref:System.Collections.Generic.IEnumerable%601> `int` . Jedná se o běžné typy výsledků, ale nejsou vhodné pro všechny scénáře. V mnoha případech budete chtít, aby dotazy vracely <xref:System.Collections.Generic.IEnumerable%601> nějaký jiný typ.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak vytvořit instanci objektů v `Select` klauzuli. Kód nejprve definuje novou třídu s konstruktorem a poté upraví `Select` příkaz tak, aby výraz byl novou instancí nové třídy.  
  
 Tento příklad používá následující dokument XML: [vzorový soubor XML: typická nákupní objednávka (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
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
  
 Tento příklad používá `M:System.Xml.Linq.XElement.Element` metodu, která byla představena v tématu [Postupy: načtení jednoho podřízeného prvku (LINQ to XML) (Visual Basic)](how-to-retrieve-a-single-child-element-linq-to-xml.md). Používá také přetypování k načtení hodnot prvků, které jsou vráceny `M:System.Xml.Linq.XElement.Element` metodou.  
  
 Tento příklad vytvoří následující výstup:  
  
```console  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a>Viz také

- [Projekce a transformace (LINQ to XML) (Visual Basic)](projections-and-transformations-linq-to-xml.md)
