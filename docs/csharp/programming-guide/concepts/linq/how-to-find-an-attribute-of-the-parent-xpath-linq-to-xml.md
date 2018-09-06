---
title: 'Postupy: Vyhledání atributu nadřazeného elementu (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 9a6a4724c7e22b15a247622c8afdd592ee4893ab
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856410"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="63fcc-102">Postupy: Vyhledání atributu nadřazeného elementu (XPath – LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="63fcc-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="63fcc-103">Toto téma ukazuje, jak přejít do nadřazeného elementu a vyhledání atributu ho.</span><span class="sxs-lookup"><span data-stu-id="63fcc-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="63fcc-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="63fcc-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="63fcc-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="63fcc-105">Example</span></span>  
 <span data-ttu-id="63fcc-106">V tomto příkladu nejprve vyhledá `Author` elementu.</span><span class="sxs-lookup"><span data-stu-id="63fcc-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="63fcc-107">Následně vyhledá `id` atributu nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="63fcc-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="63fcc-108">Tento příklad používá následujícího dokumentu XML: [ukázkový soubor XML: knihy (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="63fcc-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="63fcc-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="63fcc-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="63fcc-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="63fcc-110">See Also</span></span>

- [<span data-ttu-id="63fcc-111">LINQ to XML pro uživatele jazyka XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="63fcc-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
