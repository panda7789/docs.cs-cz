---
title: 'Postupy: dotazování technologie LINQ to XML s použitím XPath (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
ms.openlocfilehash: d8f23bd8417c3f59377e5e677b08e403ecc1122d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33639334"
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a><span data-ttu-id="5aed6-102">Postupy: dotazování technologie LINQ to XML s použitím XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5aed6-102">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>
<span data-ttu-id="5aed6-103">Toto téma představuje rozšiřující metody, které vám umožní zadat dotaz strom XML s použitím XPath.</span><span class="sxs-lookup"><span data-stu-id="5aed6-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="5aed6-104">Podrobné informace o použití těchto metod rozšíření najdete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5aed6-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="5aed6-105">Pokud nemáte velmi konkrétní důvod, proč pro dotazování pomocí jazyka XPath, jako je například rozsáhlé používání starší verze kódu, pomocí technologie LINQ to XML XPath se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="5aed6-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="5aed6-106">Nebude provádět dotazy XPath a také [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="5aed6-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5aed6-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="5aed6-107">Example</span></span>  
 <span data-ttu-id="5aed6-108">Následující příklad vytvoří malé stromu XML a používá <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> pro výběr sady elementů.</span><span class="sxs-lookup"><span data-stu-id="5aed6-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child1>2</Child1>  
        <Child1>3</Child1>  
        <Child2>4</Child2>  
        <Child2>5</Child2>  
        <Child2>6</Child2>  
    </Root>  
  
Dim list As IEnumerable(Of XElement) = root.XPathSelectElements("./Child2")  
For Each el As XElement In list  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="5aed6-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5aed6-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5aed6-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="5aed6-110">See Also</span></span>  
 [<span data-ttu-id="5aed6-111">Pokročilé techniky dotazu (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5aed6-111">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
