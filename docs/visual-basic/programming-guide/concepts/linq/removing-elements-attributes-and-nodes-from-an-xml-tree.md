---
title: Odebrání elementů, atributů a uzlů ze stromu XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: 85a7a3b4047e269c562177cfa045b952472aaac2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814910"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a><span data-ttu-id="20a7c-102">Odebrání elementů, atributů a uzlů ze stromu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20a7c-102">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="20a7c-103">Můžete upravit stromu XML, odebrání elementů, atributů a dalších typů uzlů.</span><span class="sxs-lookup"><span data-stu-id="20a7c-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="20a7c-104">Odebrání jeden element nebo jeden atribut z dokumentu XML je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="20a7c-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="20a7c-105">Ale při odstraňování kolekce elementy nebo atributy, musí nejprve sloučit kolekci do seznamu a pak odstraníte elementy nebo atributy ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="20a7c-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="20a7c-106">Nejlepší možností je použít <xref:System.Xml.Linq.Extensions.Remove%2A> metodu rozšíření, která to udělal za vás.</span><span class="sxs-lookup"><span data-stu-id="20a7c-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="20a7c-107">Hlavním důvodem pro to je, že jsou výsledkem většinu kolekce, které se načítají ze stromu XML pomocí odloženého provedení.</span><span class="sxs-lookup"><span data-stu-id="20a7c-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="20a7c-108">Pokud jste není nejprve materializovat je do seznamu, nebo pokud používáte metody rozšíření, je možné se setkat se třídy chyb.</span><span class="sxs-lookup"><span data-stu-id="20a7c-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="20a7c-109">Další informace najdete v tématu [smíšené deklarativní kód/dnešní kód chyby (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="20a7c-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="20a7c-110">Následující metody odebrání uzlů a atributy ze stromu XML.</span><span class="sxs-lookup"><span data-stu-id="20a7c-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="20a7c-111">Metoda</span><span class="sxs-lookup"><span data-stu-id="20a7c-111">Method</span></span>|<span data-ttu-id="20a7c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="20a7c-112">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="20a7c-113">Odebere <xref:System.Xml.Linq.XAttribute> od svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="20a7c-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="20a7c-114">Odebere podřízené uzly ze <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="20a7c-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="20a7c-115">Odstraní obsah a atributy ze <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="20a7c-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="20a7c-116">Odebere atributy <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="20a7c-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="20a7c-117">Pokud předáte `null` pro hodnotu, pak taky odebere atribut.</span><span class="sxs-lookup"><span data-stu-id="20a7c-117">If you pass `null` for value, then removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="20a7c-118">Pokud předáte `null` pro hodnotu, pak taky odebere podřízený element.</span><span class="sxs-lookup"><span data-stu-id="20a7c-118">If you pass `null` for value, then removes the child element.</span></span>|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="20a7c-119">Odebere <xref:System.Xml.Linq.XNode> od svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="20a7c-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="20a7c-120">Odebere každý atribut nebo element ve zdrojové kolekci ze svého nadřízeného elementu.</span><span class="sxs-lookup"><span data-stu-id="20a7c-120">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="20a7c-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="20a7c-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="20a7c-122">Popis</span><span class="sxs-lookup"><span data-stu-id="20a7c-122">Description</span></span>  
 <span data-ttu-id="20a7c-123">Tento příklad ukazuje tři přístupy k odebrání prvků.</span><span class="sxs-lookup"><span data-stu-id="20a7c-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="20a7c-124">Nejprve se odebere jeden element.</span><span class="sxs-lookup"><span data-stu-id="20a7c-124">First, it removes a single element.</span></span> <span data-ttu-id="20a7c-125">Za druhé, načte kolekci elementů, bude je realizována pomocí <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operátorů a odebere kolekce.</span><span class="sxs-lookup"><span data-stu-id="20a7c-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="20a7c-126">A konečně, načte kolekci elementů a odebere je pomocí <xref:System.Xml.Linq.Extensions.Remove%2A> – metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="20a7c-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="20a7c-127">Další informace o <xref:System.Linq.Enumerable.ToList%2A> operátoru, naleznete v tématu [převádění datových typů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="20a7c-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="20a7c-128">Kód</span><span class="sxs-lookup"><span data-stu-id="20a7c-128">Code</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
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
    </Root>  
root.<Child1>.<GrandChild1>.Remove()  
root.<Child2>.Elements().ToList().Remove()  
root.<Child3>.Elements().Remove()  
Console.WriteLine(root)  
```  
  
### <a name="comments"></a><span data-ttu-id="20a7c-129">Komentáře</span><span class="sxs-lookup"><span data-stu-id="20a7c-129">Comments</span></span>  
 <span data-ttu-id="20a7c-130">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="20a7c-130">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="20a7c-131">Všimněte si, že první podřízený element byl odebrán z `Child1`.</span><span class="sxs-lookup"><span data-stu-id="20a7c-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="20a7c-132">Všechny podřízené prvky byly odebrány z `Child2` a z `Child3`.</span><span class="sxs-lookup"><span data-stu-id="20a7c-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20a7c-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20a7c-133">See also</span></span>

- [<span data-ttu-id="20a7c-134">Změna stromů XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20a7c-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
