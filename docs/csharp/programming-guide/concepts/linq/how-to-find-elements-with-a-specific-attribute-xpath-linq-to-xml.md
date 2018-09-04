---
title: 'Postupy: vyhledání elementů s konkrétním atributem (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
ms.openlocfilehash: da7633b34ddd61577bfc62f4f76d8f8929be1cc4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500277"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-c"></a><span data-ttu-id="29983-102">Postupy: vyhledání elementů s konkrétním atributem (XPath – LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="29983-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="29983-103">Někdy budete chtít najít všechny elementy, které mají určitý atribut.</span><span class="sxs-lookup"><span data-stu-id="29983-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="29983-104">Nejste obavy o obsah atributu.</span><span class="sxs-lookup"><span data-stu-id="29983-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="29983-105">Místo toho chcete vybrat na základě existence atributu.</span><span class="sxs-lookup"><span data-stu-id="29983-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="29983-106">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="29983-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="29983-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="29983-107">Example</span></span>  
 <span data-ttu-id="29983-108">Následující kód vybere pouze prvky, které mají `Select` atribut.</span><span class="sxs-lookup"><span data-stu-id="29983-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
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
  
 <span data-ttu-id="29983-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="29983-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a><span data-ttu-id="29983-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="29983-110">See Also</span></span>

- [<span data-ttu-id="29983-111">LINQ to XML pro uživatele jazyka XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="29983-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
