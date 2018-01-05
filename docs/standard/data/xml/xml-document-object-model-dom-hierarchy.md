---
title: Hierarchie modelu (DOM) objekt dokumentu XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4d2ffaa994ce3c9b02ed0937967845be1b803f6d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="c006e-102">Hierarchie modelu (DOM) objekt dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="c006e-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="c006e-103">Následující obrázek znázorňuje hierarchie tříd pro XML modelu DOM (Document Object), s World Wide Web Consortium (W3C) název do závorek společně s název třídy, kde je relevantní.</span><span class="sxs-lookup"><span data-stu-id="c006e-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="c006e-104">![XML Document Object Model &#40; DOM &#41; hierarchie](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="c006e-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="c006e-105">Hierarchii XML modelu DOM (Document Object)</span><span class="sxs-lookup"><span data-stu-id="c006e-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="c006e-106">Následující třídy nedědí z **XmlNode**:</span><span class="sxs-lookup"><span data-stu-id="c006e-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
-   <span data-ttu-id="c006e-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="c006e-107">**XmlImplementation**</span></span>  
  
-   <span data-ttu-id="c006e-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="c006e-108">**XmlNamedNodeMap**</span></span>  
  
-   <span data-ttu-id="c006e-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="c006e-109">**XmlNodeList**</span></span>  
  
-   <span data-ttu-id="c006e-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="c006e-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="c006e-111">**XmlImplementation** třída se používá k vytvoření dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c006e-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="c006e-112">Další informace najdete v tématu [vytvoření dokumentu XML](../../../../docs/standard/data/xml/xml-document-creation.md).</span><span class="sxs-lookup"><span data-stu-id="c006e-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="c006e-113">**XmlNamedNodeMap** třída zpracovává neuspořádaný sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="c006e-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="c006e-114">Další informace najdete v tématu [Neseřazený uzlu načítání podle názvu nebo Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="c006e-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="c006e-115">**XmlNodeList** třída zpracovává seřazený seznam uzlů.</span><span class="sxs-lookup"><span data-stu-id="c006e-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="c006e-116">Další informace najdete v tématu [načtení uzlu seřazené podle indexu](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="c006e-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="c006e-117">**XmlNodeChangedEventArgs** třída zpracovává obslužné rutiny událostí zaregistrované na **třídou XMLDocument nastavenou na**.</span><span class="sxs-lookup"><span data-stu-id="c006e-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="c006e-118">Další informace najdete v tématu [zpracování událostí v dokumentu XML pomocí XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span><span class="sxs-lookup"><span data-stu-id="c006e-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="c006e-119">**XmlLinkedNode** třída dědí z **XmlNode**.</span><span class="sxs-lookup"><span data-stu-id="c006e-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="c006e-120">Jejím účelem je přepsat dvě metody z **XmlNode**: **PreviousSibling** a **NextSibling** metody.</span><span class="sxs-lookup"><span data-stu-id="c006e-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="c006e-121">Tyto metody přepsaného pak zděděná a používá **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, a **XmlProcessingInstruction**, které jsou třídy, které nemají stejné úrovně předchozí a další.</span><span class="sxs-lookup"><span data-stu-id="c006e-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c006e-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="c006e-122">See Also</span></span>  
 [<span data-ttu-id="c006e-123">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="c006e-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
