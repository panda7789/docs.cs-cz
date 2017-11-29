---
title: "Úprava prvky, atributy a uzly v Tree3 XML"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: da3b31456bc86b547c5174143620f464dc42f35b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="1d172-102">Úprava prvky, atributy a uzly ve stromu XML</span><span class="sxs-lookup"><span data-stu-id="1d172-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="1d172-103">Následující tabulka shrnuje metody a vlastnosti, které můžete použít k úpravě prvek a jeho podřízené elementy nebo jeho atributy.</span><span class="sxs-lookup"><span data-stu-id="1d172-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="1d172-104">Upravit následující metody <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="1d172-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="1d172-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1d172-105">Method</span></span>|<span data-ttu-id="1d172-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1d172-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="1d172-107">Nahradí element Analyzovaná XML.</span><span class="sxs-lookup"><span data-stu-id="1d172-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="1d172-108">Odebere všechny obsah elementu (podřízené uzly a atributy).</span><span class="sxs-lookup"><span data-stu-id="1d172-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="1d172-109">Odebere atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="1d172-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="1d172-110">Nahradí všechny obsah elementu (podřízené uzly a atributy).</span><span class="sxs-lookup"><span data-stu-id="1d172-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="1d172-111">Nahradí atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="1d172-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="1d172-112">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="1d172-112">Sets the value of an attribute.</span></span> <span data-ttu-id="1d172-113">Pokud neexistuje, vytvoří atribut.</span><span class="sxs-lookup"><span data-stu-id="1d172-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="1d172-114">Pokud je hodnota nastavená `null`, odebere atribut.</span><span class="sxs-lookup"><span data-stu-id="1d172-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="1d172-115">Nastaví hodnotu podřízený element.</span><span class="sxs-lookup"><span data-stu-id="1d172-115">Sets the value of a child element.</span></span> <span data-ttu-id="1d172-116">Pokud neexistuje, vytvoří elementu.</span><span class="sxs-lookup"><span data-stu-id="1d172-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="1d172-117">Pokud je hodnota nastavená `null`, odebere element.</span><span class="sxs-lookup"><span data-stu-id="1d172-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="1d172-118">Obsah elementu (podřízené uzly) nahradí zadaný text.</span><span class="sxs-lookup"><span data-stu-id="1d172-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="1d172-119">Nastaví hodnotu elementu.</span><span class="sxs-lookup"><span data-stu-id="1d172-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="1d172-120">Upravit následující metody <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1d172-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="1d172-121">Metoda</span><span class="sxs-lookup"><span data-stu-id="1d172-121">Method</span></span>|<span data-ttu-id="1d172-122">Popis</span><span class="sxs-lookup"><span data-stu-id="1d172-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="1d172-123">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="1d172-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="1d172-124">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="1d172-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="1d172-125">Upravit následující metody <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="1d172-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="1d172-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="1d172-126">Method</span></span>|<span data-ttu-id="1d172-127">Popis</span><span class="sxs-lookup"><span data-stu-id="1d172-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="1d172-128">Nahradí uzlu nový obsah.</span><span class="sxs-lookup"><span data-stu-id="1d172-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="1d172-129">Upravit následující metody <xref:System.Xml.Linq.XContainer> ( <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="1d172-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="1d172-130">Metoda</span><span class="sxs-lookup"><span data-stu-id="1d172-130">Method</span></span>|<span data-ttu-id="1d172-131">Popis</span><span class="sxs-lookup"><span data-stu-id="1d172-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="1d172-132">Podřízené uzly nahradí nový obsah.</span><span class="sxs-lookup"><span data-stu-id="1d172-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d172-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d172-133">See Also</span></span>  
 [<span data-ttu-id="1d172-134">Úprava XML stromů (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1d172-134">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
