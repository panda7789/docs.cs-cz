---
title: "Postupy: vyhledání jednoho následníka metodou následníky (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6f735be9-0293-4680-8007-ca9d96bfebed
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6dc90262318f5f31c4236318f87393749295a18a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-c"></a><span data-ttu-id="3505b-102">Postupy: vyhledání jednoho následníka metodou následníky (C#)</span><span class="sxs-lookup"><span data-stu-id="3505b-102">How to: Find a Single Descendant Using the Descendants Method (C#)</span></span>
<span data-ttu-id="3505b-103">Můžete použít <xref:System.Xml.Linq.XContainer.Descendants%2A> osy metoda rychle napsat kód najít jednoho jednoznačně s názvem elementu.</span><span class="sxs-lookup"><span data-stu-id="3505b-103">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to quickly write code to find a single uniquely named element.</span></span> <span data-ttu-id="3505b-104">Tento postup je zvlášť užitečné, když chcete najít konkrétní následníka s konkrétním názvem.</span><span class="sxs-lookup"><span data-stu-id="3505b-104">This technique is especially useful when you want to find a particular descendant with a specific name.</span></span> <span data-ttu-id="3505b-105">Můžete napsat kód, přejděte na požadovaný element, ale je často rychlejší a snadnější k zápisu kódu pomocí <xref:System.Xml.Linq.XContainer.Descendants%2A> osy.</span><span class="sxs-lookup"><span data-stu-id="3505b-105">You could write the code to navigate to the desired element, but it is often faster and easier to write the code using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3505b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="3505b-106">Example</span></span>  
 <span data-ttu-id="3505b-107">Tento příklad používá <xref:System.Linq.Enumerable.First%2A> operátor standardní dotazu.</span><span class="sxs-lookup"><span data-stu-id="3505b-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>  
  
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
  
 <span data-ttu-id="3505b-108">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3505b-108">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="example"></a><span data-ttu-id="3505b-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="3505b-109">Example</span></span>  
 <span data-ttu-id="3505b-110">Následující příklad ukazuje stejný dotaz pro formát XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3505b-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="3505b-111">Další informace najdete v tématu [práci s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="3505b-111">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="3505b-112">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3505b-112">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="see-also"></a><span data-ttu-id="3505b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="3505b-113">See Also</span></span>  
 [<span data-ttu-id="3505b-114">Základní dotazy (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="3505b-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
