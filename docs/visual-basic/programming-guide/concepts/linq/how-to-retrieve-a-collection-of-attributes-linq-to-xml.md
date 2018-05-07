---
title: 'Postupy: načtení kolekci atributů (technologie LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
ms.openlocfilehash: fdb7f236339de242a887f3040e33b8d24eb114f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a>Postupy: načtení kolekci atributů (technologie LINQ to XML) (Visual Basic)
Toto téma představuje <xref:System.Xml.Linq.XElement.Attributes%2A> metoda. Tato metoda načte atributy elementu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak k iteraci v rámci kolekce atributů elementu.  
  
```vb  
Dim val = _  
    <Value ID="1243" Type="int" ConvertableTo="double">100</Value>  
Dim listOfAttributes As IEnumerable(Of XAttribute) = _  
    From att In val.Attributes() _  
    Select att  
For Each att As XAttribute In listOfAttributes  
    Console.WriteLine(att)  
Next  
```  
  
 Tento kód vytvoří následující výstup:  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to XML osy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
