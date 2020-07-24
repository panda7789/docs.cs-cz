---
title: Přidání elementů, atributů a uzlů do stromu XML (C#)
description: Další informace o metodách přidání obsahu, například prvků, atributů, komentářů, instrukcí pro zpracování a textu do existujícího stromu XML.
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 78a84401494e2d4280799632fa42dc95574e3e10
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105554"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a><span data-ttu-id="8e1e5-103">Přidání elementů, atributů a uzlů do stromu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="8e1e5-103">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>
<span data-ttu-id="8e1e5-104">Do existujícího stromu XML můžete přidat obsah (prvky, atributy, komentáře, instrukce pro zpracování, text a CDATA).</span><span class="sxs-lookup"><span data-stu-id="8e1e5-104">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="8e1e5-105">Metody pro přidání obsahu</span><span class="sxs-lookup"><span data-stu-id="8e1e5-105">Methods for Adding Content</span></span>  
 <span data-ttu-id="8e1e5-106">Následující metody přidají podřízený obsah do <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> :</span><span class="sxs-lookup"><span data-stu-id="8e1e5-106">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="8e1e5-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="8e1e5-107">Method</span></span>|<span data-ttu-id="8e1e5-108">Popis</span><span class="sxs-lookup"><span data-stu-id="8e1e5-108">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="8e1e5-109">Přidá obsah na konec podřízeného obsahu <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="8e1e5-109">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="8e1e5-110">Přidá obsah na začátek podřízeného obsahu <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="8e1e5-110">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="8e1e5-111">Následující metody přidávají obsah jako uzly na stejné úrovni <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="8e1e5-111">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="8e1e5-112">Nejběžnější uzel, do kterého můžete přidat obsah na stejné úrovni <xref:System.Xml.Linq.XElement> , je, i když můžete přidat platný obsah na stejné úrovni k jiným typům uzlů, například <xref:System.Xml.Linq.XText> nebo <xref:System.Xml.Linq.XComment> .</span><span class="sxs-lookup"><span data-stu-id="8e1e5-112">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="8e1e5-113">Metoda</span><span class="sxs-lookup"><span data-stu-id="8e1e5-113">Method</span></span>|<span data-ttu-id="8e1e5-114">Popis</span><span class="sxs-lookup"><span data-stu-id="8e1e5-114">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="8e1e5-115">Přidá obsah za <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="8e1e5-115">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="8e1e5-116">Přidá obsah před <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="8e1e5-116">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8e1e5-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e1e5-117">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8e1e5-118">Popis</span><span class="sxs-lookup"><span data-stu-id="8e1e5-118">Description</span></span>  
 <span data-ttu-id="8e1e5-119">Následující příklad vytvoří dvě stromy XML a pak upraví jednu z stromů.</span><span class="sxs-lookup"><span data-stu-id="8e1e5-119">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8e1e5-120">Kód</span><span class="sxs-lookup"><span data-stu-id="8e1e5-120">Code</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",
    new XElement("Element1", 1),  
    new XElement("Element2", 2),  
    new XElement("Element3", 3),  
    new XElement("Element4", 4),  
    new XElement("Element5", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child2", 2),  
    new XElement("Child3", 3),  
    new XElement("Child4", 4),  
    new XElement("Child5", 5)  
);  
xmlTree.Add(new XElement("NewChild", "new content"));  
xmlTree.Add(  
    from el in srcTree.Elements()  
    where (int)el > 3  
    select el  
);  
// Even though Child9 does not exist in srcTree, the following statement will not  
// throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"));  
Console.WriteLine(xmlTree);  
```  
  
### <a name="comments"></a><span data-ttu-id="8e1e5-121">Komentáře</span><span class="sxs-lookup"><span data-stu-id="8e1e5-121">Comments</span></span>  
 <span data-ttu-id="8e1e5-122">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8e1e5-122">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  