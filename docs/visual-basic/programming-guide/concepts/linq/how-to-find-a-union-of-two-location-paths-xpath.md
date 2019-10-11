---
title: 'Postupy: Vyhledání sjednocení dvou cest umístění (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: 6905e6a7bd0cba37006b1fc3077ad72de36bcf56
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72249952"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="268a4-102">Postupy: Vyhledání sjednocení dvou cest umístění (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="268a4-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="268a4-103">XPath umožňuje najít sjednocení výsledků dvou cest umístění XPath.</span><span class="sxs-lookup"><span data-stu-id="268a4-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="268a4-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="268a4-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="268a4-105">Stejné výsledky můžete dosáhnout pomocí operátoru standardního dotazu <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="268a4-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="268a4-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="268a4-106">Example</span></span>  
 <span data-ttu-id="268a4-107">V tomto příkladu jsou vyhledány všechny prvky `Category` a všechny prvky `Price` a zřetězeny do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="268a4-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="268a4-108">Všimněte si, že dotaz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] volá <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> pro seřazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="268a4-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="268a4-109">Výsledky vyhodnocení výrazu XPath jsou také v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="268a4-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="268a4-110">Tento příklad používá následující dokument XML: [ukázkový soubor XML: numerická data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="268a4-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="268a4-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="268a4-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="268a4-112">Související témata</span><span class="sxs-lookup"><span data-stu-id="268a4-112">See also</span></span>

- [<span data-ttu-id="268a4-113">LINQ to XML pro uživatele XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="268a4-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
