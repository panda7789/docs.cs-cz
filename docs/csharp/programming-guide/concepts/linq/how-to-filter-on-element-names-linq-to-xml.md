---
title: Jak filtrovat názvy prvků (LINQ na XML) (C#)
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 74efb19ef5ec77ca29145d27a8e5aa977530b68b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141260"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="e961f-102">Jak filtrovat názvy prvků (LINQ na XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e961f-102">How to filter on element names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="e961f-103">Při volání jedné z metod, které vracejí <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, můžete filtrovat na název prvku.</span><span class="sxs-lookup"><span data-stu-id="e961f-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e961f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e961f-104">Example</span></span>  
 <span data-ttu-id="e961f-105">Tento příklad načte kolekci potomků, která je filtrována tak, aby obsahovala pouze potomky se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="e961f-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="e961f-106">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Typický nákupní objednávka (LINQ to XML).](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)</span><span class="sxs-lookup"><span data-stu-id="e961f-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="e961f-107">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e961f-107">This code produces the following output:</span></span>  
  
```output  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="e961f-108">Ostatní metody, <xref:System.Collections.Generic.IEnumerable%601> které <xref:System.Xml.Linq.XElement> vracejí kolekce postupujte podle stejného vzoru.</span><span class="sxs-lookup"><span data-stu-id="e961f-108">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="e961f-109">Jejich podpisy jsou <xref:System.Xml.Linq.XContainer.Elements%2A> <xref:System.Xml.Linq.XContainer.Descendants%2A>podobné a .</span><span class="sxs-lookup"><span data-stu-id="e961f-109">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="e961f-110">Následuje úplný seznam metod, které mají podobné podpisy metody:</span><span class="sxs-lookup"><span data-stu-id="e961f-110">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="e961f-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="e961f-111">Example</span></span>  
 <span data-ttu-id="e961f-112">Následující příklad ukazuje stejný dotaz pro jazyk XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e961f-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="e961f-113">Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e961f-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="e961f-114">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Typická nákupní objednávka v oboru názvů](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="e961f-114">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="e961f-115">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e961f-115">This code produces the following output:</span></span>  
  
```output  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="e961f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e961f-116">See also</span></span>

- [<span data-ttu-id="e961f-117">LINQ na osy XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e961f-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
