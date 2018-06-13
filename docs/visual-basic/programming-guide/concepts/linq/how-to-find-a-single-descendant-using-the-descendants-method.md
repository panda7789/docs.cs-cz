---
title: 'Postupy: vyhledání jednoho následníka pomocí metody následníky (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 0c03468c-efc8-4140-98f3-fb67acd9e8e1
ms.openlocfilehash: 5c4e857d28ab4660638198c054cf93bf94a621a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642835"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-visual-basic"></a><span data-ttu-id="39e94-102">Postupy: vyhledání jednoho následníka pomocí metody následníky (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39e94-102">How to: Find a Single Descendant Using the Descendants Method (Visual Basic)</span></span>
<span data-ttu-id="39e94-103">Můžete použít <xref:System.Xml.Linq.XContainer.Descendants%2A> osy metoda rychle napsat kód najít jednoho jednoznačně s názvem elementu.</span><span class="sxs-lookup"><span data-stu-id="39e94-103">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to quickly write code to find a single uniquely named element.</span></span> <span data-ttu-id="39e94-104">Tento postup je zvlášť užitečné, když chcete najít konkrétní následníka s konkrétním názvem.</span><span class="sxs-lookup"><span data-stu-id="39e94-104">This technique is especially useful when you want to find a particular descendant with a specific name.</span></span> <span data-ttu-id="39e94-105">Můžete napsat kód, přejděte na požadovaný element, ale je často rychlejší a snadnější k zápisu kódu pomocí <xref:System.Xml.Linq.XContainer.Descendants%2A> osy.</span><span class="sxs-lookup"><span data-stu-id="39e94-105">You could write the code to navigate to the desired element, but it is often faster and easier to write the code using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39e94-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="39e94-106">Example</span></span>  
 <span data-ttu-id="39e94-107">Tento příklad používá <xref:System.Linq.Enumerable.First%2A> operátor standardní dotazu.</span><span class="sxs-lookup"><span data-stu-id="39e94-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>  
  
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
  
 <span data-ttu-id="39e94-108">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="39e94-108">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="example"></a><span data-ttu-id="39e94-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="39e94-109">Example</span></span>  
 <span data-ttu-id="39e94-110">Následující příklad ukazuje stejný dotaz pro formát XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="39e94-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="39e94-111">Další informace najdete v tématu [práci s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="39e94-111">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="39e94-112">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="39e94-112">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="see-also"></a><span data-ttu-id="39e94-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="39e94-113">See Also</span></span>  
 [<span data-ttu-id="39e94-114">Základní dotazy (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39e94-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
