---
title: 'Postupy: Vyhledání bezprostředně předcházejícího uzlu na stejné úrovni (XPath – LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
ms.openlocfilehash: 8b0071b2f39b8debdd52083718fe928c1f9fb6f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364523"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="6f61c-102">Postupy: Vyhledání bezprostředního předchozího uzlu na stejné úrovni (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f61c-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="6f61c-103">Někdy chcete najít bezprostřední předchozí položku na stejné úrovni jako uzel.</span><span class="sxs-lookup"><span data-stu-id="6f61c-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="6f61c-104">Z důvodu rozdílu v sémantikě pozičních predikátů pro předchozí osy na stejné úrovni ve výrazu XPath, na rozdíl od [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , jde o jedno z zajímavějších porovnání.</span><span class="sxs-lookup"><span data-stu-id="6f61c-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>

## <a name="example"></a><span data-ttu-id="6f61c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="6f61c-105">Example</span></span>

<span data-ttu-id="6f61c-106">V tomto příkladu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotaz pomocí <xref:System.Linq.Enumerable.Last%2A> operátoru najde poslední uzel v kolekci, kterou vrátí <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f61c-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="6f61c-107">Naopak výraz XPath používá predikát s hodnotou 1 pro nalezení bezprostředně předcházejícího prvku.</span><span class="sxs-lookup"><span data-stu-id="6f61c-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>

```vb
Dim root As XElement = _
    <Root>
        <Child1/>
        <Child2/>
        <Child3/>
        <Child4/>
    </Root>
Dim child4 As XElement = root.Element("Child4")

' LINQ to XML query
Dim el1 As XElement = child4.ElementsBeforeSelf().Last()

' XPath expression
Dim el2 As XElement = _
    DirectCast(child4.XPathEvaluate("preceding-sibling::*[1]"),  _
    IEnumerable).Cast(Of XElement)().First()

If el1 Is el2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(el1)
```

<span data-ttu-id="6f61c-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6f61c-108">This example produces the following output:</span></span>

```console
Results are identical
<Child3 />
```

## <a name="see-also"></a><span data-ttu-id="6f61c-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f61c-109">See also</span></span>

- [<span data-ttu-id="6f61c-110">LINQ to XML pro uživatele XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f61c-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
