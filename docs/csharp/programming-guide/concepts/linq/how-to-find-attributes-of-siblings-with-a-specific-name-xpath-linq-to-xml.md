---
title: "Postupy: vyhledání atributů na stejné úrovni s konkrétním názvem (XPath-technologie LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b5a67d502289b10dca95bbc91b16cbc2beae90cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="8ee50-102">Postupy: vyhledání atributů na stejné úrovni s konkrétním názvem (XPath-technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8ee50-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="8ee50-103">Toto téma ukazuje, jak najít všechny atributy stejné úrovně uzlu.</span><span class="sxs-lookup"><span data-stu-id="8ee50-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="8ee50-104">Pouze atributy s konkrétním názvem jsou vráceny v kolekci.</span><span class="sxs-lookup"><span data-stu-id="8ee50-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="8ee50-105">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="8ee50-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="8ee50-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ee50-106">Example</span></span>  
 <span data-ttu-id="8ee50-107">Tento příklad nejprve najde `Book` elementu a najde všechny elementy na stejné úrovni jako s názvem `Book`a potom vyhledá všechny atributy s názvem `id`.</span><span class="sxs-lookup"><span data-stu-id="8ee50-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="8ee50-108">Výsledkem je kolekce atributů.</span><span class="sxs-lookup"><span data-stu-id="8ee50-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="8ee50-109">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: knihy (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8ee50-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =   
    books  
    .Root  
    .Element("Book");  
  
// LINQ to XML query  
IEnumerable<XAttribute> list1 =  
    from el in book.Parent.Elements("Book")  
    select el.Attribute("id");  
  
// XPath expression  
IEnumerable<XAttribute> list2 =  
  ((IEnumerable)book.XPathEvaluate("../Book/@id")).Cast<XAttribute>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XAttribute el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="8ee50-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8ee50-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ee50-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ee50-111">See Also</span></span>  
 [<span data-ttu-id="8ee50-112">Technologie LINQ to XML pro uživatele XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="8ee50-112">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
