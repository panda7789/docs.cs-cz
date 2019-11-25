---
title: Jak najít sjednocení dvou cest umístění (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 17a3310f367cb68b3b80b1a3f30af40428f6d2c7
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141208"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a><span data-ttu-id="0283a-102">Jak najít sjednocení dvou cest umístění (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0283a-102">How to find a union of two location paths (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="0283a-103">XPath umožňuje najít sjednocení výsledků dvou cest umístění XPath.</span><span class="sxs-lookup"><span data-stu-id="0283a-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="0283a-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="0283a-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="0283a-105">Stejné výsledky můžete dosáhnout pomocí operátoru dotazu <xref:System.Linq.Enumerable.Concat%2A> Standard.</span><span class="sxs-lookup"><span data-stu-id="0283a-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0283a-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="0283a-106">Example</span></span>  
 <span data-ttu-id="0283a-107">V tomto příkladu jsou vyhledány všechny prvky `Category` a všechny `Price` prvky a zřetězeny do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="0283a-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="0283a-108">Všimněte si, že dotaz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] volá <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> k seřazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="0283a-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="0283a-109">Výsledky vyhodnocení výrazu XPath jsou také v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="0283a-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="0283a-110">Tento příklad používá následující dokument XML: [ukázkový soubor XML: numerická data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0283a-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument data = XDocument.Load("Data.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    data  
    .Descendants("Category")  
    .Concat(  
        data  
        .Descendants("Price")  
    )  
    .InDocumentOrder();  
  
// XPath expression  
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="0283a-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0283a-111">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  