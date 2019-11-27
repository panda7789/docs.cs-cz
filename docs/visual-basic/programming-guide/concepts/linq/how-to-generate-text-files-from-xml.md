---
title: 'Postupy: generování textových souborů z XML'
ms.date: 07/20/2015
ms.assetid: 3b33f191-4abe-4419-b81b-3cb81d9a317f
ms.openlocfilehash: b30596df1a490d78d1333c688a23ed4ab30bcb82
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344565"
---
# <a name="how-to-generate-text-files-from-xml-visual-basic"></a><span data-ttu-id="96fe3-102">Postupy: generování textových souborů z formátu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96fe3-102">How to: Generate Text Files from XML (Visual Basic)</span></span>
<span data-ttu-id="96fe3-103">Tento příklad ukazuje, jak vygenerovat soubor hodnot oddělených čárkami (CSV) ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="96fe3-103">This example shows how to generate a comma-separated values (CSV) file from an XML file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96fe3-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="96fe3-104">Example</span></span>  
 <span data-ttu-id="96fe3-105">Verze Visual Basic používá procedurální kód pro agregaci kolekce řetězců do jediného řetězce.</span><span class="sxs-lookup"><span data-stu-id="96fe3-105">The Visual Basic version uses procedural code to aggregate the collection of strings into a single string.</span></span>  
  
 <span data-ttu-id="96fe3-106">Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="96fe3-106">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim strCollection As IEnumerable(Of String) = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select _  
        String.Format("{0},{1},{2},{3},{4},{5},{6},{7},{8},{9}{10}", _  
            el.@CustomerID, _  
            el.<CompanyName>.Value, _  
            el.<ContactName>.Value, _  
            el.<ContactTitle>.Value, _  
            el.<Phone>.Value, _  
            el.<FullAddress>.<Address>.Value, _  
            el.<FullAddress>.<City>.Value, _  
            el.<FullAddress>.<Region>.Value, _  
            el.<FullAddress>.<PostalCode>.Value, _  
            el.<FullAddress>.<Country>.Value, _  
            Environment.NewLine _  
        )  
Dim sb As StringBuilder = New StringBuilder()  
For Each str As String In strCollection  
    sb.Append(str)  
Next  
Console.WriteLine(sb.ToString())  
```  
  
 <span data-ttu-id="96fe3-107">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="96fe3-107">This code produces the following output:</span></span>  
  
```console  
GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA  
HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA  
LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA  
LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA  
```  
  
## <a name="see-also"></a><span data-ttu-id="96fe3-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96fe3-108">See also</span></span>

- [<span data-ttu-id="96fe3-109">Projekce a transformace (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96fe3-109">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
