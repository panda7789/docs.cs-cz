---
title: 'Postupy: Najít jednoho následníka pomocí metody Descendants (C#)'
ms.date: 07/20/2015
ms.assetid: 6f735be9-0293-4680-8007-ca9d96bfebed
ms.openlocfilehash: 726c89b8fdd3df774de2d7ac9a824f2b3769d404
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709970"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-c"></a><span data-ttu-id="612ab-102">Postupy: Najít jednoho následníka pomocí metody Descendants (C#)</span><span class="sxs-lookup"><span data-stu-id="612ab-102">How to: Find a Single Descendant Using the Descendants Method (C#)</span></span>
<span data-ttu-id="612ab-103">Můžete použít <xref:System.Xml.Linq.XContainer.Descendants%2A> metodu Axis k rychlému psaní kódu pro vyhledání jediného jedinečného pojmenovaného elementu.</span><span class="sxs-lookup"><span data-stu-id="612ab-103">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to quickly write code to find a single uniquely named element.</span></span> <span data-ttu-id="612ab-104">Tato technika je užitečná hlavně v případě, že chcete najít konkrétního následníka s konkrétním názvem.</span><span class="sxs-lookup"><span data-stu-id="612ab-104">This technique is especially useful when you want to find a particular descendant with a specific name.</span></span> <span data-ttu-id="612ab-105">Můžete napsat kód pro přechod na požadovaný prvek, ale je často rychlejší a snazší napsat kód pomocí <xref:System.Xml.Linq.XContainer.Descendants%2A> osy.</span><span class="sxs-lookup"><span data-stu-id="612ab-105">You could write the code to navigate to the desired element, but it is often faster and easier to write the code using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="612ab-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="612ab-106">Example</span></span>  
 <span data-ttu-id="612ab-107">V tomto příkladu se <xref:System.Linq.Enumerable.First%2A> používá standardní operátor dotazu.</span><span class="sxs-lookup"><span data-stu-id="612ab-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
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
</Root>");  
string grandChild3 = (string)  
    (from el in root.Descendants("GrandChild3")  
    select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 <span data-ttu-id="612ab-108">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="612ab-108">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="example"></a><span data-ttu-id="612ab-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="612ab-109">Example</span></span>  
 <span data-ttu-id="612ab-110">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="612ab-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="612ab-111">Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="612ab-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
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
</aw:Root>");  
XNamespace aw = "http://www.adventure-works.com";  
string grandChild3 = (string)  
    (from el in root.Descendants(aw + "GrandChild3")  
     select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 <span data-ttu-id="612ab-112">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="612ab-112">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
