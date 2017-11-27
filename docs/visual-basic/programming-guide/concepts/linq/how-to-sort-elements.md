---
title: "Postupy: řazení elementy (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2c09279-6c8a-482e-8e71-b1453a815052
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f8664a011538269de06ed30dd7367e8f85c510df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-elements-visual-basic"></a><span data-ttu-id="83082-102">Postupy: řazení elementy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83082-102">How to: Sort Elements (Visual Basic)</span></span>
<span data-ttu-id="83082-103">Tento příklad ukazuje, jak napsat dotaz, který seřadí své výsledky.</span><span class="sxs-lookup"><span data-stu-id="83082-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83082-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="83082-104">Example</span></span>  
 <span data-ttu-id="83082-105">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Číselná Data (technologie LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="83082-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim prices As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let price = Convert.ToDecimal(el.<Price>.Value) _  
    Order By (price) _  
    Select price  
For Each el As Decimal In prices  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="83082-106">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="83082-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="83082-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="83082-107">Example</span></span>  
 <span data-ttu-id="83082-108">Následující příklad ukazuje stejný dotaz pro formát XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="83082-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="83082-109">Další informace najdete v tématu [práci s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="83082-109">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="83082-110">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Číselná Data v Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="83082-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim prices As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let price = Convert.ToDecimal(el.<Price>.Value) _  
            Order By (price) _  
            Select price  
        For Each el As Decimal In prices  
            Console.WriteLine(el)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="83082-111">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="83082-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="83082-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="83082-112">See Also</span></span>  
 [<span data-ttu-id="83082-113">Řazení dat</span><span class="sxs-lookup"><span data-stu-id="83082-113">Sorting Data</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
 [<span data-ttu-id="83082-114">Základní dotazy (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83082-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
