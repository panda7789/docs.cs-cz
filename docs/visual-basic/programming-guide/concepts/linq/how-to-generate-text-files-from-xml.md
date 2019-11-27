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
# <a name="how-to-generate-text-files-from-xml-visual-basic"></a>Postupy: generování textových souborů z formátu XML (Visual Basic)
Tento příklad ukazuje, jak vygenerovat soubor hodnot oddělených čárkami (CSV) ze souboru XML.  
  
## <a name="example"></a>Příklad  
 Verze Visual Basic používá procedurální kód pro agregaci kolekce řetězců do jediného řetězce.  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
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
  
 Tento kód generuje následující výstup:  
  
```console  
GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA  
HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA  
LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA  
LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA  
```  
  
## <a name="see-also"></a>Viz také:

- [Projekce a transformace (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
