---
title: 'Postupy: řazení elementů'
ms.date: 07/20/2015
ms.assetid: c2c09279-6c8a-482e-8e71-b1453a815052
ms.openlocfilehash: 84d791a73c27b9acf1eaa5a5e4a31d6798a6c76d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341537"
---
# <a name="how-to-sort-elements-visual-basic"></a><span data-ttu-id="22656-102">Postupy: řazení elementů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22656-102">How to: Sort Elements (Visual Basic)</span></span>
<span data-ttu-id="22656-103">Tento příklad ukazuje, jak napsat dotaz, který seřadí jeho výsledky.</span><span class="sxs-lookup"><span data-stu-id="22656-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22656-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="22656-104">Example</span></span>  
 <span data-ttu-id="22656-105">Tento příklad používá následující dokument XML: [ukázkový soubor XML: numerická data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="22656-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="22656-106">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="22656-106">This code produces the following output:</span></span>  
  
```console  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="22656-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="22656-107">Example</span></span>  
 <span data-ttu-id="22656-108">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="22656-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="22656-109">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="22656-109">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="22656-110">Tento příklad používá následující dokument XML: [ukázkový soubor XML: numerická data v oboru názvů](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="22656-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="22656-111">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="22656-111">This code produces the following output:</span></span>  
  
```console  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="22656-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22656-112">See also</span></span>

- [<span data-ttu-id="22656-113">Řazení dat</span><span class="sxs-lookup"><span data-stu-id="22656-113">Sorting Data</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)
- [<span data-ttu-id="22656-114">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22656-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
