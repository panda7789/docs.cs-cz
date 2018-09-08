---
title: Hierarchie Model (DOM) objekt dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef2b5b200f95cdfac9b08a33c328c1dfb797e59e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44179161"
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="0a4e8-102">Hierarchie Model (DOM) objekt dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="0a4e8-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="0a4e8-103">Následující obrázek znázorňuje hierarchii tříd pro XML Document Object Model (DOM), s World Wide Web Consortium (W3C) název v závorka spolu s názvem třídy, kde je to relevantní.</span><span class="sxs-lookup"><span data-stu-id="0a4e8-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="0a4e8-104">![Modelu objektu dokumentu XML &#40;modelu DOM&#41; hierarchie](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="0a4e8-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="0a4e8-105">Hierarchie XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="0a4e8-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="0a4e8-106">Následující třídy nedědí z **XmlNode**:</span><span class="sxs-lookup"><span data-stu-id="0a4e8-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
-   <span data-ttu-id="0a4e8-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="0a4e8-107">**XmlImplementation**</span></span>  
  
-   <span data-ttu-id="0a4e8-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="0a4e8-108">**XmlNamedNodeMap**</span></span>  
  
-   <span data-ttu-id="0a4e8-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="0a4e8-109">**XmlNodeList**</span></span>  
  
-   <span data-ttu-id="0a4e8-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="0a4e8-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="0a4e8-111">**XmlImplementation** třída se používá k vytvoření dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0a4e8-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="0a4e8-112">Další informace najdete v tématu [vytváření dokumentů XML](../../../../docs/standard/data/xml/xml-document-creation.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e8-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="0a4e8-113">**XmlNamedNodeMap** třída zpracovává neuspořádanou sadu uzlů.</span><span class="sxs-lookup"><span data-stu-id="0a4e8-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="0a4e8-114">Další informace najdete v tématu [Neseřazený načtení uzlů podle názvu nebo indexu](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e8-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="0a4e8-115">**XmlNodeList** třída zpracovává uspořádaný seznam uzlů.</span><span class="sxs-lookup"><span data-stu-id="0a4e8-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="0a4e8-116">Další informace najdete v tématu [seřazené načtení uzlů podle indexu](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e8-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="0a4e8-117">**XmlNodeChangedEventArgs** třída zpracovává obslužné rutiny událostí zaregistrované na **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="0a4e8-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="0a4e8-118">Další informace najdete v tématu [zpracování událostí v dokumentu XML pomocí XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e8-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="0a4e8-119">**XmlLinkedNode** třída dědí z **XmlNode**.</span><span class="sxs-lookup"><span data-stu-id="0a4e8-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="0a4e8-120">Jeho účelem je přepsat dvě metody ze **XmlNode**: **PreviousSibling** a **NextSibling** metody.</span><span class="sxs-lookup"><span data-stu-id="0a4e8-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="0a4e8-121">Tyto přepsané metody jsou pak zděděné a používá **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, a **XmlProcessingInstruction**, které jsou třídy, které mají další a předchozí položky na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="0a4e8-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a4e8-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a4e8-122">See also</span></span>

- [<span data-ttu-id="0a4e8-123">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="0a4e8-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
