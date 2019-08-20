---
title: 'Postupy: Filtrovat podle názvů elementů (LINQ to XML)C#()'
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 9febe3b834261326bab3e82d87c476f99d4e6b1f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593816"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="57441-102">Postupy: Filtrovat podle názvů elementů (LINQ to XML)C#()</span><span class="sxs-lookup"><span data-stu-id="57441-102">How to: Filter on Element Names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="57441-103">Při volání jedné z metod, které vrací <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>hodnotu, můžete filtrovat podle názvu elementu.</span><span class="sxs-lookup"><span data-stu-id="57441-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57441-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="57441-104">Example</span></span>  
 <span data-ttu-id="57441-105">Tento příklad načte kolekci následníků, které jsou filtrovány tak, aby obsahovaly pouze následníky se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="57441-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="57441-106">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="57441-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="57441-107">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="57441-107">This code produces the following output:</span></span>  
  
```  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="57441-108">Jiné metody, které vracejí <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> kolekce, budou následovat po stejném vzoru.</span><span class="sxs-lookup"><span data-stu-id="57441-108">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="57441-109">Jejich signatury jsou podobné <xref:System.Xml.Linq.XContainer.Elements%2A> a <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="57441-109">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="57441-110">Následuje úplný seznam metod, které mají podobné signatury metody:</span><span class="sxs-lookup"><span data-stu-id="57441-110">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="57441-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="57441-111">Example</span></span>  
 <span data-ttu-id="57441-112">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="57441-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="57441-113">Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="57441-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="57441-114">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Typická nákupní objednávka v oboru názvů](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="57441-114">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="57441-115">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="57441-115">This code produces the following output:</span></span>  
  
```  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="57441-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57441-116">See also</span></span>

- [<span data-ttu-id="57441-117">LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="57441-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
