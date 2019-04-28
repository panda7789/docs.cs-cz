---
title: 'Postupy: Vyhledání atributu nadřazeného elementu (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: e139e278141a8f42cddf8103f1c5d8d3195751e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668026"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="31f9b-102">Postupy: Vyhledání atributu nadřazeného elementu (XPath – LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="31f9b-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="31f9b-103">Toto téma ukazuje, jak přejít do nadřazeného elementu a vyhledání atributu ho.</span><span class="sxs-lookup"><span data-stu-id="31f9b-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="31f9b-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="31f9b-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="31f9b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="31f9b-105">Example</span></span>  
 <span data-ttu-id="31f9b-106">V tomto příkladu nejprve vyhledá `Author` elementu.</span><span class="sxs-lookup"><span data-stu-id="31f9b-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="31f9b-107">Následně vyhledá `id` atributu nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="31f9b-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="31f9b-108">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Knihy (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="31f9b-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement author =   
    books  
    .Root  
    .Element("Book")  
    .Element("Author");  
  
// LINQ to XML query  
XAttribute att1 =  
    author  
    .Parent  
    .Attribute("id");  
  
// XPath expression  
XAttribute att2 = ((IEnumerable)author.XPathEvaluate("../@id")).Cast<XAttribute>().First();  
  
if (att1 == att2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(att1);  
```  
  
 <span data-ttu-id="31f9b-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="31f9b-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="31f9b-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31f9b-110">See also</span></span>

- [<span data-ttu-id="31f9b-111">LINQ to XML pro uživatele jazyka XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="31f9b-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
