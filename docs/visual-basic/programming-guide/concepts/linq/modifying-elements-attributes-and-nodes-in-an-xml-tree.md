---
title: Úprava prvky, atributy a uzly v Tree1 XML
ms.date: 07/20/2015
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
ms.openlocfilehash: 91a7cca2e39e5ddc62d6010fbe4efad9bd7ff3c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645210"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="8ce24-102">Úprava prvky, atributy a uzly ve stromu XML</span><span class="sxs-lookup"><span data-stu-id="8ce24-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="8ce24-103">Následující tabulka shrnuje metody a vlastnosti, které můžete použít k úpravě prvek a jeho podřízené elementy nebo jeho atributy.</span><span class="sxs-lookup"><span data-stu-id="8ce24-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="8ce24-104">Upravit následující metody <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="8ce24-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="8ce24-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8ce24-105">Method</span></span>|<span data-ttu-id="8ce24-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8ce24-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="8ce24-107">Nahradí element Analyzovaná XML.</span><span class="sxs-lookup"><span data-stu-id="8ce24-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="8ce24-108">Odebere všechny obsah elementu (podřízené uzly a atributy).</span><span class="sxs-lookup"><span data-stu-id="8ce24-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="8ce24-109">Odebere atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="8ce24-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="8ce24-110">Nahradí všechny obsah elementu (podřízené uzly a atributy).</span><span class="sxs-lookup"><span data-stu-id="8ce24-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="8ce24-111">Nahradí atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="8ce24-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="8ce24-112">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="8ce24-112">Sets the value of an attribute.</span></span> <span data-ttu-id="8ce24-113">Pokud neexistuje, vytvoří atribut.</span><span class="sxs-lookup"><span data-stu-id="8ce24-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="8ce24-114">Pokud je hodnota nastavená `null`, odebere atribut.</span><span class="sxs-lookup"><span data-stu-id="8ce24-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="8ce24-115">Nastaví hodnotu podřízený element.</span><span class="sxs-lookup"><span data-stu-id="8ce24-115">Sets the value of a child element.</span></span> <span data-ttu-id="8ce24-116">Pokud neexistuje, vytvoří elementu.</span><span class="sxs-lookup"><span data-stu-id="8ce24-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="8ce24-117">Pokud je hodnota nastavená `null`, odebere element.</span><span class="sxs-lookup"><span data-stu-id="8ce24-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="8ce24-118">Obsah elementu (podřízené uzly) nahradí zadaný text.</span><span class="sxs-lookup"><span data-stu-id="8ce24-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="8ce24-119">Nastaví hodnotu elementu.</span><span class="sxs-lookup"><span data-stu-id="8ce24-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="8ce24-120">Upravit následující metody <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8ce24-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="8ce24-121">Metoda</span><span class="sxs-lookup"><span data-stu-id="8ce24-121">Method</span></span>|<span data-ttu-id="8ce24-122">Popis</span><span class="sxs-lookup"><span data-stu-id="8ce24-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="8ce24-123">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="8ce24-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="8ce24-124">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="8ce24-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="8ce24-125">Upravit následující metody <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="8ce24-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="8ce24-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="8ce24-126">Method</span></span>|<span data-ttu-id="8ce24-127">Popis</span><span class="sxs-lookup"><span data-stu-id="8ce24-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="8ce24-128">Nahradí uzlu nový obsah.</span><span class="sxs-lookup"><span data-stu-id="8ce24-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="8ce24-129">Upravit následující metody <xref:System.Xml.Linq.XContainer> ( <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="8ce24-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="8ce24-130">Metoda</span><span class="sxs-lookup"><span data-stu-id="8ce24-130">Method</span></span>|<span data-ttu-id="8ce24-131">Popis</span><span class="sxs-lookup"><span data-stu-id="8ce24-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="8ce24-132">Podřízené uzly nahradí nový obsah.</span><span class="sxs-lookup"><span data-stu-id="8ce24-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ce24-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ce24-133">See Also</span></span>  
 [<span data-ttu-id="8ce24-134">Úprava XML stromů (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ce24-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
