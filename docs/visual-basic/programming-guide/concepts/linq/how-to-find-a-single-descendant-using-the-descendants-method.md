---
title: 'Postupy: Vyhledání jednoho následníka pomocí metody Descendants (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 0c03468c-efc8-4140-98f3-fb67acd9e8e1
ms.openlocfilehash: 7e90e7e8c4a6cd4c91b15037be0fa422dd2108e3
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709081"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-visual-basic"></a><span data-ttu-id="dd70d-102">Postupy: Vyhledání jednoho následníka pomocí metody Descendants (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd70d-102">How to: Find a Single Descendant Using the Descendants Method (Visual Basic)</span></span>
<span data-ttu-id="dd70d-103">Můžete použít <xref:System.Xml.Linq.XContainer.Descendants%2A> metodu Axis k rychlému psaní kódu pro vyhledání jediného jedinečného pojmenovaného elementu.</span><span class="sxs-lookup"><span data-stu-id="dd70d-103">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to quickly write code to find a single uniquely named element.</span></span> <span data-ttu-id="dd70d-104">Tato technika je užitečná hlavně v případě, že chcete najít konkrétního následníka s konkrétním názvem.</span><span class="sxs-lookup"><span data-stu-id="dd70d-104">This technique is especially useful when you want to find a particular descendant with a specific name.</span></span> <span data-ttu-id="dd70d-105">Můžete napsat kód pro přechod na požadovaný prvek, ale je často rychlejší a snazší napsat kód pomocí <xref:System.Xml.Linq.XContainer.Descendants%2A> osy.</span><span class="sxs-lookup"><span data-stu-id="dd70d-105">You could write the code to navigate to the desired element, but it is often faster and easier to write the code using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd70d-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd70d-106">Example</span></span>  
 <span data-ttu-id="dd70d-107">V tomto příkladu se <xref:System.Linq.Enumerable.First%2A> používá standardní operátor dotazu.</span><span class="sxs-lookup"><span data-stu-id="dd70d-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1>GC1 Value</GrandChild1>  
        </Child1>  
        <Child2>  
            <GrandChild2>GC2 Value</GrandChild2>  
        </Child2>  
        <Child3>  
            <GrandChild3>GC3 Value</GrandChild3>  
        </Child3>  
        <Child4>  
            <GrandChild4>GC4 Value</GrandChild4>  
        </Child4>  
    </Root>  
Dim grandChild3 As String = _  
    (From el In root...<GrandChild3> _  
    Select el).First()  
Console.WriteLine(grandChild3)  
```  
  
 <span data-ttu-id="dd70d-108">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="dd70d-108">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="example"></a><span data-ttu-id="dd70d-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd70d-109">Example</span></span>  
 <span data-ttu-id="dd70d-110">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="dd70d-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="dd70d-111">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="dd70d-111">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child1>  
                    <aw:GrandChild1>GC1 Value</aw:GrandChild1>  
                </aw:Child1>  
                <aw:Child2>  
                    <aw:GrandChild2>GC2 Value</aw:GrandChild2>  
                </aw:Child2>  
                <aw:Child3>  
                    <aw:GrandChild3>GC3 Value</aw:GrandChild3>  
                </aw:Child3>  
                <aw:Child4>  
                    <aw:GrandChild4>GC4 Value</aw:GrandChild4>  
                </aw:Child4>  
            </aw:Root>  
        Dim grandChild3 As String = _  
            (From el In root...<aw:GrandChild3> _  
            Select el).First()  
        Console.WriteLine(grandChild3)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="dd70d-112">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="dd70d-112">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd70d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd70d-113">See also</span></span>

- [<span data-ttu-id="dd70d-114">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd70d-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
