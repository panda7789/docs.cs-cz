---
title: Odebrání prvků, atributů a uzlů ze stromu XML (C#)
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: badaa6bab35367d62a73f56c5221cb7d6d4a45f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591256"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a><span data-ttu-id="89535-102">Odebrání prvků, atributů a uzlů ze stromu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="89535-102">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>

<span data-ttu-id="89535-103">Můžete upravit strom XML, odebrat prvky, atributy a další typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="89535-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>

<span data-ttu-id="89535-104">Odebrání jednoho prvku nebo jednoho atributu z dokumentu XML je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="89535-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="89535-105">Však při odebírání kolekce prvků nebo atributů, měli byste nejprve zhmotnit kolekci do seznamu a potom odstranit prvky nebo atributy ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="89535-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="89535-106">Nejlepším přístupem je použití <xref:System.Xml.Linq.Extensions.Remove%2A> metody rozšíření, která to udělá za vás.</span><span class="sxs-lookup"><span data-stu-id="89535-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>

<span data-ttu-id="89535-107">Hlavním důvodem je, že většina kolekcí, které načtete ze stromu XML, jsou výsledkem pomocí odloženého spuštění.</span><span class="sxs-lookup"><span data-stu-id="89535-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="89535-108">Pokud je nejprve nezhmotníte do seznamu nebo pokud nepoužíváte metody rozšíření, je možné se setkat s určitou třídou chyb.</span><span class="sxs-lookup"><span data-stu-id="89535-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="89535-109">Další informace naleznete [v tématu Smíšené deklarativní kód/imperativní kód chyby (LINQ do XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="89535-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>

<span data-ttu-id="89535-110">Následující metody odeberou uzly a atributy ze stromu XML.</span><span class="sxs-lookup"><span data-stu-id="89535-110">The following methods remove nodes and attributes from an XML tree.</span></span>

|<span data-ttu-id="89535-111">Metoda</span><span class="sxs-lookup"><span data-stu-id="89535-111">Method</span></span>|<span data-ttu-id="89535-112">Popis</span><span class="sxs-lookup"><span data-stu-id="89535-112">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="89535-113">Odebere <xref:System.Xml.Linq.XAttribute> a z jeho nadřazené.</span><span class="sxs-lookup"><span data-stu-id="89535-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="89535-114">Odebere podřízené uzly z <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="89535-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="89535-115">Odebere obsah a atributy z . <xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="89535-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="89535-116">Odebere atributy . <xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="89535-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="89535-117">Pokud předáte `null` hodnotu, odebere atribut.</span><span class="sxs-lookup"><span data-stu-id="89535-117">If you pass `null` for value, then removes the attribute.</span></span>|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="89535-118">Pokud předáte `null` hodnotu, odebere podřízený prvek.</span><span class="sxs-lookup"><span data-stu-id="89535-118">If you pass `null` for value, then removes the child element.</span></span>|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="89535-119">Odebere <xref:System.Xml.Linq.XNode> a z jeho nadřazené.</span><span class="sxs-lookup"><span data-stu-id="89535-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="89535-120">Odebere každý atribut nebo prvek ve zdrojové kolekci z nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="89535-120">Removes every attribute or element in the source collection from its parent element.</span></span>|

## <a name="example"></a><span data-ttu-id="89535-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="89535-121">Example</span></span>

### <a name="description"></a><span data-ttu-id="89535-122">Popis</span><span class="sxs-lookup"><span data-stu-id="89535-122">Description</span></span>

<span data-ttu-id="89535-123">Tento příklad ukazuje tři přístupy k odebrání prvků.</span><span class="sxs-lookup"><span data-stu-id="89535-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="89535-124">Nejprve odebere jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="89535-124">First, it removes a single element.</span></span> <span data-ttu-id="89535-125">Za druhé načte kolekci prvků, materializes <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> je pomocí operátoru a odebere kolekci.</span><span class="sxs-lookup"><span data-stu-id="89535-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="89535-126">Nakonec načte kolekci prvků a odebere <xref:System.Xml.Linq.Extensions.Remove%2A> je pomocí metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="89535-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>

<span data-ttu-id="89535-127">Další informace o <xref:System.Linq.Enumerable.ToList%2A> operátoru naleznete v [tématu Převod datových typů (C#)](./converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="89535-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](./converting-data-types.md).</span></span>

### <a name="code"></a><span data-ttu-id="89535-128">kód</span><span class="sxs-lookup"><span data-stu-id="89535-128">Code</span></span>

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

### <a name="comments"></a><span data-ttu-id="89535-129">Komentáře</span><span class="sxs-lookup"><span data-stu-id="89535-129">Comments</span></span>

<span data-ttu-id="89535-130">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="89535-130">This code produces the following output:</span></span>

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

<span data-ttu-id="89535-131">Všimněte si, že první prvek `Child1`vnouče byl odebrán z .</span><span class="sxs-lookup"><span data-stu-id="89535-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="89535-132">Všechny prvky vnoučat byly `Child2` odebrány z a z `Child3`.</span><span class="sxs-lookup"><span data-stu-id="89535-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>
