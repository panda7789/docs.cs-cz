---
title: 'Postupy: Výpočet mezilehlých hodnot (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 933a97b2-dfe7-4f4d-94ad-e6e20df84abd
ms.openlocfilehash: cb619784d487ae12b1fb8bb3adc97acb0f767455
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827039"
---
# <a name="how-to-calculate-intermediate-values-visual-basic"></a><span data-ttu-id="cbd61-102">Postupy: Výpočet mezilehlých hodnot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbd61-102">How to: Calculate Intermediate Values (Visual Basic)</span></span>
<span data-ttu-id="cbd61-103">Tento příklad ukazuje způsob výpočtu pomocných hodnot použitých v řazení, filtrování a vyberete.</span><span class="sxs-lookup"><span data-stu-id="cbd61-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbd61-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="cbd61-104">Example</span></span>  
 <span data-ttu-id="cbd61-105">V následujícím příkladu `Let` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="cbd61-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="cbd61-106">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Číselná Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cbd61-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="cbd61-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="cbd61-107">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="cbd61-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="cbd61-108">Example</span></span>  
 <span data-ttu-id="cbd61-109">Následující příklad ukazuje stejný dotaz pro soubor XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cbd61-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="cbd61-110">Další informace najdete v tématu [práce s názvovými prostory XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="cbd61-110">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="cbd61-111">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Číselná Data ve Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="cbd61-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="cbd61-112">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="cbd61-112">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a><span data-ttu-id="cbd61-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cbd61-113">See also</span></span>

- [<span data-ttu-id="cbd61-114">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbd61-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
