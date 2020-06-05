---
title: 'Postupy: Změna názvového prostoru pro celý strom XML'
ms.date: 07/20/2015
ms.assetid: 1837324b-5cb5-4fa8-95b9-3071efa0f913
ms.openlocfilehash: 11938b575ed5133d930e585dbe4d744e3168cced
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374976"
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-visual-basic"></a><span data-ttu-id="c5f8c-102">Postupy: Změna oboru názvů pro celý strom XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5f8c-102">How to: Change the Namespace for an Entire XML Tree (Visual Basic)</span></span>
<span data-ttu-id="c5f8c-103">Někdy je nutné programově změnit obor názvů pro element nebo atribut.</span><span class="sxs-lookup"><span data-stu-id="c5f8c-103">You sometimes have to programmatically change the namespace for an element or an attribute.</span></span> <span data-ttu-id="c5f8c-104">LINQ to XML to usnadňuje.</span><span class="sxs-lookup"><span data-stu-id="c5f8c-104">LINQ to XML makes this easy.</span></span> <span data-ttu-id="c5f8c-105"><xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType>Vlastnost lze nastavit.</span><span class="sxs-lookup"><span data-stu-id="c5f8c-105">The <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> property can be set.</span></span> <span data-ttu-id="c5f8c-106"><xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType>Vlastnost nelze nastavit, ale lze snadno zkopírovat atributy do <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> , odebrat existující atributy a pak přidat nové atributy, které jsou v novém požadovaném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c5f8c-106">The <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> property cannot be set, but you can easily copy the attributes into a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, remove the existing attributes, and then add new attributes that are in the new desired namespace.</span></span>  
  
 <span data-ttu-id="c5f8c-107">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c5f8c-107">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5f8c-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="c5f8c-108">Example</span></span>  
 <span data-ttu-id="c5f8c-109">Následující kód vytvoří dvě stromy XML v žádném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c5f8c-109">The following code creates two XML trees in no namespace.</span></span> <span data-ttu-id="c5f8c-110">Poté změní obor názvů každé z stromů a zkombinuje je do jednoho stromu.</span><span class="sxs-lookup"><span data-stu-id="c5f8c-110">It then changes the namespace of each of the trees, and combines them into a single tree.</span></span>  
  
```vb  
Dim tree1 As XElement = _  
    <Data>  
        <Child MyAttr="content">content</Child>  
    </Data>  
Dim tree2 As XElement = _  
    <Data>  
        <Child MyAttr="content">content</Child>  
    </Data>  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim ad As XNamespace = "http://www.adatum.com"  
' change the namespace of every element and attribute in the first tree  
For Each el As XElement In tree1.DescendantsAndSelf  
    el.Name = aw.GetName(el.Name.LocalName)  
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()  
    el.Attributes().Remove()  
    For Each at As XAttribute In atList  
        el.Add(New XAttribute(aw.GetName(at.Name.LocalName), at.Value))  
    Next  
Next  
' change the namespace of every element and attribute in the second tree  
For Each el As XElement In tree2.DescendantsAndSelf()  
    el.Name = ad.GetName(el.Name.LocalName)  
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()  
    el.Attributes().Remove()  
    For Each at As XAttribute In atList  
        el.Add(New XAttribute(ad.GetName(at.Name.LocalName), at.Value))  
    Next  
Next  
' add attribute namespaces so that the tree will be serialized with  
' the aw and ad namespace prefixes  
tree1.Add( _  
    New XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com") _  
)  
tree2.Add( _  
    New XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com") _  
)  
' create a new composite tree  
Dim root As XElement = _  
    <Root>  
        <%= tree1 %>  
        <%= tree2 %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="c5f8c-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c5f8c-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5f8c-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5f8c-112">See also</span></span>

- [<span data-ttu-id="c5f8c-113">Úprava stromů XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5f8c-113">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](modifying-xml-trees-linq-to-xml.md)
