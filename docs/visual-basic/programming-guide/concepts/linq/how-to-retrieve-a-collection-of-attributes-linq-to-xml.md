---
title: 'Postupy: načtení kolekce atributů (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
ms.openlocfilehash: ff260660057c3b75f4cc92c37c67fca0a0b7f192
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347578"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a><span data-ttu-id="b05fb-102">Postupy: načtení kolekce atributů (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b05fb-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="b05fb-103">Toto téma představuje metodu <xref:System.Xml.Linq.XElement.Attributes%2A>.</span><span class="sxs-lookup"><span data-stu-id="b05fb-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="b05fb-104">Tato metoda načte atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="b05fb-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b05fb-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b05fb-105">Example</span></span>  
 <span data-ttu-id="b05fb-106">Následující příklad ukazuje, jak iterovat kolekcí atributů elementu.</span><span class="sxs-lookup"><span data-stu-id="b05fb-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="b05fb-107">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b05fb-107">This code produces the following output:</span></span>  
  
```console  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="b05fb-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b05fb-108">See also</span></span>

- [<span data-ttu-id="b05fb-109">LINQ to XML osy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b05fb-109">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
