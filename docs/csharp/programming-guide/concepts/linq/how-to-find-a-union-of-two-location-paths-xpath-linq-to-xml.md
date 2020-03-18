---
title: Jak najít sjednocení dvou cest umístění (XPath-LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 17a3310f367cb68b3b80b1a3f30af40428f6d2c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141208"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a><span data-ttu-id="9500f-102">Jak najít sjednocení dvou cest umístění (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9500f-102">How to find a union of two location paths (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="9500f-103">XPath umožňuje najít spojení výsledků dvou cest umístění XPath.</span><span class="sxs-lookup"><span data-stu-id="9500f-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="9500f-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="9500f-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="9500f-105">Můžete dosáhnout stejných výsledků <xref:System.Linq.Enumerable.Concat%2A> pomocí standardního operátoru dotazu.</span><span class="sxs-lookup"><span data-stu-id="9500f-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9500f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="9500f-106">Example</span></span>  
 <span data-ttu-id="9500f-107">Tento příklad vyhledá `Category` všechny prvky `Price` a všechny prvky a zřetězí je do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="9500f-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="9500f-108">Všimněte [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] si, <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> že dotaz volá pořadí výsledků.</span><span class="sxs-lookup"><span data-stu-id="9500f-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="9500f-109">Výsledky vyhodnocení výrazu XPath jsou také v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="9500f-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="9500f-110">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Numerická data (LINQ to XML).](./sample-xml-file-numerical-data-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="9500f-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="9500f-111">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9500f-111">This example produces the following output:</span></span>  
  
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
  