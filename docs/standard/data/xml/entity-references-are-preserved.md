---
title: Odkazy na entity jsou zachované
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e512f2077c2e6b9feba5024c4eabc2568357ecab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965917"
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="6104e-102">Odkazy na entity jsou zachované</span><span class="sxs-lookup"><span data-stu-id="6104e-102">Entity References are Preserved</span></span>
<span data-ttu-id="6104e-103">Pokud odkaz na entitu není rozbalený, ale zachová, model DOM (Document Object Model) XML (DOM) vytvoří uzel **XmlEntityReference** , když dojde k odkazování na entitu.</span><span class="sxs-lookup"><span data-stu-id="6104e-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="6104e-104">Pomocí následujícího kódu XML</span><span class="sxs-lookup"><span data-stu-id="6104e-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="6104e-105">model DOM vytvoří uzel **XmlEntityReference** , když nalezne `&publisher;` odkaz.</span><span class="sxs-lookup"><span data-stu-id="6104e-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="6104e-106">**XmlEntityReference** obsahuje podřízené uzly zkopírované z obsahu v deklaraci entity.</span><span class="sxs-lookup"><span data-stu-id="6104e-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="6104e-107">Předchozí příklad kódu obsahuje text v deklaraci entity, takže se vytvoří uzel **XmlText** jako podřízený uzel uzlu odkazu na entitu.</span><span class="sxs-lookup"><span data-stu-id="6104e-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="6104e-108">![Stromová struktura pro zachované odkazy na entity](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="6104e-108">![Tree structure for preserved entity references](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="6104e-109">Stromová struktura pro Nezachované odkazy entit</span><span class="sxs-lookup"><span data-stu-id="6104e-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="6104e-110">Podřízené uzly **XmlEntityReference** jsou kopie všech podřízených uzlů vytvořených z uzlu **XmlEntity** při zjištění deklarace entity.</span><span class="sxs-lookup"><span data-stu-id="6104e-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6104e-111">Uzly zkopírované z **XmlEntity** nejsou vždy přesně zkopírovány po umístění do uzlu odkaz na entitu.</span><span class="sxs-lookup"><span data-stu-id="6104e-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="6104e-112">V uzlu odkazu na entitu můžou být obory názvů, které mají vliv na konečnou konfiguraci podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="6104e-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="6104e-113">Ve výchozím nastavení jsou obecné entity `&abc;` jako zachované a **XmlEntityReference** uzly se vždycky vytvářejí.</span><span class="sxs-lookup"><span data-stu-id="6104e-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6104e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6104e-114">See also</span></span>

- [<span data-ttu-id="6104e-115">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="6104e-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
