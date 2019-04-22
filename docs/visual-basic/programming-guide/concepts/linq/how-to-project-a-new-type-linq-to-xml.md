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
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a><span data-ttu-id="bd420-102">Postupy: Projektování nového typu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd420-102">How to: Project a New Type (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="bd420-103">Další příklady v této části ukázaly, dotazy, které vracejí výsledky jako <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> z `string`, a <xref:System.Collections.Generic.IEnumerable%601> z `int`.</span><span class="sxs-lookup"><span data-stu-id="bd420-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="bd420-104">Toto jsou běžné typy výsledků, ale nejsou vhodná pro každý scénář.</span><span class="sxs-lookup"><span data-stu-id="bd420-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="bd420-105">V mnoha případech můžete vrátit dotazech <xref:System.Collections.Generic.IEnumerable%601> nějakého jiného typu.</span><span class="sxs-lookup"><span data-stu-id="bd420-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd420-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="bd420-106">Example</span></span>  
 <span data-ttu-id="bd420-107">Tento příklad ukazuje, jak vytvořit instanci objektů v `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="bd420-107">This example shows how to instantiate objects in the `Select` clause.</span></span> <span data-ttu-id="bd420-108">Kód nejdřív definuje novou třídu s konstruktorem a pak změní `Select` příkaz tak, aby novou instanci třídy nový výraz.</span><span class="sxs-lookup"><span data-stu-id="bd420-108">The code first defines a new class with a constructor, and then modifies the `Select` statement so that the expression is a new instance of the new class.</span></span>  
  
 <span data-ttu-id="bd420-109">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bd420-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="bd420-110">V tomto příkladu `M:System.Xml.Linq.XElement.Element` metodu, která byla zavedena v tématu [jak: Načtení jednoho podřízeného elementu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bd420-110">This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="bd420-111">Také používá k načtení hodnoty prvků, které jsou vráceny pomocí přetypování `M:System.Xml.Linq.XElement.Element` metody.</span><span class="sxs-lookup"><span data-stu-id="bd420-111">It also uses casts to retrieve the values of the elements that are returned by the `M:System.Xml.Linq.XElement.Element` method.</span></span>  
  
 <span data-ttu-id="bd420-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="bd420-112">This example produces the following output:</span></span>  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd420-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd420-113">See also</span></span>

- [<span data-ttu-id="bd420-114">Projekce a transformace (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd420-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
