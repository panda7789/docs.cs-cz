---
title: 'Postupy: hledání atributů na stejné úrovni s konkrétním názvem (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 83b3ddca-830a-4b71-9756-9e4bdf907302
ms.openlocfilehash: 709c21cee37c42f7633b2b108b8846ddd8e3b4e7
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72249903"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="71a5d-102">Postupy: hledání atributů na stejné úrovni s konkrétním názvem (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71a5d-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="71a5d-103">Toto téma ukazuje, jak najít všechny atributy na stejné úrovni kontextu uzlu.</span><span class="sxs-lookup"><span data-stu-id="71a5d-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="71a5d-104">V kolekci jsou vráceny pouze atributy s určitým názvem.</span><span class="sxs-lookup"><span data-stu-id="71a5d-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="71a5d-105">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="71a5d-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="71a5d-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="71a5d-106">Example</span></span>  
 <span data-ttu-id="71a5d-107">Tento příklad nejprve vyhledá prvek `Book` a pak najde všechny prvky na stejné úrovni s názvem `Book` a pak najde všechny atributy s názvem `id`.</span><span class="sxs-lookup"><span data-stu-id="71a5d-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="71a5d-108">Výsledkem je kolekce atributů.</span><span class="sxs-lookup"><span data-stu-id="71a5d-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="71a5d-109">Tento příklad používá následující dokument XML: [ukázkový soubor XML: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="71a5d-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim books as XDocument = XDocument.Load("Books.xml")  
Dim book As XElement = books.Root.<Book>(0)  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XAttribute) = _  
    From el In book.Parent.<Book> _  
    Select el.Attribute("id")  
  
' XPath expression  
Dim list2 As IEnumerable(Of XAttribute) = DirectCast(book. _  
    XPathEvaluate("../Book/@id"), IEnumerable).Cast(Of XAttribute)()  
  
If list1.Count() = list2.Count() And _  
        (list1.Intersect(list2)).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XAttribute In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="71a5d-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="71a5d-110">This example produces the following output:</span></span>  
  
```console  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a><span data-ttu-id="71a5d-111">Související témata</span><span class="sxs-lookup"><span data-stu-id="71a5d-111">See also</span></span>

- [<span data-ttu-id="71a5d-112">LINQ to XML pro uživatele XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71a5d-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
