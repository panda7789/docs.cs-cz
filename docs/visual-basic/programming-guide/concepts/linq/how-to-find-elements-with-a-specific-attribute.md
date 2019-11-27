---
title: 'Postupy: Vyhledání elementů s konkrétním atributem (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 4bb38d2c-bc7c-4196-8909-aaf41fb86b28
ms.openlocfilehash: ef8dd26d40f15d3d5a27f0ca5d62f7337f2054ca
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343689"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="69c90-102">Postupy: Vyhledání elementů s konkrétním atributem (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69c90-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="69c90-103">Někdy chcete najít všechny prvky, které mají konkrétní atribut.</span><span class="sxs-lookup"><span data-stu-id="69c90-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="69c90-104">Nemáte obavy o obsah atributu.</span><span class="sxs-lookup"><span data-stu-id="69c90-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="69c90-105">Místo toho je třeba vybrat na základě existence atributu.</span><span class="sxs-lookup"><span data-stu-id="69c90-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="69c90-106">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="69c90-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="69c90-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="69c90-107">Example</span></span>  
 <span data-ttu-id="69c90-108">Následující kód vybere pouze prvky, které mají atribut `Select`.</span><span class="sxs-lookup"><span data-stu-id="69c90-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
```vb  
Dim doc As XElement = _   
    <Root>  
        <Child1>1</Child1>  
        <Child2 Select='true'>2</Child2>  
        <Child3>3</Child3>  
        <Child4 Select='true'>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    From el In doc.Elements() _  
    Where el.@Select <> Nothing _  
    Select el  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = DirectCast(doc.XPathEvaluate _  
    ("./*[@Select]"), IEnumerable).Cast(Of XElement)()  
  
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
  
 <span data-ttu-id="69c90-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="69c90-109">This example produces the following output:</span></span>  
  
```console
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a><span data-ttu-id="69c90-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69c90-110">See also</span></span>

- [<span data-ttu-id="69c90-111">LINQ to XML pro uživatele XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69c90-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
