---
title: Úprava elementů, atributů a uzlů v XML Tree1
ms.date: 07/20/2015
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
ms.openlocfilehash: 002e87d58ad1a3730889225bf4b3e50448431f2d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360927"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="f67a8-102">Změna elementů, atributů a uzlů ve stromu XML</span><span class="sxs-lookup"><span data-stu-id="f67a8-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="f67a8-103">Následující tabulka shrnuje metody a vlastnosti, které lze použít pro úpravu prvku, jeho podřízených prvků nebo jeho atributů.</span><span class="sxs-lookup"><span data-stu-id="f67a8-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="f67a8-104">Následující metody upravují <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="f67a8-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="f67a8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f67a8-105">Method</span></span>|<span data-ttu-id="f67a8-106">Description</span><span class="sxs-lookup"><span data-stu-id="f67a8-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="f67a8-107">Nahradí element pomocí analyzovaného kódu XML.</span><span class="sxs-lookup"><span data-stu-id="f67a8-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="f67a8-108">Odebere veškerý obsah (podřízené uzly a atributy) elementu.</span><span class="sxs-lookup"><span data-stu-id="f67a8-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="f67a8-109">Odebere atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="f67a8-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="f67a8-110">Nahradí veškerý obsah (podřízené uzly a atributy) elementu.</span><span class="sxs-lookup"><span data-stu-id="f67a8-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="f67a8-111">Nahradí atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="f67a8-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="f67a8-112">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="f67a8-112">Sets the value of an attribute.</span></span> <span data-ttu-id="f67a8-113">Vytvoří atribut, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="f67a8-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="f67a8-114">Pokud je hodnota nastavena na `null` , odebere atribut.</span><span class="sxs-lookup"><span data-stu-id="f67a8-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="f67a8-115">Nastaví hodnotu podřízeného prvku.</span><span class="sxs-lookup"><span data-stu-id="f67a8-115">Sets the value of a child element.</span></span> <span data-ttu-id="f67a8-116">Vytvoří prvek, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="f67a8-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="f67a8-117">Pokud je hodnota nastavena na `null` , odebere prvek.</span><span class="sxs-lookup"><span data-stu-id="f67a8-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="f67a8-118">Nahradí obsah (podřízené uzly) prvku zadaným textem.</span><span class="sxs-lookup"><span data-stu-id="f67a8-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="f67a8-119">Nastaví hodnotu prvku.</span><span class="sxs-lookup"><span data-stu-id="f67a8-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="f67a8-120">Následující metody upravují <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="f67a8-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="f67a8-121">Metoda</span><span class="sxs-lookup"><span data-stu-id="f67a8-121">Method</span></span>|<span data-ttu-id="f67a8-122">Description</span><span class="sxs-lookup"><span data-stu-id="f67a8-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="f67a8-123">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="f67a8-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="f67a8-124">Nastaví hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="f67a8-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="f67a8-125">Následující metody upravují <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> ).</span><span class="sxs-lookup"><span data-stu-id="f67a8-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="f67a8-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="f67a8-126">Method</span></span>|<span data-ttu-id="f67a8-127">Description</span><span class="sxs-lookup"><span data-stu-id="f67a8-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="f67a8-128">Nahradí uzel novým obsahem.</span><span class="sxs-lookup"><span data-stu-id="f67a8-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="f67a8-129">Následující metody upravují <xref:System.Xml.Linq.XContainer> ( <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> ).</span><span class="sxs-lookup"><span data-stu-id="f67a8-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="f67a8-130">Metoda</span><span class="sxs-lookup"><span data-stu-id="f67a8-130">Method</span></span>|<span data-ttu-id="f67a8-131">Description</span><span class="sxs-lookup"><span data-stu-id="f67a8-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="f67a8-132">Nahradí podřízené uzly novým obsahem.</span><span class="sxs-lookup"><span data-stu-id="f67a8-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f67a8-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="f67a8-133">See also</span></span>

- [<span data-ttu-id="f67a8-134">Úprava stromů XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f67a8-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](modifying-xml-trees-linq-to-xml.md)
