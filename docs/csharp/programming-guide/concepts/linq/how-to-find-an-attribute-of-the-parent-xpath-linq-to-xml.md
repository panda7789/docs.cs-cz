---
title: "Postupy: vyhledat atribut nadřazeného (XPath-technologie LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eeb1bea8c82eaff904ec1076e92609cd16024d28
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="d0308-102">Postupy: vyhledat atribut nadřazeného (XPath-technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d0308-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="d0308-103">Toto téma ukazuje, jak vyhledat atribut ho a přejděte do nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="d0308-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="d0308-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="d0308-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="d0308-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0308-105">Example</span></span>  
 <span data-ttu-id="d0308-106">Tento příklad nejprve najde `Author` elementu.</span><span class="sxs-lookup"><span data-stu-id="d0308-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="d0308-107">Poté vyhledá `id` atribut nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="d0308-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="d0308-108">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: knihy (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d0308-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="d0308-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d0308-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0308-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0308-110">See Also</span></span>  
 [<span data-ttu-id="d0308-111">Technologie LINQ to XML pro uživatele XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="d0308-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
