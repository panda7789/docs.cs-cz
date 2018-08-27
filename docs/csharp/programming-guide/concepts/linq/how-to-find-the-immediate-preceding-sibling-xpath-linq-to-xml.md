---
title: 'Postupy: vyhledání okamžité předcházející na stejné úrovni (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: 82c0ee6e7340ada18fb2077c0b8b04fb6a41671a
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935190"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a><span data-ttu-id="f6125-102">Postupy: vyhledání okamžité předcházející na stejné úrovni (XPath – LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f6125-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="f6125-103">Někdy budete chtít najít okamžité předcházející na stejné k uzlu.</span><span class="sxs-lookup"><span data-stu-id="f6125-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="f6125-104">Z důvodu rozdíly v sémantice poziční predikáty. pro předchozí osy na stejné úrovni ve výrazu XPath, nikoli [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], to je jedna z zajímavější porovnání.</span><span class="sxs-lookup"><span data-stu-id="f6125-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6125-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6125-105">Example</span></span>  
 <span data-ttu-id="f6125-106">V tomto příkladu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotaz používá <xref:System.Linq.Enumerable.Last%2A> operátor najít poslední uzel v kolekci vrácené poskytovatelem <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6125-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="f6125-107">Výraz XPath naopak používá k nalezení prvku bezprostředně předcházející predikátu s hodnotou 1.</span><span class="sxs-lookup"><span data-stu-id="f6125-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
    @"<Root>  
    <Child1/>  
    <Child2/>  
    <Child3/>  
    <Child4/>  
</Root>");  
XElement child4 = root.Element("Child4");  
  
// LINQ to XML query  
XElement el1 =  
    child4  
    .ElementsBeforeSelf()  
    .Last();  
  
// XPath expression  
XElement el2 =  
    ((IEnumerable)child4  
                 .XPathEvaluate("preceding-sibling::*[1]"))  
                 .Cast<XElement>()  
                 .First();  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 <span data-ttu-id="f6125-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f6125-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6125-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6125-109">See Also</span></span>  
 [<span data-ttu-id="f6125-110">LINQ to XML pro uživatele jazyka XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="f6125-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
