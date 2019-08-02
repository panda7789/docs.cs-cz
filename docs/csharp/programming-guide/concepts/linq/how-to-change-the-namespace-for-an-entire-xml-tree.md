---
title: 'Postupy: Změna oboru názvů pro celý strom XML (C#)'
ms.date: 07/20/2015
ms.assetid: 1584ff3b-c77d-4241-ab62-80adfb7bfc1b
ms.openlocfilehash: 80ab1f3b1a6df1debc3d94e89d3e0f3a8d78de7f
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709979"
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-c"></a><span data-ttu-id="3fbf7-102">Postupy: Změna oboru názvů pro celý strom XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3fbf7-102">How to: Change the Namespace for an Entire XML Tree (C#)</span></span>
<span data-ttu-id="3fbf7-103">Někdy je nutné programově změnit obor názvů pro element nebo atribut.</span><span class="sxs-lookup"><span data-stu-id="3fbf7-103">You sometimes have to programmatically change the namespace for an element or an attribute.</span></span> <span data-ttu-id="3fbf7-104">LINQ to XML to usnadňuje.</span><span class="sxs-lookup"><span data-stu-id="3fbf7-104">LINQ to XML makes this easy.</span></span> <span data-ttu-id="3fbf7-105"><xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> Vlastnost lze nastavit.</span><span class="sxs-lookup"><span data-stu-id="3fbf7-105">The <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> property can be set.</span></span> <span data-ttu-id="3fbf7-106">Vlastnost nelze nastavit, ale lze snadno zkopírovat atributy <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>do, odebrat existující atributy a pak přidat nové atributy, které jsou v novém požadovaném oboru názvů. <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3fbf7-106">The <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> property cannot be set, but you can easily copy the attributes into a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, remove the existing attributes, and then add new attributes that are in the new desired namespace.</span></span>  
  
 <span data-ttu-id="3fbf7-107">Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3fbf7-107">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fbf7-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="3fbf7-108">Example</span></span>  
 <span data-ttu-id="3fbf7-109">Následující kód vytvoří dvě stromy XML v žádném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3fbf7-109">The following code creates two XML trees in no namespace.</span></span> <span data-ttu-id="3fbf7-110">Poté změní obor názvů každé z stromů a zkombinuje je do jednoho stromu.</span><span class="sxs-lookup"><span data-stu-id="3fbf7-110">It then changes the namespace of each of the trees, and combines them into a single tree.</span></span>  
  
```csharp  
XElement tree1 = new XElement("Data",  
    new XElement("Child", "content",  
        new XAttribute("MyAttr", "content")  
    )  
);  
XElement tree2 = new XElement("Data",  
    new XElement("Child", "content",  
        new XAttribute("MyAttr", "content")  
    )  
);  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace ad = "http://www.adatum.com";  
// change the namespace of every element and attribute in the first tree  
foreach (XElement el in tree1.DescendantsAndSelf())  
{  
    el.Name = aw.GetName(el.Name.LocalName);  
    List<XAttribute> atList = el.Attributes().ToList();  
    el.Attributes().Remove();  
    foreach (XAttribute at in atList)  
        el.Add(new XAttribute(aw.GetName(at.Name.LocalName), at.Value));  
}  
// change the namespace of every element and attribute in the second tree  
foreach (XElement el in tree2.DescendantsAndSelf())  
{  
    el.Name = ad.GetName(el.Name.LocalName);  
    List<XAttribute> atList = el.Attributes().ToList();  
    el.Attributes().Remove();  
    foreach (XAttribute at in atList)  
        el.Add(new XAttribute(ad.GetName(at.Name.LocalName), at.Value));  
}  
// add attribute namespaces so that the tree will be serialized with  
// the aw and ad namespace prefixes  
tree1.Add(  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com")  
);  
tree2.Add(  
    new XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com")  
);  
// create a new composite tree  
XElement root = new XElement("Root",  
    tree1,  
    tree2  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="3fbf7-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3fbf7-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <aw:Data xmlns:aw="http://www.adventure-works.com">  
    <aw:Child aw:MyAttr="content">content</aw:Child>  
  </aw:Data>  
  <ad:Data xmlns:ad="http://www.adatum.com">  
    <ad:Child ad:MyAttr="content">content</ad:Child>  
  </ad:Data>  
</Root>  
```  
