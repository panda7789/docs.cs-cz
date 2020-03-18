---
title: Jak najít atributy na stejné úrovni s určitým názvem (XPath-LINQ na XML) (C#)
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 331e1a7f432f4d06b697180b1594106ec6842c9a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169256"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="7e704-102">Jak najít atributy na stejné úrovni s určitým názvem (XPath-LINQ na XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7e704-102">How to find attributes of siblings with a specific name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="7e704-103">Toto téma ukazuje, jak najít všechny atributy na stejné úrovni kontextového uzlu.</span><span class="sxs-lookup"><span data-stu-id="7e704-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="7e704-104">V kolekci jsou vráceny pouze atributy s určitým názvem.</span><span class="sxs-lookup"><span data-stu-id="7e704-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="7e704-105">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="7e704-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="7e704-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e704-106">Example</span></span>  
 <span data-ttu-id="7e704-107">Tento příklad nejprve `Book` vyhledá prvek a potom `Book`vyhledá všechny prvky `id`na stejné úrovni s názvem a potom vyhledá všechny atributy s názvem .</span><span class="sxs-lookup"><span data-stu-id="7e704-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="7e704-108">Výsledkem je kolekce atributů.</span><span class="sxs-lookup"><span data-stu-id="7e704-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="7e704-109">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Books (LINQ to XML).](./sample-xml-file-books-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="7e704-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="7e704-110">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7e704-110">This example produces the following output:</span></span>  
  
```output  
Results are identical  
id="bk101"  
id="bk102"  
```  
  