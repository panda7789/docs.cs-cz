---
title: Přidání elementů, atributů a uzlů do stromu XML (C#)
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 87b63df1011af9594ff44bed6385f9d82dee08a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585874"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a><span data-ttu-id="fd2d9-102">Přidání elementů, atributů a uzlů do stromu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="fd2d9-102">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>
<span data-ttu-id="fd2d9-103">Obsah (elementy, atributy, komentáře, pokyny pro zpracování, text a CDATA) můžete přidat do existující stromu XML.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="fd2d9-104">Metody pro přidávání obsahu</span><span class="sxs-lookup"><span data-stu-id="fd2d9-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="fd2d9-105">Podřízený obsah k přidání následujících metod <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>:</span><span class="sxs-lookup"><span data-stu-id="fd2d9-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="fd2d9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="fd2d9-106">Method</span></span>|<span data-ttu-id="fd2d9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fd2d9-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="fd2d9-108">Přidá obsah na konci podřízený obsah <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-108">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="fd2d9-109">Přidá obsah na začátku podřízený obsah <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-109">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="fd2d9-110">Následující metody přidat jako uzly na stejné úrovni obsah <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-110">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="fd2d9-111">Nejběžnější uzel, do které přidáte na stejné úrovni obsah je <xref:System.Xml.Linq.XElement>, i když přidáte na stejné úrovni platný obsah na jiné typy uzlů, jako <xref:System.Xml.Linq.XText> nebo <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-111">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="fd2d9-112">Metoda</span><span class="sxs-lookup"><span data-stu-id="fd2d9-112">Method</span></span>|<span data-ttu-id="fd2d9-113">Popis</span><span class="sxs-lookup"><span data-stu-id="fd2d9-113">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="fd2d9-114">Přidá obsah po <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-114">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="fd2d9-115">Přidá obsah před <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-115">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fd2d9-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd2d9-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="fd2d9-117">Popis</span><span class="sxs-lookup"><span data-stu-id="fd2d9-117">Description</span></span>  
 <span data-ttu-id="fd2d9-118">Následující příklad vytvoří dvě stromů XML a pak jednu z stromy upraví.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-118">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="fd2d9-119">Kód</span><span class="sxs-lookup"><span data-stu-id="fd2d9-119">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="fd2d9-120">Komentáře</span><span class="sxs-lookup"><span data-stu-id="fd2d9-120">Comments</span></span>  
 <span data-ttu-id="fd2d9-121">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="fd2d9-121">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fd2d9-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd2d9-122">See also</span></span>

- [<span data-ttu-id="fd2d9-123">Změna stromů XML (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="fd2d9-123">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
