---
title: "Odebrání prvky, atributy a uzly ze stromu XML (C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1745b1ce84b33a67d54f5e752da2ecf9bbfdbc17
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a><span data-ttu-id="a610c-102">Odebrání prvky, atributy a uzly ze stromu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a610c-102">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>
<span data-ttu-id="a610c-103">Ve stromu XML, můžete upravit odebrání prvky, atributy a jiné typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="a610c-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="a610c-104">Odebrání jeden element nebo jeden atribut z dokumentu XML je jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="a610c-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="a610c-105">Ale při odebírání kolekce elementy nebo atributy, doporučujeme nejdřív vyhodnotit kolekce do seznamu a pak odstraňte elementy nebo atributy ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="a610c-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="a610c-106">Nejlepším postupem je použití <xref:System.Xml.Linq.Extensions.Remove%2A> metody rozšíření, která bude to dělají za vás.</span><span class="sxs-lookup"><span data-stu-id="a610c-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="a610c-107">Hlavním důvodem tohoto postupu je výsledkem většinu kolekce, které je načíst ze stromu XML jsou chybná pomocí odložené provedení.</span><span class="sxs-lookup"><span data-stu-id="a610c-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="a610c-108">Pokud jste není nejdřív vyhodnotit je do seznamu, nebo pokud nepoužijete rozšiřující metody, je možné dojde k určité třídě chyby.</span><span class="sxs-lookup"><span data-stu-id="a610c-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="a610c-109">Další informace najdete v tématu [smíšený deklarativní kód nebo imperativní kód chyby (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a610c-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="a610c-110">Následující metody odebrat uzly a atributy ze stromu XML.</span><span class="sxs-lookup"><span data-stu-id="a610c-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="a610c-111">Metoda</span><span class="sxs-lookup"><span data-stu-id="a610c-111">Method</span></span>|<span data-ttu-id="a610c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a610c-112">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="a610c-113">Odebere <xref:System.Xml.Linq.XAttribute> z nadřazené.</span><span class="sxs-lookup"><span data-stu-id="a610c-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="a610c-114">Odebere z podřízených uzlů <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="a610c-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="a610c-115">Odstraní obsah a pro atributy z <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="a610c-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="a610c-116">Odebere atributy <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="a610c-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="a610c-117">Pokud předáte `null` pro hodnotu, pak odebere atribut.</span><span class="sxs-lookup"><span data-stu-id="a610c-117">If you pass `null` for value, then removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="a610c-118">Pokud předáte `null` pro hodnotu, pak odebere podřízený element.</span><span class="sxs-lookup"><span data-stu-id="a610c-118">If you pass `null` for value, then removes the child element.</span></span>|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="a610c-119">Odebere <xref:System.Xml.Linq.XNode> z nadřazené.</span><span class="sxs-lookup"><span data-stu-id="a610c-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="a610c-120">Odebere každý atribut nebo element ve zdrojové kolekci ze svého nadřízeného elementu.</span><span class="sxs-lookup"><span data-stu-id="a610c-120">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a610c-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="a610c-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a610c-122">Popis</span><span class="sxs-lookup"><span data-stu-id="a610c-122">Description</span></span>  
 <span data-ttu-id="a610c-123">Tento příklad ukazuje tři metody odebírání elementů.</span><span class="sxs-lookup"><span data-stu-id="a610c-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="a610c-124">Nejprve odebere jeden element.</span><span class="sxs-lookup"><span data-stu-id="a610c-124">First, it removes a single element.</span></span> <span data-ttu-id="a610c-125">Druhý, načte kolekci elementů, bude je realizována pomocí <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operátor a také odebere kolekce.</span><span class="sxs-lookup"><span data-stu-id="a610c-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="a610c-126">Nakonec načte kolekci elementů a odebere je pomocí <xref:System.Xml.Linq.Extensions.Remove%2A> metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="a610c-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="a610c-127">Další informace o <xref:System.Linq.Enumerable.ToList%2A> operátor, najdete v části [převádění datových typů (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="a610c-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="a610c-128">Kód</span><span class="sxs-lookup"><span data-stu-id="a610c-128">Code</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
    <Child1>  
        <GrandChild1/>  
        <GrandChild2/>  
        <GrandChild3/>  
    </Child1>  
    <Child2>  
        <GrandChild4/>  
        <GrandChild5/>  
        <GrandChild6/>  
    </Child2>  
    <Child3>  
        <GrandChild7/>  
        <GrandChild8/>  
        <GrandChild9/>  
    </Child3>  
</Root>");  
root.Element("Child1").Element("GrandChild1").Remove();  
root.Element("Child2").Elements().ToList().Remove();  
root.Element("Child3").Elements().Remove();  
Console.WriteLine(root);  
```  
  
### <a name="comments"></a><span data-ttu-id="a610c-129">Komentáře</span><span class="sxs-lookup"><span data-stu-id="a610c-129">Comments</span></span>  
 <span data-ttu-id="a610c-130">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a610c-130">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>  
    <GrandChild2 />  
    <GrandChild3 />  
  </Child1>  
  <Child2 />  
  <Child3 />  
</Root>  
```  
  
 <span data-ttu-id="a610c-131">Všimněte si, že první podřízený prvek byl odebrán z `Child1`.</span><span class="sxs-lookup"><span data-stu-id="a610c-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="a610c-132">Všechny podřízené elementy byly odebrány z `Child2` a z `Child3`.</span><span class="sxs-lookup"><span data-stu-id="a610c-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a610c-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="a610c-133">See Also</span></span>  
 [<span data-ttu-id="a610c-134">Úprava XML stromů (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a610c-134">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
