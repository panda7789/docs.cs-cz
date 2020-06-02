---
title: Hierarchie modelu DOM (Document Object Model) dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
ms.openlocfilehash: a6099b6c5e30fbf2e4d5d4ed046369bc8f884845
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291432"
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="858e4-102">Hierarchie modelu DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="858e4-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="858e4-103">Následující ilustrace znázorňuje hierarchii tříd pro XML model DOM (Document Object Model) (DOM), s názvem konsorcium World Wide Web (W3C) v závorkách spolu s názvem třídy, kde je relevantní.</span><span class="sxs-lookup"><span data-stu-id="858e4-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="858e4-104">![Hierarchie&#41; &#40;DOM model DOM (Document Object Model) XML](media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="858e4-104">![XML Document Object Model &#40;DOM&#41; hierarchy](media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="858e4-105">Hierarchie XML model DOM (Document Object Model) (DOM)</span><span class="sxs-lookup"><span data-stu-id="858e4-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="858e4-106">Následující třídy nedědí z **XmlNode**:</span><span class="sxs-lookup"><span data-stu-id="858e4-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
- <span data-ttu-id="858e4-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="858e4-107">**XmlImplementation**</span></span>  
  
- <span data-ttu-id="858e4-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="858e4-108">**XmlNamedNodeMap**</span></span>  
  
- <span data-ttu-id="858e4-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="858e4-109">**XmlNodeList**</span></span>  
  
- <span data-ttu-id="858e4-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="858e4-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="858e4-111">Třída **XmlImplementation** se používá k vytvoření dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="858e4-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="858e4-112">Další informace najdete v tématu [vytváření dokumentů XML](xml-document-creation.md).</span><span class="sxs-lookup"><span data-stu-id="858e4-112">For more information, see [XML Document Creation](xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="858e4-113">Třída **XmlNamedNodeMap** zpracovává neuspořádanou sadu uzlů.</span><span class="sxs-lookup"><span data-stu-id="858e4-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="858e4-114">Další informace naleznete v tématu [neuspořádané načtení uzlu podle názvu nebo indexu](unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="858e4-114">For more information, see [Unordered Node Retrieval by Name or Index](unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="858e4-115">Třída **XmlNodeList** zpracovává uspořádaný seznam uzlů.</span><span class="sxs-lookup"><span data-stu-id="858e4-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="858e4-116">Další informace naleznete v tématu [pořadí načítání uzlů podle indexu](ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="858e4-116">For more information, see [Ordered Node Retrieval by Index](ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="858e4-117">Třída **XmlNodeChangedEventArgs** zpracovává obslužné rutiny událostí registrované v **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="858e4-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="858e4-118">Další informace naleznete v tématu [zpracování událostí v dokumentu XML pomocí XmlNodeChangedEventArgs](event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span><span class="sxs-lookup"><span data-stu-id="858e4-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="858e4-119">Třída **XmlLinkedNode** dědí z typu **XmlNode**.</span><span class="sxs-lookup"><span data-stu-id="858e4-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="858e4-120">Jeho účelem je přepsat dvě metody z **XmlNode**: metody **PreviousSibling** a **NextSibling** .</span><span class="sxs-lookup"><span data-stu-id="858e4-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="858e4-121">Tyto přepsané metody jsou potom zděděné a používané v **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**a **XmlProcessingInstruction**, což jsou třídy, které mají předchozí a další na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="858e4-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="858e4-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="858e4-122">See also</span></span>

- [<span data-ttu-id="858e4-123">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="858e4-123">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
