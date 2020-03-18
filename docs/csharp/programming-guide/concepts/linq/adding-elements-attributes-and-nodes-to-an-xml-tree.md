---
title: Přidání prvků, atributů a uzlů do stromu XML (C#)
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 20d8d9d9c592f5f570d7c94298dcee41763c1f1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169572"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a><span data-ttu-id="6fe73-102">Přidání prvků, atributů a uzlů do stromu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6fe73-102">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>
<span data-ttu-id="6fe73-103">Do existujícího stromu XML můžete přidat obsah (prvky, atributy, komentáře, pokyny pro zpracování, text a CDATA).</span><span class="sxs-lookup"><span data-stu-id="6fe73-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="6fe73-104">Metody přidávání obsahu</span><span class="sxs-lookup"><span data-stu-id="6fe73-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="6fe73-105">Následující metody přidávají podřízený obsah do aplikace <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>:</span><span class="sxs-lookup"><span data-stu-id="6fe73-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="6fe73-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="6fe73-106">Method</span></span>|<span data-ttu-id="6fe73-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6fe73-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="6fe73-108">Přidá obsah na konci podřízeného <xref:System.Xml.Linq.XContainer>obsahu .</span><span class="sxs-lookup"><span data-stu-id="6fe73-108">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="6fe73-109">Přidá obsah na začátku podřízeného obsahu . <xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="6fe73-109">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="6fe73-110">Následující metody přidávají obsah jako <xref:System.Xml.Linq.XNode>uzly na stejné úrovni .</span><span class="sxs-lookup"><span data-stu-id="6fe73-110">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="6fe73-111">Nejběžnější uzel, do kterého přidáte obsah <xref:System.Xml.Linq.XElement>na stejné úrovni, je , i když <xref:System.Xml.Linq.XText> můžete <xref:System.Xml.Linq.XComment>přidat platný obsah na stejné úrovni do jiných typů uzlů, jako jsou nebo .</span><span class="sxs-lookup"><span data-stu-id="6fe73-111">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="6fe73-112">Metoda</span><span class="sxs-lookup"><span data-stu-id="6fe73-112">Method</span></span>|<span data-ttu-id="6fe73-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6fe73-113">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="6fe73-114">Přidá obsah <xref:System.Xml.Linq.XNode>za .</span><span class="sxs-lookup"><span data-stu-id="6fe73-114">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="6fe73-115">Přidá obsah <xref:System.Xml.Linq.XNode>před .</span><span class="sxs-lookup"><span data-stu-id="6fe73-115">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6fe73-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="6fe73-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6fe73-117">Popis</span><span class="sxs-lookup"><span data-stu-id="6fe73-117">Description</span></span>  
 <span data-ttu-id="6fe73-118">Následující příklad vytvoří dva stromy XML a potom upraví jeden ze stromů.</span><span class="sxs-lookup"><span data-stu-id="6fe73-118">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6fe73-119">kód</span><span class="sxs-lookup"><span data-stu-id="6fe73-119">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="6fe73-120">Komentáře</span><span class="sxs-lookup"><span data-stu-id="6fe73-120">Comments</span></span>  
 <span data-ttu-id="6fe73-121">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6fe73-121">This code produces the following output:</span></span>  
  
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
  