---
title: 'Postupy: načtení kolekci atributů (technologie LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
ms.openlocfilehash: fdb7f236339de242a887f3040e33b8d24eb114f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641164"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a><span data-ttu-id="5cc3a-102">Postupy: načtení kolekci atributů (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5cc3a-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="5cc3a-103">Toto téma představuje <xref:System.Xml.Linq.XElement.Attributes%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="5cc3a-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="5cc3a-104">Tato metoda načte atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="5cc3a-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cc3a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="5cc3a-105">Example</span></span>  
 <span data-ttu-id="5cc3a-106">Následující příklad ukazuje, jak k iteraci v rámci kolekce atributů elementu.</span><span class="sxs-lookup"><span data-stu-id="5cc3a-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="5cc3a-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5cc3a-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="5cc3a-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="5cc3a-108">See Also</span></span>  
 [<span data-ttu-id="5cc3a-109">Technologie LINQ to XML osy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5cc3a-109">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
