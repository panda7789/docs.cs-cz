---
title: 'Postupy: Filtrovat podle názvů elementů (LINQ to XML)C#()'
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 2a4eccac3bc24005af0efee0785393de00039228
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253809"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="2c669-102">Postupy: Filtrovat podle názvů elementů (LINQ to XML)C#()</span><span class="sxs-lookup"><span data-stu-id="2c669-102">How to: Filter on Element Names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="2c669-103">Při volání jedné z metod, které vrací <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>hodnotu, můžete filtrovat podle názvu elementu.</span><span class="sxs-lookup"><span data-stu-id="2c669-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c669-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c669-104">Example</span></span>  
 <span data-ttu-id="2c669-105">Tento příklad načte kolekci následníků, které jsou filtrovány tak, aby obsahovaly pouze následníky se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="2c669-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="2c669-106">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="2c669-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="2c669-107">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="2c669-107">This code produces the following output:</span></span>  
  
```output  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="2c669-108">Jiné metody, které vracejí <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> kolekce, budou následovat po stejném vzoru.</span><span class="sxs-lookup"><span data-stu-id="2c669-108">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="2c669-109">Jejich signatury jsou podobné <xref:System.Xml.Linq.XContainer.Elements%2A> a <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="2c669-109">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="2c669-110">Následuje úplný seznam metod, které mají podobné signatury metody:</span><span class="sxs-lookup"><span data-stu-id="2c669-110">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="2c669-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c669-111">Example</span></span>  
 <span data-ttu-id="2c669-112">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2c669-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="2c669-113">Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2c669-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="2c669-114">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Typická nákupní objednávka v oboru názvů](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="2c669-114">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="2c669-115">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="2c669-115">This code produces the following output:</span></span>  
  
```output  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c669-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c669-116">See also</span></span>

- [<span data-ttu-id="2c669-117">LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="2c669-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
