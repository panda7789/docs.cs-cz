---
title: 'Postupy: řízení typu projekce'
ms.date: 07/20/2015
ms.assetid: a0171276-0b46-4817-aee5-a8d5191b12fe
ms.openlocfilehash: b9620e7dab7abecce5161c5e7f50b187dbb3a71e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351091"
---
# <a name="how-to-control-the-type-of-a-projection-visual-basic"></a><span data-ttu-id="8a678-102">Postupy: řízení typu projekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a678-102">How to: Control the Type of a Projection (Visual Basic)</span></span>
<span data-ttu-id="8a678-103">Projekcí je proces pořízení jedné sady dat, její filtrování, změna jejího tvaru a dokonce i změna jejího typu.</span><span class="sxs-lookup"><span data-stu-id="8a678-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="8a678-104">Většina výrazů dotazů provádí projekce.</span><span class="sxs-lookup"><span data-stu-id="8a678-104">Most query expressions perform projections.</span></span> <span data-ttu-id="8a678-105">Většina výrazů dotazů zobrazených v této části vyhodnocuje <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, ale můžete řídit typ projekce pro vytváření kolekcí jiných typů.</span><span class="sxs-lookup"><span data-stu-id="8a678-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="8a678-106">V tomto tématu se dozvíte, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="8a678-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a678-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a678-107">Example</span></span>  
 <span data-ttu-id="8a678-108">Následující příklad definuje nový typ `Customer`.</span><span class="sxs-lookup"><span data-stu-id="8a678-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="8a678-109">Výraz dotazu potom vytvoří instanci nových objektů `Customer` v klauzuli `Select`.</span><span class="sxs-lookup"><span data-stu-id="8a678-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="8a678-110">To způsobí, že typ výrazu dotazu bude <xref:System.Collections.Generic.IEnumerable%601> `Customer`.</span><span class="sxs-lookup"><span data-stu-id="8a678-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="8a678-111">Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8a678-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Public Class Customer  
    Private customerIDValue As String  
    Public Property CustomerID() As String  
        Get  
            Return customerIDValue  
        End Get  
        Set(ByVal value As String)  
            customerIDValue = value  
        End Set  
    End Property  
  
    Private companyNameValue As String  
    Public Property CompanyName() As String  
        Get  
            Return companyNameValue  
        End Get  
        Set(ByVal value As String)  
            companyNameValue = value  
        End Set  
    End Property  
  
    Private contactNameValue As String  
    Public Property ContactName() As String  
        Get  
            Return contactNameValue  
        End Get  
        Set(ByVal value As String)  
            contactNameValue = value  
        End Set  
    End Property  
  
    Public Sub New(ByVal customerID As String, _  
                   ByVal companyName As String, _  
                   ByVal contactName As String)  
        CustomerIDValue = customerID  
        CompanyNameValue = companyName  
        ContactNameValue = contactName  
    End Sub  
  
    Public Overrides Function ToString() As String  
        Return String.Format("{0}:{1}:{2}", Me.CustomerID, Me.CompanyName, Me.ContactName)  
    End Function  
End Class  
  
Sub Main()  
    Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
    Dim custList As IEnumerable(Of Customer) = _  
        From el In custOrd.<Customers>.<Customer> _  
        Select New Customer( _  
            el.@<CustomerID>, _  
            el.<CompanyName>.Value, _  
            el.<ContactName>.Value _  
        )  
    For Each cust In custList  
        Console.WriteLine(cust)  
    Next  
End Sub  
```  
  
 <span data-ttu-id="8a678-112">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8a678-112">This code produces the following output:</span></span>  
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a678-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a678-113">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
- [<span data-ttu-id="8a678-114">Projekce a transformace (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a678-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
