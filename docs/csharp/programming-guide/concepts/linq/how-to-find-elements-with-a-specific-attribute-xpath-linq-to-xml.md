---
title: 'Postupy: Vyhledání elementů s konkrétním atributem (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
ms.openlocfilehash: fc1bc285a066dcb1843dcb626b1b3b354f28da74
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486802"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-c"></a><span data-ttu-id="ab450-102">Postupy: Vyhledání elementů s konkrétním atributem (XPath – LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ab450-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="ab450-103">Někdy budete chtít najít všechny elementy, které mají určitý atribut.</span><span class="sxs-lookup"><span data-stu-id="ab450-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="ab450-104">Nejste obavy o obsah atributu.</span><span class="sxs-lookup"><span data-stu-id="ab450-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="ab450-105">Místo toho chcete vybrat na základě existence atributu.</span><span class="sxs-lookup"><span data-stu-id="ab450-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="ab450-106">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="ab450-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="ab450-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab450-107">Example</span></span>  
 <span data-ttu-id="ab450-108">Následující kód vybere pouze prvky, které mají `Select` atribut.</span><span class="sxs-lookup"><span data-stu-id="ab450-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
```csharp  
XElement doc = XElement.Parse(  
@"<Root>  
    <Child1>1</Child1>  
    <Child2 Select='true'>2</Child2>  
    <Child3>3</Child3>  
    <Child4 Select='true'>4</Child4>  
    <Child5>5</Child5>  
</Root>");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    from el in doc.Elements()  
    where el.Attribute("Select") != null  
    select el;  
  
// XPath expression  
IEnumerable<XElement> list2 =  
    ((IEnumerable)doc.XPathEvaluate("./*[@Select]")).Cast<XElement>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="ab450-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ab450-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  