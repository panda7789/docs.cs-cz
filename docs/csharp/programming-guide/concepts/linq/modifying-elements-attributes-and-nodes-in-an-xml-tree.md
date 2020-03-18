---
title: Úprava prvků, atributů a uzlů ve stromu XML3
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: 93a4d67129e22d0bbeef464c1d4d8758439edb7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484229"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="d61ac-102">Změna elementů, atributů a uzlů ve stromu XML</span><span class="sxs-lookup"><span data-stu-id="d61ac-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="d61ac-103">Následující tabulka shrnuje metody a vlastnosti, které můžete použít k úpravě prvku, jeho podřízených prvků nebo jeho atributů.</span><span class="sxs-lookup"><span data-stu-id="d61ac-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="d61ac-104">Následující metody upravují . <xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="d61ac-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="d61ac-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d61ac-105">Method</span></span>|<span data-ttu-id="d61ac-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d61ac-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="d61ac-107">Nahradí prvek analyzovaným XML.</span><span class="sxs-lookup"><span data-stu-id="d61ac-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="d61ac-108">Odebere veškerý obsah (podřízené uzly a atributy) prvku.</span><span class="sxs-lookup"><span data-stu-id="d61ac-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="d61ac-109">Odebere atributy prvku.</span><span class="sxs-lookup"><span data-stu-id="d61ac-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="d61ac-110">Nahradí veškerý obsah (podřízené uzly a atributy) prvku.</span><span class="sxs-lookup"><span data-stu-id="d61ac-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="d61ac-111">Nahradí atributy prvku.</span><span class="sxs-lookup"><span data-stu-id="d61ac-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="d61ac-112">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="d61ac-112">Sets the value of an attribute.</span></span> <span data-ttu-id="d61ac-113">Vytvoří atribut, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="d61ac-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="d61ac-114">Pokud je hodnota `null`nastavena na , odebere atribut.</span><span class="sxs-lookup"><span data-stu-id="d61ac-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="d61ac-115">Nastaví hodnotu podřízeného prvku.</span><span class="sxs-lookup"><span data-stu-id="d61ac-115">Sets the value of a child element.</span></span> <span data-ttu-id="d61ac-116">Vytvoří prvek, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="d61ac-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="d61ac-117">Pokud je hodnota `null`nastavena na , odebere prvek.</span><span class="sxs-lookup"><span data-stu-id="d61ac-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="d61ac-118">Nahradí obsah (podřízené uzly) prvku zadaným textem.</span><span class="sxs-lookup"><span data-stu-id="d61ac-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="d61ac-119">Nastaví hodnotu prvku.</span><span class="sxs-lookup"><span data-stu-id="d61ac-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="d61ac-120">Následující metody upravují . <xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="d61ac-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="d61ac-121">Metoda</span><span class="sxs-lookup"><span data-stu-id="d61ac-121">Method</span></span>|<span data-ttu-id="d61ac-122">Popis</span><span class="sxs-lookup"><span data-stu-id="d61ac-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="d61ac-123">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="d61ac-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="d61ac-124">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="d61ac-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="d61ac-125">Následující metody upravují <xref:System.Xml.Linq.XNode> <xref:System.Xml.Linq.XElement> (včetně nebo). <xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="d61ac-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="d61ac-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="d61ac-126">Method</span></span>|<span data-ttu-id="d61ac-127">Popis</span><span class="sxs-lookup"><span data-stu-id="d61ac-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="d61ac-128">Nahradí uzel novým obsahem.</span><span class="sxs-lookup"><span data-stu-id="d61ac-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="d61ac-129">Následující metody <xref:System.Xml.Linq.XContainer> upravují <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument>(nebo).</span><span class="sxs-lookup"><span data-stu-id="d61ac-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="d61ac-130">Metoda</span><span class="sxs-lookup"><span data-stu-id="d61ac-130">Method</span></span>|<span data-ttu-id="d61ac-131">Popis</span><span class="sxs-lookup"><span data-stu-id="d61ac-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="d61ac-132">Nahradí podřízené uzly novým obsahem.</span><span class="sxs-lookup"><span data-stu-id="d61ac-132">Replaces the children nodes with new content.</span></span>|  
