---
title: 'Postupy: Vyhledání jednoho potomka pomocí metody Descendants (C#)'
ms.date: 07/20/2015
ms.assetid: 6f735be9-0293-4680-8007-ca9d96bfebed
ms.openlocfilehash: a13a4aef6a3d22d2b7c3adb8e37996de08978b6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702097"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-c"></a><span data-ttu-id="d66d3-102">Postupy: Vyhledání jednoho potomka pomocí metody Descendants (C#)</span><span class="sxs-lookup"><span data-stu-id="d66d3-102">How to: Find a Single Descendant Using the Descendants Method (C#)</span></span>
<span data-ttu-id="d66d3-103">Můžete použít <xref:System.Xml.Linq.XContainer.Descendants%2A> metody osy rychle psát kód jednoznačně najít jeden s názvem elementu.</span><span class="sxs-lookup"><span data-stu-id="d66d3-103">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to quickly write code to find a single uniquely named element.</span></span> <span data-ttu-id="d66d3-104">Tato technika je užitečná, pokud chcete najít konkrétní potomkem s konkrétním názvem.</span><span class="sxs-lookup"><span data-stu-id="d66d3-104">This technique is especially useful when you want to find a particular descendant with a specific name.</span></span> <span data-ttu-id="d66d3-105">Můžete napsat kód pro navigaci na požadovaný element, ale je často rychlejší a snazší psát kód s využitím <xref:System.Xml.Linq.XContainer.Descendants%2A> osy.</span><span class="sxs-lookup"><span data-stu-id="d66d3-105">You could write the code to navigate to the desired element, but it is often faster and easier to write the code using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d66d3-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d66d3-106">Example</span></span>  
 <span data-ttu-id="d66d3-107">V tomto příkladu <xref:System.Linq.Enumerable.First%2A> standardní operátor dotazu.</span><span class="sxs-lookup"><span data-stu-id="d66d3-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>  
  
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
  
 <span data-ttu-id="d66d3-108">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d66d3-108">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="example"></a><span data-ttu-id="d66d3-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d66d3-109">Example</span></span>  
 <span data-ttu-id="d66d3-110">Následující příklad ukazuje stejný dotaz pro soubor XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d66d3-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="d66d3-111">Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="d66d3-111">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="d66d3-112">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d66d3-112">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="see-also"></a><span data-ttu-id="d66d3-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d66d3-113">See also</span></span>

- [<span data-ttu-id="d66d3-114">Základní dotazy (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d66d3-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
