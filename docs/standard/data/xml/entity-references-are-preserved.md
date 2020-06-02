---
title: Odkazy na entity jsou zachované
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
ms.openlocfilehash: e4c902df1b0cd2bd9e97b49c0ec1d10df91ef1c7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290341"
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="1ff06-102">Odkazy na entity jsou zachované</span><span class="sxs-lookup"><span data-stu-id="1ff06-102">Entity References are Preserved</span></span>
<span data-ttu-id="1ff06-103">Pokud odkaz na entitu není rozbalený, ale zachová, model DOM (Document Object Model) XML (DOM) vytvoří uzel **XmlEntityReference** , když dojde k odkazování na entitu.</span><span class="sxs-lookup"><span data-stu-id="1ff06-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="1ff06-104">Pomocí následujícího kódu XML</span><span class="sxs-lookup"><span data-stu-id="1ff06-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="1ff06-105">model DOM vytvoří uzel **XmlEntityReference** , když nalezne `&publisher;` odkaz.</span><span class="sxs-lookup"><span data-stu-id="1ff06-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="1ff06-106">**XmlEntityReference** obsahuje podřízené uzly zkopírované z obsahu v deklaraci entity.</span><span class="sxs-lookup"><span data-stu-id="1ff06-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="1ff06-107">Předchozí příklad kódu obsahuje text v deklaraci entity, takže se vytvoří uzel **XmlText** jako podřízený uzel uzlu odkazu na entitu.</span><span class="sxs-lookup"><span data-stu-id="1ff06-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="1ff06-108">![Stromová struktura pro zachované odkazy na entity](media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="1ff06-108">![Tree structure for preserved entity references](media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="1ff06-109">Stromová struktura pro Nezachované odkazy entit</span><span class="sxs-lookup"><span data-stu-id="1ff06-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="1ff06-110">Podřízené uzly **XmlEntityReference** jsou kopie všech podřízených uzlů vytvořených z uzlu **XmlEntity** při zjištění deklarace entity.</span><span class="sxs-lookup"><span data-stu-id="1ff06-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ff06-111">Uzly zkopírované z **XmlEntity** nejsou vždy přesně zkopírovány po umístění do uzlu odkaz na entitu.</span><span class="sxs-lookup"><span data-stu-id="1ff06-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="1ff06-112">V uzlu odkazu na entitu můžou být obory názvů, které mají vliv na konečnou konfiguraci podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="1ff06-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="1ff06-113">Ve výchozím nastavení jsou obecné entity jako `&abc;` zachované a **XmlEntityReference** uzly se vždycky vytvářejí.</span><span class="sxs-lookup"><span data-stu-id="1ff06-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ff06-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ff06-114">See also</span></span>

- [<span data-ttu-id="1ff06-115">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="1ff06-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
