---
title: 'Postupy: Vyhledání atributu nadřazeného elementu (XPath – LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9d2572fd-27d4-426c-b079-16854cb9ec7d
ms.openlocfilehash: ded20c173063492d260aee5ba55f3c4c585bd961
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828651"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="686d8-102">Postupy: Vyhledání atributu nadřazeného elementu (XPath – LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="686d8-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="686d8-103">Toto téma ukazuje, jak přejít do nadřazeného elementu a vyhledání atributu ho.</span><span class="sxs-lookup"><span data-stu-id="686d8-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="686d8-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="686d8-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="686d8-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="686d8-105">Example</span></span>  
 <span data-ttu-id="686d8-106">V tomto příkladu nejprve vyhledá `Author` elementu.</span><span class="sxs-lookup"><span data-stu-id="686d8-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="686d8-107">Následně vyhledá `id` atributu nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="686d8-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="686d8-108">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Knihy (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="686d8-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="686d8-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="686d8-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="686d8-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="686d8-110">See also</span></span>

- [<span data-ttu-id="686d8-111">LINQ to XML pro uživatele jazyka XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="686d8-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
