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
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a><span data-ttu-id="a5c10-102">Postupy: projektování nového typu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5c10-102">How to: Project a New Type (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="a5c10-103">Další příklady v této části obsahují dotazy, které vracejí výsledky od <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> z `string` a do <xref:System.Collections.Generic.IEnumerable%601> `int` .</span><span class="sxs-lookup"><span data-stu-id="a5c10-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="a5c10-104">Jedná se o běžné typy výsledků, ale nejsou vhodné pro všechny scénáře.</span><span class="sxs-lookup"><span data-stu-id="a5c10-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="a5c10-105">V mnoha případech budete chtít, aby dotazy vracely <xref:System.Collections.Generic.IEnumerable%601> nějaký jiný typ.</span><span class="sxs-lookup"><span data-stu-id="a5c10-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5c10-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5c10-106">Example</span></span>  
 <span data-ttu-id="a5c10-107">Tento příklad ukazuje, jak vytvořit instanci objektů v `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a5c10-107">This example shows how to instantiate objects in the `Select` clause.</span></span> <span data-ttu-id="a5c10-108">Kód nejprve definuje novou třídu s konstruktorem a poté upraví `Select` příkaz tak, aby výraz byl novou instancí nové třídy.</span><span class="sxs-lookup"><span data-stu-id="a5c10-108">The code first defines a new class with a constructor, and then modifies the `Select` statement so that the expression is a new instance of the new class.</span></span>  
  
 <span data-ttu-id="a5c10-109">Tento příklad používá následující dokument XML: [vzorový soubor XML: typická nákupní objednávka (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a5c10-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="a5c10-110">Tento příklad používá `M:System.Xml.Linq.XElement.Element` metodu, která byla představena v tématu [Postupy: načtení jednoho podřízeného prvku (LINQ to XML) (Visual Basic)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a5c10-110">This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="a5c10-111">Používá také přetypování k načtení hodnot prvků, které jsou vráceny `M:System.Xml.Linq.XElement.Element` metodou.</span><span class="sxs-lookup"><span data-stu-id="a5c10-111">It also uses casts to retrieve the values of the elements that are returned by the `M:System.Xml.Linq.XElement.Element` method.</span></span>  
  
 <span data-ttu-id="a5c10-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a5c10-112">This example produces the following output:</span></span>  
  
```console  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5c10-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5c10-113">See also</span></span>

- [<span data-ttu-id="a5c10-114">Projekce a transformace (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5c10-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)
