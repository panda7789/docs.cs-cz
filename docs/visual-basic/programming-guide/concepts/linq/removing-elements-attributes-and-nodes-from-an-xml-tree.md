---
title: Odebrání elementů, atributů a uzlů ze stromu XML
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: 4cce1eff469c1f737e18b88cce30155547d9f11b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348953"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a><span data-ttu-id="54444-102">Odebrání elementů, atributů a uzlů ze stromu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54444-102">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="54444-103">Můžete upravit strom XML, odebrat prvky, atributy a jiné typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="54444-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="54444-104">Odebrání jednoho prvku nebo jednoho atributu z dokumentu XML je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="54444-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="54444-105">Při odebírání kolekcí prvků nebo atributů byste však měli nejprve vyhodnotit kolekci do seznamu a poté prvky nebo atributy odstranit ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="54444-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="54444-106">Nejlepším řešením je použít metodu rozšíření <xref:System.Xml.Linq.Extensions.Remove%2A>, která to provede za vás.</span><span class="sxs-lookup"><span data-stu-id="54444-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="54444-107">Hlavním důvodem pro toto je to, že většina kolekcí, které načítáte ze stromu XML, je výsledkem použití odloženého provedení.</span><span class="sxs-lookup"><span data-stu-id="54444-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="54444-108">Pokud je nebudete napřed vyhodnotit do seznamu, nebo pokud nepoužíváte rozšiřující metody, je možné narazit na určitou třídu chyb.</span><span class="sxs-lookup"><span data-stu-id="54444-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="54444-109">Další informace naleznete v tématu [smíšený deklarativní kód/nepodmíněný kód chyby (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="54444-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="54444-110">Následující metody odstraňují uzly a atributy ze stromu XML.</span><span class="sxs-lookup"><span data-stu-id="54444-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="54444-111">Metoda</span><span class="sxs-lookup"><span data-stu-id="54444-111">Method</span></span>|<span data-ttu-id="54444-112">Popis</span><span class="sxs-lookup"><span data-stu-id="54444-112">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="54444-113">Odebere <xref:System.Xml.Linq.XAttribute> z nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="54444-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="54444-114">Odebere podřízené uzly z <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="54444-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="54444-115">Odebere obsah a atributy z <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="54444-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="54444-116">Odebere atributy <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="54444-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="54444-117">Pokud předáte `null` pro hodnotu, pak atribut odebere.</span><span class="sxs-lookup"><span data-stu-id="54444-117">If you pass `null` for value, then removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="54444-118">Pokud předáte `null` pro hodnotu, pak se podřízený element odstraní.</span><span class="sxs-lookup"><span data-stu-id="54444-118">If you pass `null` for value, then removes the child element.</span></span>|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="54444-119">Odebere <xref:System.Xml.Linq.XNode> z nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="54444-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="54444-120">Odebere všechny atributy nebo elementy ve zdrojové kolekci z jejího nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="54444-120">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="54444-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="54444-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="54444-122">Popis</span><span class="sxs-lookup"><span data-stu-id="54444-122">Description</span></span>  
 <span data-ttu-id="54444-123">Tento příklad ukazuje tři přístupy k odebrání prvků.</span><span class="sxs-lookup"><span data-stu-id="54444-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="54444-124">Nejprve odebere jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="54444-124">First, it removes a single element.</span></span> <span data-ttu-id="54444-125">Za druhé načte kolekci prvků, materializuje je pomocí operátoru <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> a kolekce se odstraní.</span><span class="sxs-lookup"><span data-stu-id="54444-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="54444-126">Nakonec načte kolekci prvků a odebere je pomocí metody rozšíření <xref:System.Xml.Linq.Extensions.Remove%2A>.</span><span class="sxs-lookup"><span data-stu-id="54444-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="54444-127">Další informace o operátoru <xref:System.Linq.Enumerable.ToList%2A> naleznete v tématu [Převod datových typů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="54444-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="54444-128">Kód</span><span class="sxs-lookup"><span data-stu-id="54444-128">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="54444-129">Komentáře</span><span class="sxs-lookup"><span data-stu-id="54444-129">Comments</span></span>  
 <span data-ttu-id="54444-130">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="54444-130">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="54444-131">Všimněte si, že první podřízená prvek byl odebrán z `Child1`.</span><span class="sxs-lookup"><span data-stu-id="54444-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="54444-132">Všechny prvky podřízené byly odebrány z `Child2` a z `Child3`.</span><span class="sxs-lookup"><span data-stu-id="54444-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54444-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54444-133">See also</span></span>

- [<span data-ttu-id="54444-134">Úprava stromů XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54444-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
