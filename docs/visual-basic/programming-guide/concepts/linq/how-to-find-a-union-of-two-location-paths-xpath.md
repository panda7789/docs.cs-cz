---
title: 'Postupy: vyhledání sjednocení dvou cest k umístění (XPath – LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: 3f67ac24d12e7d2fcbd74e2f27a75d982c1cf00b
ms.sourcegitcommit: a474397fd4de822f0d878d86d907e49763872b0b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2018
ms.locfileid: "42751941"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a>Postupy: vyhledání sjednocení dvou cest k umístění (XPath – LINQ to XML) (Visual Basic)
Výraz XPath umožňuje najít sjednocení výsledky ze dvou možných cest umístění XPath.  
  
 Výraz XPath je:  
  
 `//Category|//Price`  
  
 Můžete dosáhnout stejných výsledků pomocí <xref:System.Linq.Enumerable.Concat%2A> standardní operátor dotazu.  
  
## <a name="example"></a>Příklad  
 Tento příklad vyhledá všechny `Category` elementy a všechny `Price` elementy a zřetězí do jedné kolekce. Všimněte si, že [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazování volání <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> řazení výsledků. Výsledky vyhodnocení výrazu XPath jsou také v pořadí dokumentů.  
  
 Tento příklad používá následujícího dokumentu XML: [ukázkový soubor XML: numerická Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).  
  
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
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [LINQ to XML pro uživatele jazyka XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
