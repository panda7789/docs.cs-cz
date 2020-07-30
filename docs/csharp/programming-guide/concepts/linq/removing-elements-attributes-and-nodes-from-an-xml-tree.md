---
title: Odebrání elementů, atributů a uzlů ze stromu XML (C#)
description: Naučte se, jak odebrat prvky, atributy a uzly ze stromu XML. Podívejte se na seznam metod odebrání a příkladu kódu.
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 4e753c3d96c4cbc050b08076ca8bff8c17b2e252
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300043"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a><span data-ttu-id="39102-104">Odebrání elementů, atributů a uzlů ze stromu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="39102-104">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>

<span data-ttu-id="39102-105">Můžete upravit strom XML, odebrat prvky, atributy a jiné typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="39102-105">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>

<span data-ttu-id="39102-106">Odebrání jednoho prvku nebo jednoho atributu z dokumentu XML je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="39102-106">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="39102-107">Při odebírání kolekcí prvků nebo atributů byste však měli nejprve vyhodnotit kolekci do seznamu a poté prvky nebo atributy odstranit ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="39102-107">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="39102-108">Nejlepším řešením je použít <xref:System.Xml.Linq.Extensions.Remove%2A> metodu rozšíření, která to provede za vás.</span><span class="sxs-lookup"><span data-stu-id="39102-108">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>

<span data-ttu-id="39102-109">Hlavním důvodem pro toto je to, že většina kolekcí, které načítáte ze stromu XML, je výsledkem použití odloženého provedení.</span><span class="sxs-lookup"><span data-stu-id="39102-109">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="39102-110">Pokud je nebudete napřed vyhodnotit do seznamu, nebo pokud nepoužíváte rozšiřující metody, je možné narazit na určitou třídu chyb.</span><span class="sxs-lookup"><span data-stu-id="39102-110">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="39102-111">Další informace naleznete v tématu [smíšený deklarativní kód/nepodmíněný kód chyby (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="39102-111">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>

<span data-ttu-id="39102-112">Následující metody odstraňují uzly a atributy ze stromu XML.</span><span class="sxs-lookup"><span data-stu-id="39102-112">The following methods remove nodes and attributes from an XML tree.</span></span>

|<span data-ttu-id="39102-113">Metoda</span><span class="sxs-lookup"><span data-stu-id="39102-113">Method</span></span>|<span data-ttu-id="39102-114">Popis</span><span class="sxs-lookup"><span data-stu-id="39102-114">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="39102-115">Odebere <xref:System.Xml.Linq.XAttribute> z jeho nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="39102-115">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="39102-116">Odebere podřízené uzly z <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="39102-116">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="39102-117">Odebere obsah a atributy z <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="39102-117">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="39102-118">Odebere atributy <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="39102-118">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="39102-119">Pokud předáte `null` hodnotu, pak atribut odeberte.</span><span class="sxs-lookup"><span data-stu-id="39102-119">If you pass `null` for value, then removes the attribute.</span></span>|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="39102-120">Pokud předáte `null` hodnotu, pak je podřízený element odebrán.</span><span class="sxs-lookup"><span data-stu-id="39102-120">If you pass `null` for value, then removes the child element.</span></span>|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="39102-121">Odebere <xref:System.Xml.Linq.XNode> z jeho nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="39102-121">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="39102-122">Odebere všechny atributy nebo elementy ve zdrojové kolekci z jejího nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="39102-122">Removes every attribute or element in the source collection from its parent element.</span></span>|

## <a name="example"></a><span data-ttu-id="39102-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="39102-123">Example</span></span>

### <a name="description"></a><span data-ttu-id="39102-124">Popis</span><span class="sxs-lookup"><span data-stu-id="39102-124">Description</span></span>

<span data-ttu-id="39102-125">Tento příklad ukazuje tři přístupy k odebrání prvků.</span><span class="sxs-lookup"><span data-stu-id="39102-125">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="39102-126">Nejprve odebere jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="39102-126">First, it removes a single element.</span></span> <span data-ttu-id="39102-127">Za druhé načte kolekci prvků, materializuje je pomocí <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operátoru a kolekce odebere.</span><span class="sxs-lookup"><span data-stu-id="39102-127">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="39102-128">Nakonec načte kolekci prvků a odebere je pomocí <xref:System.Xml.Linq.Extensions.Remove%2A> metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="39102-128">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>

<span data-ttu-id="39102-129">Další informace o <xref:System.Linq.Enumerable.ToList%2A> operátoru naleznete v tématu [Převod datových typů (C#)](./converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="39102-129">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](./converting-data-types.md).</span></span>

### <a name="code"></a><span data-ttu-id="39102-130">Kód</span><span class="sxs-lookup"><span data-stu-id="39102-130">Code</span></span>

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

### <a name="comments"></a><span data-ttu-id="39102-131">Komentáře</span><span class="sxs-lookup"><span data-stu-id="39102-131">Comments</span></span>

<span data-ttu-id="39102-132">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="39102-132">This code produces the following output:</span></span>

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

<span data-ttu-id="39102-133">Všimněte si, že byl odebrán první podřízený prvek z `Child1` .</span><span class="sxs-lookup"><span data-stu-id="39102-133">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="39102-134">Všechny prvky podřízené byly odebrány z `Child2` a z `Child3` .</span><span class="sxs-lookup"><span data-stu-id="39102-134">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>
