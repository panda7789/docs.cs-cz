---
title: 'Postupy: Vyhledání sjednocení dvou cest umístění (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: 6905e6a7bd0cba37006b1fc3077ad72de36bcf56
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72249952"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a>Postupy: Vyhledání sjednocení dvou cest umístění (XPath-LINQ to XML) (Visual Basic)
XPath umožňuje najít sjednocení výsledků dvou cest umístění XPath.  
  
 Výraz XPath je:  
  
 `//Category|//Price`  
  
 Stejné výsledky můžete dosáhnout pomocí operátoru standardního dotazu <xref:System.Linq.Enumerable.Concat%2A>.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu jsou vyhledány všechny prvky `Category` a všechny prvky `Price` a zřetězeny do jedné kolekce. Všimněte si, že dotaz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] volá <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> pro seřazení výsledků. Výsledky vyhodnocení výrazu XPath jsou také v pořadí dokumentů.  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: numerická data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).  
  
```vb  
Dim data As XDocument = XDocument.Load("Data.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    data...<Category>.Concat(data...<Price>).InDocumentOrder()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    data.XPathSelectElements("//Category|//Price")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```console
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  
## <a name="see-also"></a>Související témata

- [LINQ to XML pro uživatele XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
