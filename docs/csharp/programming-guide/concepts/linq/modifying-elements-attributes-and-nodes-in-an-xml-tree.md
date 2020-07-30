---
title: Změna elementů, atributů a uzlů ve stromu XML
description: Další informace o metodách a vlastnostech, které lze použít pro úpravu prvku, jeho podřízených uzlů nebo jeho atributů.
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: bfff882dc57a4f6f4b228563ac923122097d88d0
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303163"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="859ba-103">Změna elementů, atributů a uzlů ve stromu XML</span><span class="sxs-lookup"><span data-stu-id="859ba-103">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="859ba-104">Následující tabulka shrnuje metody a vlastnosti, které lze použít pro úpravu prvku, jeho podřízených prvků nebo jeho atributů.</span><span class="sxs-lookup"><span data-stu-id="859ba-104">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="859ba-105">Následující metody upravují <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="859ba-105">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="859ba-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="859ba-106">Method</span></span>|<span data-ttu-id="859ba-107">Popis</span><span class="sxs-lookup"><span data-stu-id="859ba-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="859ba-108">Nahradí element pomocí analyzovaného kódu XML.</span><span class="sxs-lookup"><span data-stu-id="859ba-108">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="859ba-109">Odebere veškerý obsah (podřízené uzly a atributy) elementu.</span><span class="sxs-lookup"><span data-stu-id="859ba-109">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="859ba-110">Odebere atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="859ba-110">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="859ba-111">Nahradí veškerý obsah (podřízené uzly a atributy) elementu.</span><span class="sxs-lookup"><span data-stu-id="859ba-111">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="859ba-112">Nahradí atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="859ba-112">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="859ba-113">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="859ba-113">Sets the value of an attribute.</span></span> <span data-ttu-id="859ba-114">Vytvoří atribut, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="859ba-114">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="859ba-115">Pokud je hodnota nastavena na `null` , odebere atribut.</span><span class="sxs-lookup"><span data-stu-id="859ba-115">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="859ba-116">Nastaví hodnotu podřízeného prvku.</span><span class="sxs-lookup"><span data-stu-id="859ba-116">Sets the value of a child element.</span></span> <span data-ttu-id="859ba-117">Vytvoří prvek, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="859ba-117">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="859ba-118">Pokud je hodnota nastavena na `null` , odebere prvek.</span><span class="sxs-lookup"><span data-stu-id="859ba-118">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="859ba-119">Nahradí obsah (podřízené uzly) prvku zadaným textem.</span><span class="sxs-lookup"><span data-stu-id="859ba-119">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="859ba-120">Nastaví hodnotu prvku.</span><span class="sxs-lookup"><span data-stu-id="859ba-120">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="859ba-121">Následující metody upravují <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="859ba-121">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="859ba-122">Metoda</span><span class="sxs-lookup"><span data-stu-id="859ba-122">Method</span></span>|<span data-ttu-id="859ba-123">Popis</span><span class="sxs-lookup"><span data-stu-id="859ba-123">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="859ba-124">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="859ba-124">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="859ba-125">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="859ba-125">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="859ba-126">Následující metody upravují <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> ).</span><span class="sxs-lookup"><span data-stu-id="859ba-126">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="859ba-127">Metoda</span><span class="sxs-lookup"><span data-stu-id="859ba-127">Method</span></span>|<span data-ttu-id="859ba-128">Popis</span><span class="sxs-lookup"><span data-stu-id="859ba-128">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="859ba-129">Nahradí uzel novým obsahem.</span><span class="sxs-lookup"><span data-stu-id="859ba-129">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="859ba-130">Následující metody upravují <xref:System.Xml.Linq.XContainer> ( <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> ).</span><span class="sxs-lookup"><span data-stu-id="859ba-130">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="859ba-131">Metoda</span><span class="sxs-lookup"><span data-stu-id="859ba-131">Method</span></span>|<span data-ttu-id="859ba-132">Popis</span><span class="sxs-lookup"><span data-stu-id="859ba-132">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="859ba-133">Nahradí podřízené uzly novým obsahem.</span><span class="sxs-lookup"><span data-stu-id="859ba-133">Replaces the children nodes with new content.</span></span>|  
