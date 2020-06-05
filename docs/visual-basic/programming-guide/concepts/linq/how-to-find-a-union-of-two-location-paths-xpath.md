---
title: 'Postupy: Vyhledání sjednocení dvou cest k umístění (XPath – LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: 36528d1748d5675231f14de92dcd78734a696711
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406869"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="3e754-102">Postupy: Vyhledání sjednocení dvou cest umístění (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e754-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="3e754-103">XPath umožňuje najít sjednocení výsledků dvou cest umístění XPath.</span><span class="sxs-lookup"><span data-stu-id="3e754-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="3e754-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="3e754-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="3e754-105">Stejné výsledky můžete dosáhnout pomocí <xref:System.Linq.Enumerable.Concat%2A> standardního operátoru dotazu.</span><span class="sxs-lookup"><span data-stu-id="3e754-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e754-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e754-106">Example</span></span>  
 <span data-ttu-id="3e754-107">V tomto příkladu jsou vyhledány všechny `Category` prvky a všechny `Price` prvky a zřetězeny do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="3e754-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="3e754-108">Všimněte si, že [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotaz volá <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> k řazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="3e754-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="3e754-109">Výsledky vyhodnocení výrazu XPath jsou také v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="3e754-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="3e754-110">Tento příklad používá následující dokument XML: [ukázkový soubor XML: numerická data (LINQ to XML)](sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3e754-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim data As XDocument = XDocument.Load("Data.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    data...<Category>.Concat(data...<Price>).InDocumentOrder()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    data.XPathSelectElements("//Category|//Price")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="3e754-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3e754-111">This example produces the following output:</span></span>  
  
```console
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
  
## <a name="see-also"></a><span data-ttu-id="3e754-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e754-112">See also</span></span>

- [<span data-ttu-id="3e754-113">LINQ to XML pro uživatele XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e754-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
