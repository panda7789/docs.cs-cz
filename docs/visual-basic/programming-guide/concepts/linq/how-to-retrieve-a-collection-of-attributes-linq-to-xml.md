---
title: 'Postupy: načtení kolekce atributů (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
ms.openlocfilehash: 7c0f809c5a0707f2e6575cb8bca1b2a312f6daeb
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321328"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a><span data-ttu-id="71332-102">Postupy: načtení kolekce atributů (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71332-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="71332-103">Toto téma zavádí metodu <xref:System.Xml.Linq.XElement.Attributes%2A>.</span><span class="sxs-lookup"><span data-stu-id="71332-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="71332-104">Tato metoda načte atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="71332-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71332-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="71332-105">Example</span></span>  
 <span data-ttu-id="71332-106">Následující příklad ukazuje, jak iterovat kolekcí atributů elementu.</span><span class="sxs-lookup"><span data-stu-id="71332-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="71332-107">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="71332-107">This code produces the following output:</span></span>  
  
```console  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="71332-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71332-108">See also</span></span>

- [<span data-ttu-id="71332-109">LINQ to XML osy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71332-109">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
