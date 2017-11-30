---
title: "Postupy: výpočtu pomocných hodnot (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 933a97b2-dfe7-4f4d-94ad-e6e20df84abd
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: eaedaf15318ea9ae521cc070e7cd9a267decf330
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-calculate-intermediate-values-visual-basic"></a><span data-ttu-id="3553a-102">Postupy: výpočtu pomocných hodnot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3553a-102">How to: Calculate Intermediate Values (Visual Basic)</span></span>
<span data-ttu-id="3553a-103">Tento příklad ukazuje způsob výpočtu pomocných hodnot, které mohou být používány třídění, filtrování a výběr.</span><span class="sxs-lookup"><span data-stu-id="3553a-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3553a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3553a-104">Example</span></span>  
 <span data-ttu-id="3553a-105">Následující příklad používá `Let` klauzule.</span><span class="sxs-lookup"><span data-stu-id="3553a-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="3553a-106">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Číselná Data (technologie LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3553a-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="3553a-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3553a-107">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="3553a-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="3553a-108">Example</span></span>  
 <span data-ttu-id="3553a-109">Následující příklad ukazuje stejný dotaz pro formát XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3553a-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="3553a-110">Další informace najdete v tématu [práci s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="3553a-110">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="3553a-111">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Číselná Data v Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="3553a-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="3553a-112">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3553a-112">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a><span data-ttu-id="3553a-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="3553a-113">See Also</span></span>  
 [<span data-ttu-id="3553a-114">Základní dotazy (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3553a-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
