---
title: 'Postupy: vyhledat atribut nadřazeného (XPath-technologie LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9d2572fd-27d4-426c-b079-16854cb9ec7d
ms.openlocfilehash: af2b6fc3aaebe4ba45be405c587c549ea73b3289
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33639360"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="3f7ec-102">Postupy: vyhledat atribut nadřazeného (XPath-technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f7ec-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="3f7ec-103">Toto téma ukazuje, jak vyhledat atribut ho a přejděte do nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="3f7ec-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="3f7ec-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="3f7ec-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="3f7ec-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f7ec-105">Example</span></span>  
 <span data-ttu-id="3f7ec-106">Tento příklad nejprve najde `Author` elementu.</span><span class="sxs-lookup"><span data-stu-id="3f7ec-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="3f7ec-107">Poté vyhledá `id` atribut nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="3f7ec-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="3f7ec-108">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: knihy (technologie LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3f7ec-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim books As XDocument = XDocument.Load("Books.xml")  
Dim author As XElement = books.Root.<Book>.<Author>.FirstOrDefault()  
  
' LINQ to XML query  
Dim att1 As XAttribute = author.Parent.Attribute("id")  
  
' XPath expression  
Dim att2 As XAttribute = DirectCast(author.XPathEvaluate("../@id"),  _  
    IEnumerable).Cast(Of XAttribute)().First()  
  
If att1 Is att2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(att1)  
```  
  
 <span data-ttu-id="3f7ec-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3f7ec-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f7ec-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f7ec-110">See Also</span></span>  
 [<span data-ttu-id="3f7ec-111">Technologie LINQ to XML pro uživatele XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f7ec-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
