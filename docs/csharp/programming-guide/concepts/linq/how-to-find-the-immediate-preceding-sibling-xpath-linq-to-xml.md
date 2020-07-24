---
title: Jak najít bezprostřední předchozí položku na stejné úrovni (XPath-LINQ to XML) (C#)
description: Tento příklad v jazyce C# porovnává XPath s LINQ to XML pro nalezení stejné úrovně, která bezprostředně předchází uzlu.
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: eaee7f1205ce0d0b2a9c2c41d96ba532573a1384
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105200"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a><span data-ttu-id="f7ca7-103">Jak najít bezprostřední předchozí položku na stejné úrovni (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f7ca7-103">How to find the immediate preceding sibling (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="f7ca7-104">Někdy chcete najít bezprostřední předchozí položku na stejné úrovni jako uzel.</span><span class="sxs-lookup"><span data-stu-id="f7ca7-104">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="f7ca7-105">Z důvodu rozdílu v sémantikě pozičních predikátů pro předchozí osy na stejné úrovni ve výrazu XPath, na rozdíl od [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , jde o jedno z zajímavějších porovnání.</span><span class="sxs-lookup"><span data-stu-id="f7ca7-105">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7ca7-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="f7ca7-106">Example</span></span>  
 <span data-ttu-id="f7ca7-107">V tomto příkladu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotaz pomocí <xref:System.Linq.Enumerable.Last%2A> operátoru najde poslední uzel v kolekci, kterou vrátí <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> .</span><span class="sxs-lookup"><span data-stu-id="f7ca7-107">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="f7ca7-108">Naopak výraz XPath používá predikát s hodnotou 1 pro nalezení bezprostředně předcházejícího prvku.</span><span class="sxs-lookup"><span data-stu-id="f7ca7-108">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
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
  
 <span data-ttu-id="f7ca7-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f7ca7-109">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Child3 />  
```  
