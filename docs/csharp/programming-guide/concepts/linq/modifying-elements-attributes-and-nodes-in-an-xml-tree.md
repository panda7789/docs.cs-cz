---
title: Úprava prvky, atributy a uzly v Tree3 XML
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: a03045c9a4b7b0fb24bbe5c25211b9626cab9185
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321266"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="494bb-102">Úprava prvky, atributy a uzly ve stromu XML</span><span class="sxs-lookup"><span data-stu-id="494bb-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="494bb-103">Následující tabulka shrnuje metody a vlastnosti, které můžete použít k úpravě prvek a jeho podřízené elementy nebo jeho atributy.</span><span class="sxs-lookup"><span data-stu-id="494bb-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="494bb-104">Upravit následující metody <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="494bb-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="494bb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="494bb-105">Method</span></span>|<span data-ttu-id="494bb-106">Popis</span><span class="sxs-lookup"><span data-stu-id="494bb-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="494bb-107">Nahradí element Analyzovaná XML.</span><span class="sxs-lookup"><span data-stu-id="494bb-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="494bb-108">Odebere všechny obsah elementu (podřízené uzly a atributy).</span><span class="sxs-lookup"><span data-stu-id="494bb-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="494bb-109">Odebere atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="494bb-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="494bb-110">Nahradí všechny obsah elementu (podřízené uzly a atributy).</span><span class="sxs-lookup"><span data-stu-id="494bb-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="494bb-111">Nahradí atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="494bb-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="494bb-112">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="494bb-112">Sets the value of an attribute.</span></span> <span data-ttu-id="494bb-113">Pokud neexistuje, vytvoří atribut.</span><span class="sxs-lookup"><span data-stu-id="494bb-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="494bb-114">Pokud je hodnota nastavená `null`, odebere atribut.</span><span class="sxs-lookup"><span data-stu-id="494bb-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="494bb-115">Nastaví hodnotu podřízený element.</span><span class="sxs-lookup"><span data-stu-id="494bb-115">Sets the value of a child element.</span></span> <span data-ttu-id="494bb-116">Pokud neexistuje, vytvoří elementu.</span><span class="sxs-lookup"><span data-stu-id="494bb-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="494bb-117">Pokud je hodnota nastavená `null`, odebere element.</span><span class="sxs-lookup"><span data-stu-id="494bb-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="494bb-118">Obsah elementu (podřízené uzly) nahradí zadaný text.</span><span class="sxs-lookup"><span data-stu-id="494bb-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="494bb-119">Nastaví hodnotu elementu.</span><span class="sxs-lookup"><span data-stu-id="494bb-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="494bb-120">Upravit následující metody <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="494bb-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="494bb-121">Metoda</span><span class="sxs-lookup"><span data-stu-id="494bb-121">Method</span></span>|<span data-ttu-id="494bb-122">Popis</span><span class="sxs-lookup"><span data-stu-id="494bb-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="494bb-123">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="494bb-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="494bb-124">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="494bb-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="494bb-125">Upravit následující metody <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="494bb-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="494bb-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="494bb-126">Method</span></span>|<span data-ttu-id="494bb-127">Popis</span><span class="sxs-lookup"><span data-stu-id="494bb-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="494bb-128">Nahradí uzlu nový obsah.</span><span class="sxs-lookup"><span data-stu-id="494bb-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="494bb-129">Upravit následující metody <xref:System.Xml.Linq.XContainer> ( <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="494bb-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="494bb-130">Metoda</span><span class="sxs-lookup"><span data-stu-id="494bb-130">Method</span></span>|<span data-ttu-id="494bb-131">Popis</span><span class="sxs-lookup"><span data-stu-id="494bb-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="494bb-132">Podřízené uzly nahradí nový obsah.</span><span class="sxs-lookup"><span data-stu-id="494bb-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="494bb-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="494bb-133">See Also</span></span>  
 [<span data-ttu-id="494bb-134">Úprava XML stromů (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="494bb-134">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
