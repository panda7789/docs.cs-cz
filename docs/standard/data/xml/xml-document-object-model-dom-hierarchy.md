---
title: Hierarchie modelu (DOM) objekt dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5b4ca249928200ddfc9dcd133ac673261046fb2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570169"
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="da7f5-102">Hierarchie modelu (DOM) objekt dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="da7f5-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="da7f5-103">Následující obrázek znázorňuje hierarchie tříd pro XML modelu DOM (Document Object), s World Wide Web Consortium (W3C) název do závorek společně s název třídy, kde je relevantní.</span><span class="sxs-lookup"><span data-stu-id="da7f5-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="da7f5-104">![XML Document Object Model &#40;DOM&#41; hierarchie](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="da7f5-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="da7f5-105">Hierarchii XML modelu DOM (Document Object)</span><span class="sxs-lookup"><span data-stu-id="da7f5-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="da7f5-106">Následující třídy nedědí z **XmlNode**:</span><span class="sxs-lookup"><span data-stu-id="da7f5-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
-   <span data-ttu-id="da7f5-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="da7f5-107">**XmlImplementation**</span></span>  
  
-   <span data-ttu-id="da7f5-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="da7f5-108">**XmlNamedNodeMap**</span></span>  
  
-   <span data-ttu-id="da7f5-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="da7f5-109">**XmlNodeList**</span></span>  
  
-   <span data-ttu-id="da7f5-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="da7f5-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="da7f5-111">**XmlImplementation** třída se používá k vytvoření dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="da7f5-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="da7f5-112">Další informace najdete v tématu [vytvoření dokumentu XML](../../../../docs/standard/data/xml/xml-document-creation.md).</span><span class="sxs-lookup"><span data-stu-id="da7f5-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="da7f5-113">**XmlNamedNodeMap** třída zpracovává neuspořádaný sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="da7f5-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="da7f5-114">Další informace najdete v tématu [Neseřazený uzlu načítání podle názvu nebo Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="da7f5-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="da7f5-115">**XmlNodeList** třída zpracovává seřazený seznam uzlů.</span><span class="sxs-lookup"><span data-stu-id="da7f5-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="da7f5-116">Další informace najdete v tématu [načtení uzlu seřazené podle indexu](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="da7f5-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="da7f5-117">**XmlNodeChangedEventArgs** třída zpracovává obslužné rutiny událostí zaregistrované na **třídou XMLDocument nastavenou na**.</span><span class="sxs-lookup"><span data-stu-id="da7f5-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="da7f5-118">Další informace najdete v tématu [zpracování událostí v dokumentu XML pomocí XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span><span class="sxs-lookup"><span data-stu-id="da7f5-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="da7f5-119">**XmlLinkedNode** třída dědí z **XmlNode**.</span><span class="sxs-lookup"><span data-stu-id="da7f5-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="da7f5-120">Jejím účelem je přepsat dvě metody z **XmlNode**: **PreviousSibling** a **NextSibling** metody.</span><span class="sxs-lookup"><span data-stu-id="da7f5-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="da7f5-121">Tyto metody přepsaného pak zděděná a používá **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, a **XmlProcessingInstruction**, které jsou třídy, které nemají stejné úrovně předchozí a další.</span><span class="sxs-lookup"><span data-stu-id="da7f5-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da7f5-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="da7f5-122">See Also</span></span>  
 [<span data-ttu-id="da7f5-123">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="da7f5-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
