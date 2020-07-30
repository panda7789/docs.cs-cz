---
title: Jak filtrovat názvy elementů (LINQ to XML) (C#)
description: Naučte se filtrovat název elementu při volání metody, která vrací IEnumerable typu XElement.
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: be660a69b8d860ad907661ce17002379b8842121
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301746"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="5d1a5-103">Jak filtrovat názvy elementů (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5d1a5-103">How to filter on element names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="5d1a5-104">Při volání jedné z metod, které vrací hodnotu <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , můžete filtrovat podle názvu elementu.</span><span class="sxs-lookup"><span data-stu-id="5d1a5-104">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d1a5-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="5d1a5-105">Example</span></span>  
 <span data-ttu-id="5d1a5-106">Tento příklad načte kolekci následníků, které jsou filtrovány tak, aby obsahovaly pouze následníky se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="5d1a5-106">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="5d1a5-107">Tento příklad používá následující dokument XML: [vzorový soubor XML: typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="5d1a5-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="5d1a5-108">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5d1a5-108">This code produces the following output:</span></span>  
  
```output  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="5d1a5-109">Jiné metody, které vracejí <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> kolekce, budou následovat po stejném vzoru.</span><span class="sxs-lookup"><span data-stu-id="5d1a5-109">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="5d1a5-110">Jejich signatury jsou podobné <xref:System.Xml.Linq.XContainer.Elements%2A> a <xref:System.Xml.Linq.XContainer.Descendants%2A> .</span><span class="sxs-lookup"><span data-stu-id="5d1a5-110">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="5d1a5-111">Následuje úplný seznam metod, které mají podobné signatury metody:</span><span class="sxs-lookup"><span data-stu-id="5d1a5-111">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="5d1a5-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="5d1a5-112">Example</span></span>  
 <span data-ttu-id="5d1a5-113">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5d1a5-113">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="5d1a5-114">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5d1a5-114">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="5d1a5-115">Tento příklad používá následující dokument XML: [ukázkový soubor XML: typická nákupní objednávka v oboru názvů](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="5d1a5-115">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="5d1a5-116">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5d1a5-116">This code produces the following output:</span></span>  
  
```output  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d1a5-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d1a5-117">See also</span></span>

- [<span data-ttu-id="5d1a5-118">LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="5d1a5-118">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
