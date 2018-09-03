---
title: 'Postupy: vyhledání sjednocení dvou cest k umístění (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: cd98c1da2f2f8653c5db36f89a63dfdc7a7ab691
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481338"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a><span data-ttu-id="af856-102">Postupy: vyhledání sjednocení dvou cest k umístění (XPath – LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="af856-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="af856-103">Výraz XPath umožňuje najít sjednocení výsledky ze dvou možných cest umístění XPath.</span><span class="sxs-lookup"><span data-stu-id="af856-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="af856-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="af856-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="af856-105">Můžete dosáhnout stejných výsledků pomocí <xref:System.Linq.Enumerable.Concat%2A> standardní operátor dotazu.</span><span class="sxs-lookup"><span data-stu-id="af856-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af856-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="af856-106">Example</span></span>  
 <span data-ttu-id="af856-107">Tento příklad vyhledá všechny `Category` elementy a všechny `Price` elementy a zřetězí do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="af856-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="af856-108">Všimněte si, že [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazování volání <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> řazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="af856-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="af856-109">Výsledky vyhodnocení výrazu XPath jsou také v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="af856-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="af856-110">Tento příklad používá následujícího dokumentu XML: [ukázkový soubor XML: numerická Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="af856-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="af856-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="af856-111">This example produces the following output:</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="af856-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="af856-112">See Also</span></span>  
 [<span data-ttu-id="af856-113">LINQ to XML pro uživatele jazyka XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="af856-113">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
