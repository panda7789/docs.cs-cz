---
title: 'Postupy: Vyhledání atributu nadřazené položky (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9d2572fd-27d4-426c-b079-16854cb9ec7d
ms.openlocfilehash: ce8fbb828a5ea8df79f449d50f1d61702a4e3df2
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72249918"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="fe91c-102">Postupy: Vyhledání atributu nadřazené položky (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe91c-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="fe91c-103">Toto téma ukazuje, jak přejít na nadřazený prvek a najít atribut.</span><span class="sxs-lookup"><span data-stu-id="fe91c-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="fe91c-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="fe91c-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="fe91c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="fe91c-105">Example</span></span>  
 <span data-ttu-id="fe91c-106">Tento příklad nejprve vyhledá prvek `Author`.</span><span class="sxs-lookup"><span data-stu-id="fe91c-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="fe91c-107">Pak nalezne atribut `id` nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="fe91c-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="fe91c-108">Tento příklad používá následující dokument XML: [ukázkový soubor XML: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="fe91c-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="fe91c-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="fe91c-109">This example produces the following output:</span></span>  
  
```console  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe91c-110">Související témata</span><span class="sxs-lookup"><span data-stu-id="fe91c-110">See also</span></span>

- [<span data-ttu-id="fe91c-111">LINQ to XML pro uživatele XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe91c-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
