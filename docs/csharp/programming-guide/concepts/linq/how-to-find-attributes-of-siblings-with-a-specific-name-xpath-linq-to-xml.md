---
title: 'Postupy: vyhledání atributů elementů na stejné úrovni s konkrétním názvem (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 60b6529f310ccbb02160ff96e1db7870bcc71058
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863118"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="e069c-102">Postupy: vyhledání atributů elementů na stejné úrovni s konkrétním názvem (XPath – LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e069c-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="e069c-103">Toto téma ukazuje, jak najít všechny atributy na stejné úrovni kontextu uzlu.</span><span class="sxs-lookup"><span data-stu-id="e069c-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="e069c-104">Pouze atributy s konkrétním názvem jsou vráceny v kolekci.</span><span class="sxs-lookup"><span data-stu-id="e069c-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="e069c-105">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="e069c-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="e069c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="e069c-106">Example</span></span>  
 <span data-ttu-id="e069c-107">V tomto příkladu nejdříve vyhledá `Book` elementu a najde všechny prvky na stejné úrovni s názvem `Book`a následně vyhledá všechny atributy s názvem `id`.</span><span class="sxs-lookup"><span data-stu-id="e069c-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="e069c-108">Výsledkem je kolekce atributů.</span><span class="sxs-lookup"><span data-stu-id="e069c-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="e069c-109">Tento příklad používá následujícího dokumentu XML: [ukázkový soubor XML: knihy (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e069c-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="e069c-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e069c-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a><span data-ttu-id="e069c-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="e069c-111">See Also</span></span>

- [<span data-ttu-id="e069c-112">LINQ to XML pro uživatele jazyka XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="e069c-112">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
