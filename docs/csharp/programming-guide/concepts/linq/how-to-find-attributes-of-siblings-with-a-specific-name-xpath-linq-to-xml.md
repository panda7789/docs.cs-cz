---
title: 'Postupy: Vyhledání atributů elementů na stejné úrovni s konkrétním názvem (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 0c62ecb7660a012af556515ba5e7de330d5ab5e7
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486790"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="8c0c7-102">Postupy: Vyhledání atributů elementů na stejné úrovni s konkrétním názvem (XPath – LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8c0c7-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="8c0c7-103">Toto téma ukazuje, jak najít všechny atributy na stejné úrovni kontextu uzlu.</span><span class="sxs-lookup"><span data-stu-id="8c0c7-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="8c0c7-104">Pouze atributy s konkrétním názvem jsou vráceny v kolekci.</span><span class="sxs-lookup"><span data-stu-id="8c0c7-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="8c0c7-105">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="8c0c7-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="8c0c7-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c0c7-106">Example</span></span>  
 <span data-ttu-id="8c0c7-107">V tomto příkladu nejdříve vyhledá `Book` elementu a najde všechny prvky na stejné úrovni s názvem `Book`a následně vyhledá všechny atributy s názvem `id`.</span><span class="sxs-lookup"><span data-stu-id="8c0c7-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="8c0c7-108">Výsledkem je kolekce atributů.</span><span class="sxs-lookup"><span data-stu-id="8c0c7-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="8c0c7-109">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Knihy (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8c0c7-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="8c0c7-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8c0c7-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  