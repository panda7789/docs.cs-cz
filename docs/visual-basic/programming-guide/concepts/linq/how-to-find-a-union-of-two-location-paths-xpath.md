---
title: 'Postupy: Vyhledání sjednocení dvou cest k umístění (XPath – LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: 964e42f194cd5e6a4d8f36cfe2164268e650f9da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728249"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="50ef3-102">Postupy: Vyhledání sjednocení dvou cest k umístění (XPath – LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50ef3-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="50ef3-103">Výraz XPath umožňuje najít sjednocení výsledky ze dvou možných cest umístění XPath.</span><span class="sxs-lookup"><span data-stu-id="50ef3-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="50ef3-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="50ef3-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="50ef3-105">Můžete dosáhnout stejných výsledků pomocí <xref:System.Linq.Enumerable.Concat%2A> standardní operátor dotazu.</span><span class="sxs-lookup"><span data-stu-id="50ef3-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50ef3-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="50ef3-106">Example</span></span>  
 <span data-ttu-id="50ef3-107">Tento příklad vyhledá všechny `Category` elementy a všechny `Price` elementy a zřetězí do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="50ef3-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="50ef3-108">Všimněte si, že [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazování volání <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> řazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="50ef3-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="50ef3-109">Výsledky vyhodnocení výrazu XPath jsou také v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="50ef3-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="50ef3-110">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Číselná Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="50ef3-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="50ef3-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="50ef3-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="50ef3-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50ef3-112">See also</span></span>
- [<span data-ttu-id="50ef3-113">LINQ to XML pro uživatele jazyka XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50ef3-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
