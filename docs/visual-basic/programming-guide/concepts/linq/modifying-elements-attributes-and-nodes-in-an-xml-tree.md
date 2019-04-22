---
title: Změna elementů, atributů a uzlů v Tree1 XML
ms.date: 07/20/2015
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
ms.openlocfilehash: d548e6f5912437e5c5df27f55fcdb28990e92c8d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814897"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="ac1fe-102">Změna elementů, atributů a uzlů ve stromu XML</span><span class="sxs-lookup"><span data-stu-id="ac1fe-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="ac1fe-103">Následující tabulka shrnuje metody a vlastnosti, které můžete použít k úpravě prvek a jeho podřízené prvky nebo jeho atributy.</span><span class="sxs-lookup"><span data-stu-id="ac1fe-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="ac1fe-104">Upravte následující metody <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="ac1fe-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="ac1fe-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ac1fe-105">Method</span></span>|<span data-ttu-id="ac1fe-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ac1fe-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="ac1fe-107">Nahradí element analyzovaný kód XML.</span><span class="sxs-lookup"><span data-stu-id="ac1fe-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="ac1fe-108">Odebere všechny obsah elementu (podřízených uzlů a atributy).</span><span class="sxs-lookup"><span data-stu-id="ac1fe-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="ac1fe-109">Odebere atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="ac1fe-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="ac1fe-110">Nahradí všechny obsah elementu (podřízených uzlů a atributy).</span><span class="sxs-lookup"><span data-stu-id="ac1fe-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="ac1fe-111">Nahradí atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="ac1fe-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="ac1fe-112">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="ac1fe-112">Sets the value of an attribute.</span></span> <span data-ttu-id="ac1fe-113">Pokud neexistuje, vytvoří atribut.</span><span class="sxs-lookup"><span data-stu-id="ac1fe-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="ac1fe-114">Pokud je hodnota nastavena na `null`, odebere atribut.</span><span class="sxs-lookup"><span data-stu-id="ac1fe-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="ac1fe-115">Nastaví hodnotu podřízený element.</span><span class="sxs-lookup"><span data-stu-id="ac1fe-115">Sets the value of a child element.</span></span> <span data-ttu-id="ac1fe-116">Vytvoří element, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="ac1fe-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="ac1fe-117">Pokud je hodnota nastavena na `null`, odstraní prvek.</span><span class="sxs-lookup"><span data-stu-id="ac1fe-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="ac1fe-118">Nahradí obsah elementu (podřízené uzly) zadaný text.</span><span class="sxs-lookup"><span data-stu-id="ac1fe-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="ac1fe-119">Nastaví hodnotu elementu.</span><span class="sxs-lookup"><span data-stu-id="ac1fe-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="ac1fe-120">Upravte následující metody <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ac1fe-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="ac1fe-121">Metoda</span><span class="sxs-lookup"><span data-stu-id="ac1fe-121">Method</span></span>|<span data-ttu-id="ac1fe-122">Popis</span><span class="sxs-lookup"><span data-stu-id="ac1fe-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="ac1fe-123">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="ac1fe-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="ac1fe-124">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="ac1fe-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="ac1fe-125">Upravte následující metody <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="ac1fe-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="ac1fe-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="ac1fe-126">Method</span></span>|<span data-ttu-id="ac1fe-127">Popis</span><span class="sxs-lookup"><span data-stu-id="ac1fe-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="ac1fe-128">Nahradí uzlu nový obsah.</span><span class="sxs-lookup"><span data-stu-id="ac1fe-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="ac1fe-129">Upravte následující metody <xref:System.Xml.Linq.XContainer> ( <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="ac1fe-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="ac1fe-130">Metoda</span><span class="sxs-lookup"><span data-stu-id="ac1fe-130">Method</span></span>|<span data-ttu-id="ac1fe-131">Popis</span><span class="sxs-lookup"><span data-stu-id="ac1fe-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="ac1fe-132">Nahradí nový obsah podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="ac1fe-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac1fe-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac1fe-133">See also</span></span>

- [<span data-ttu-id="ac1fe-134">Změna stromů XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac1fe-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
