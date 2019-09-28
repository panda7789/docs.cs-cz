---
title: 'Postupy: Vypočítat mezilehlé hodnoty (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 933a97b2-dfe7-4f4d-94ad-e6e20df84abd
ms.openlocfilehash: 63067c42da37d71ad0fc5488c68d296ac7589aec
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71352905"
---
# <a name="how-to-calculate-intermediate-values-visual-basic"></a><span data-ttu-id="77b67-102">Postupy: Vypočítat mezilehlé hodnoty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77b67-102">How to: Calculate Intermediate Values (Visual Basic)</span></span>
<span data-ttu-id="77b67-103">Tento příklad ukazuje, jak vypočítat mezilehlé hodnoty, které lze použít při řazení, filtrování a výběr.</span><span class="sxs-lookup"><span data-stu-id="77b67-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77b67-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="77b67-104">Example</span></span>  
 <span data-ttu-id="77b67-105">Následující příklad používá klauzuli `Let`.</span><span class="sxs-lookup"><span data-stu-id="77b67-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="77b67-106">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Číselná data (LINQ to XML) ](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="77b67-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="77b67-107">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="77b67-107">This code produces the following output:</span></span>  
  
```console  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="77b67-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="77b67-108">Example</span></span>  
 <span data-ttu-id="77b67-109">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="77b67-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="77b67-110">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="77b67-110">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="77b67-111">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Číselná data v oboru názvů @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="77b67-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="77b67-112">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="77b67-112">This code produces the following output:</span></span>  
  
```console  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a><span data-ttu-id="77b67-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77b67-113">See also</span></span>

- [<span data-ttu-id="77b67-114">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77b67-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
