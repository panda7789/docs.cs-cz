---
title: 'How to: Calculate Intermediate Values'
ms.date: 07/20/2015
ms.assetid: 933a97b2-dfe7-4f4d-94ad-e6e20df84abd
ms.openlocfilehash: 167293a9af94a0991505b6e9edf225e6d3382bee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353356"
---
# <a name="how-to-calculate-intermediate-values-visual-basic"></a><span data-ttu-id="7d883-102">How to: Calculate Intermediate Values (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d883-102">How to: Calculate Intermediate Values (Visual Basic)</span></span>
<span data-ttu-id="7d883-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span><span class="sxs-lookup"><span data-stu-id="7d883-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d883-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d883-104">Example</span></span>  
 <span data-ttu-id="7d883-105">The following example uses the `Let` clause.</span><span class="sxs-lookup"><span data-stu-id="7d883-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="7d883-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7d883-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim extensions As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
    Where extension > 25 _  
    Order By extension _  
    Select extension  
For Each ex As Decimal In extensions  
    Console.WriteLine(ex)  
Next  
```  
  
 <span data-ttu-id="7d883-107">This code produces the following output:</span><span class="sxs-lookup"><span data-stu-id="7d883-107">This code produces the following output:</span></span>  
  
```console  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="7d883-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d883-108">Example</span></span>  
 <span data-ttu-id="7d883-109">The following example shows the same query for XML that is in a namespace.</span><span class="sxs-lookup"><span data-stu-id="7d883-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="7d883-110">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7d883-110">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="7d883-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="7d883-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns="http://www.adatum.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim extensions As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
            Where extension > 25 _  
            Order By extension _  
            Select extension  
        For Each ex As Decimal In extensions  
            Console.WriteLine(ex)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="7d883-112">This code produces the following output:</span><span class="sxs-lookup"><span data-stu-id="7d883-112">This code produces the following output:</span></span>  
  
```console  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d883-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d883-113">See also</span></span>

- [<span data-ttu-id="7d883-114">Basic Queries (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d883-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
