---
title: Hierarchie modelu DOM (Document Object Model) dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
ms.openlocfilehash: 1193d7631816fe9fbf7aa1984d79ef8e61d5da80
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709969"
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="f06c0-102">Hierarchie modelu DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="f06c0-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="f06c0-103">Následující ilustrace znázorňuje hierarchii tříd pro XML model DOM (Document Object Model) (DOM), s názvem konsorcium World Wide Web (W3C) v závorkách spolu s názvem třídy, kde je relevantní.</span><span class="sxs-lookup"><span data-stu-id="f06c0-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="f06c0-104">![XML model DOM (Document Object Model) &#40;hierarchie&#41; DOM](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="f06c0-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="f06c0-105">Hierarchie XML model DOM (Document Object Model) (DOM)</span><span class="sxs-lookup"><span data-stu-id="f06c0-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="f06c0-106">Následující třídy nedědí z **XmlNode**:</span><span class="sxs-lookup"><span data-stu-id="f06c0-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
- <span data-ttu-id="f06c0-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="f06c0-107">**XmlImplementation**</span></span>  
  
- <span data-ttu-id="f06c0-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="f06c0-108">**XmlNamedNodeMap**</span></span>  
  
- <span data-ttu-id="f06c0-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="f06c0-109">**XmlNodeList**</span></span>  
  
- <span data-ttu-id="f06c0-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="f06c0-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="f06c0-111">Třída **XmlImplementation** se používá k vytvoření dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f06c0-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="f06c0-112">Další informace najdete v tématu [vytváření dokumentů XML](../../../../docs/standard/data/xml/xml-document-creation.md).</span><span class="sxs-lookup"><span data-stu-id="f06c0-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="f06c0-113">Třída **XmlNamedNodeMap** zpracovává neuspořádanou sadu uzlů.</span><span class="sxs-lookup"><span data-stu-id="f06c0-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="f06c0-114">Další informace naleznete v tématu [neuspořádané načtení uzlu podle názvu nebo indexu](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="f06c0-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="f06c0-115">Třída **XmlNodeList** zpracovává uspořádaný seznam uzlů.</span><span class="sxs-lookup"><span data-stu-id="f06c0-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="f06c0-116">Další informace naleznete v tématu [pořadí načítání uzlů podle indexu](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="f06c0-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="f06c0-117">Třída **XmlNodeChangedEventArgs** zpracovává obslužné rutiny událostí registrované v **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="f06c0-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="f06c0-118">Další informace naleznete v tématu [zpracování událostí v dokumentu XML pomocí XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span><span class="sxs-lookup"><span data-stu-id="f06c0-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="f06c0-119">Třída **XmlLinkedNode** dědí z typu **XmlNode**.</span><span class="sxs-lookup"><span data-stu-id="f06c0-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="f06c0-120">Jeho účelem je přepsat dvě metody z **XmlNode**: metody **PreviousSibling** a **NextSibling** .</span><span class="sxs-lookup"><span data-stu-id="f06c0-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="f06c0-121">Tyto přepsané metody jsou potom zděděné a používané v **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**a **XmlProcessingInstruction**, což jsou třídy, které mají předchozí a další na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="f06c0-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f06c0-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f06c0-122">See also</span></span>

- [<span data-ttu-id="f06c0-123">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="f06c0-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
